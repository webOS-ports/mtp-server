add_definitions(-DMTP_DEVICE -DMTP_HOST)

add_executable(
    mtp-server
    server.cpp
)

set_target_properties(mtp-server PROPERTIES COMPILE_FLAGS -fPIC)

target_link_libraries(
    mtp-server
    mtpserver
    usbhost
    android-properties
    ${Boost_LIBRARIES}
    ${Boost_thread_LIBRARIES}
    ${Boost_system_LIBRARIES}
    ${Boost_filesystem_LIBRARIES}
    glog::glog
)

install(
  TARGETS mtp-server
  RUNTIME DESTINATION bin
)

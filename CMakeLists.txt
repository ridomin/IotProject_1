cmake_minimum_required(VERSION 2.8.11)

# The demonstration uses C99 but it could just as easily be a C++ application
set(CMAKE_C_FLAGS "--std=c99 ${CMAKE_C_FLAGS}")

set(binary_name "IoTproject_1" CACHE STRING "" FORCE)

set(iothub_c_files
        main.c
)

# Set up the include and library paths
include_directories(.)
include_directories(${PROJECT_SOURCE_DIR}/deps/parson)
include_directories(${SHARED_UTIL_INC_FOLDER})
include_directories(${IOTHUB_CLIENT_INC_FOLDER})

add_executable(${binary_name} ${iothub_c_files})

# List the libraries required by the link step
target_link_libraries(${binary_name}
iothub_client_mqtt_transport
iothub_client
umqtt
)
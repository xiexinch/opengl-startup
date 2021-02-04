cmake_minimum_required(VERSION 3.17)
project(gltest)

set(CMAKE_CXX_STANDARD 14)

# 添加头文件
set(GLEW_H /usr/local/Cellar/glew/2.2.0_1/include/GL)
set(GLFW_H /usr/local/Cellar/glfw/3.3.2/include/GLFW)
set(GLAD_H /usr/local/include/)
set(GLAD_H /usr/local/include/glad)
set(KH_H /usr/local/include/KHR)
include_directories(${GLEW_H} ${GLFW_H} ${GLAD_H} ${KH_H})

# 添加目标链接
set(GLEW_LINK /usr/local/Cellar/glew/2.2.0_1/lib/libGLEW.2.2.dylib)
set(GLFW_LINK /usr/local/Cellar/glfw/3.3.2/lib/libglfw.3.dylib)
link_libraries(${OPENGL} ${GLEW_LINK} ${GLFW_LINK})

# 执行编译命令
set(SOURCE_FILES main.cpp)
add_executable(gltest ${SOURCE_FILES})

# mac下这步很重要
if (APPLE)
    target_link_libraries(gltest "-framework OpenGL")
    target_link_libraries(gltest "-framework GLUT")
endif()
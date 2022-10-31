# CMakeList.txt: Opengl 的 CMake 项目，在此处包括源代码并定义
# 项目特定的逻辑。
#
cmake_minimum_required (VERSION 3.8)

# 将源代码添加到此项目的可执行文件。

message("current source directory ${CMAKE_CURRENT_SOURCE_DIR}")

message("current binary directory ${CMAKE_CURRENT_BINARY_DIR}")


add_subdirectory(glfw)

add_executable (Opengl "Opengl.cpp" "Opengl.h")

#add_custom_command(
#	TARGET ${PROJECT_NAME} PRE_BUILD
#	COMMAND
#		${CMAKE_COMMAND} -E rm -rf ${CMAKE_CURRENT_BINARY_DIR}/resources
#	COMMAND
#	    ${CMAKE_COMMAND} -E copy_directory ${CMAKE_SOURCE_DIR}/${PROJECT_NAME}/resources ${CMAKE_BINARY_DIR}/${PROJECT_NAME}/resources
#)


add_custom_target(
	COPY_RESOURCES ALL
	COMMAND
		${CMAKE_COMMAND} -E rm -rf ${CMAKE_CURRENT_BINARY_DIR}/resources
	COMMAND
	    ${CMAKE_COMMAND} -E copy_directory ${CMAKE_SOURCE_DIR}/${PROJECT_NAME}/resources ${CMAKE_BINARY_DIR}/${PROJECT_NAME}/resources
	DEPENDS
		${CMAKE_SOURCE_DIR}/${PROJECT_NAME}/resources
	WORKING_DIRECTORY
		${CMAKE_BINARY_DIR}
	COMMENT
		"copy resources"
)

add_executable (coordinate "coordinate/main.cpp" "glad/glad.c")
target_link_libraries(coordinate PRIVATE glfw)
target_include_directories(coordinate PRIVATE include)

add_executable (texture "texture/main.cpp" "glad/glad.c")
target_link_libraries(texture PRIVATE glfw)
target_include_directories(texture PRIVATE include)

add_executable (transform "transform/main.cpp" "glad/glad.c")
target_link_libraries(transform PRIVATE glfw)
target_include_directories(transform PRIVATE include)

add_executable (color "color/main.cpp" "glad/glad.c")
target_link_libraries(color PRIVATE glfw)
target_include_directories(color PRIVATE include)

add_executable (camera "camera/main.cpp" "glad/glad.c")
target_link_libraries(camera PRIVATE glfw)
target_include_directories(camera PRIVATE include)

add_executable (light1 "light/light1.cpp" "glad/glad.c")
target_link_libraries(light1 PRIVATE glfw)
target_include_directories(light1 PRIVATE include)

add_executable (light2 "light/light2.cpp" "glad/glad.c")
target_link_libraries(light2 PRIVATE glfw)
target_include_directories(light2 PRIVATE include)

add_executable (material "material/main.cpp" "glad/glad.c")
target_link_libraries(material PRIVATE glfw)
target_include_directories(material PRIVATE include)

add_executable (lightmap "lightmap/main.cpp" "glad/glad.c")
target_link_libraries(lightmap PRIVATE glfw)
target_include_directories(lightmap PRIVATE include)


# TODO: 如有需要，请添加测试并安装目标。

#1.cmake verson��ָ��cmake����С�汾�� 
cmake_minimum_required(VERSION 2.8)

#2.project name��ָ����Ŀ�����ƣ�һ�����Ŀ���ļ������ƶ�Ӧ
project(mobilefacenet_ncnn C CXX)

#3.set environment variable�����û�������
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

#4.includeͷ�ļ�Ŀ¼ 
include_directories(${CMAKE_CURRENT_LIST_DIR}/3rdparty/opencv/include
          ${CMAKE_CURRENT_LIST_DIR}/3rdparty/opencv/include/opencv
          ${CMAKE_CURRENT_LIST_DIR}/3rdparty/opencv/include/opencv2
          ${CMAKE_CURRENT_LIST_DIR}/3rdparty/ncnn/include
                    ${CMAKE_CURRENT_LIST_DIR}/src)

#5.libraryĿ¼��name����
link_directories(${CMAKE_CURRENT_LIST_DIR}/3rdparty/ncnn/lib
		${CMAKE_CURRENT_LIST_DIR}/3rdparty/opencv/lib)

list(APPEND MBF_LINKER_LIBS opencv_core2413 opencv_highgui2413 opencv_imgproc2413 ncnn)

#6.source directoryԴ�ļ�Ŀ¼
file(GLOB MBF_SRC ${CMAKE_CURRENT_LIST_DIR}/src/*.h
                    ${CMAKE_CURRENT_LIST_DIR}/src/*.cpp)
set(MBF_COMPILE_CODE ${MBF_SRC})

#7.1.add executable file������Ϊ��ִ���ļ�
add_executable(mobilefacenet_ncnn ${MBF_COMPILE_CODE})
#7.2.add library file������Ϊ��̬��
# add_library(mobilefacenet_ncnn SHARED ${MBF_COMPILE_CODE})

#8.add link library�����ӹ����������Ŀ�
target_link_libraries(mobilefacenet_ncnn ${MBF_LINKER_LIBS})
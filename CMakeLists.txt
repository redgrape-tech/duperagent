#logicmodule/CMakeLists.txt
project(duperagent VERSION 0.1 LANGUAGES CXX)

qt_add_library(${PROJECT_NAME} SHARED
    qmldir
    )


set(HEADERS duperagent.h qpm.h request.h response.h serialization.h 
	    jsvalueiterator.h config.h cookiejar.h promise.h 
	    promisemodule.h networkactivityindicator.h imageutils.h 
	    multipartsource.h ssl.h
)

set(SOURCES duperagent.cpp request.cpp response.cpp serialization.cpp
	    config.cpp cookiejar.cpp promise.cpp promisemodule.cpp 
	    networkactivityindicator.cpp imageutils.cpp multipartsource.cpp
	    ssl.cpp)

qt6_add_qml_module(${PROJECT_NAME}
    URI duperagent
    VERSION 1.0
    NO_PLUGIN
    RESOURCE_PREFIX "/qt/qml/"
    SOURCES ${HEADERS} ${SOURCES}
)

target_link_libraries(${PROJECT_NAME} PUBLIC
    Qt6::Core
    Qt6::Gui
    Qt6::Qml
    Qt6::Quick
)

target_include_directories(${PROJECT_NAME}
    PUBLIC
)


cmake_minimum_required(VERSION 2.8)

project(openFrameworks)
set(BIN openFrameworks)

set(CMAKE_CXX_FLAGS "-O3 -std=c++11")

if(${CMAKE_SYSTEM_NAME} STREQUAL "Linux")
    set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/Compiled/linux-64)

    set(DEFINITIONS
        -DOF_USING_GTK
    )
    
    set(INCLUDE_DIRS
        "/usr/include/atk-1.0"
        "/usr/include/cairo"
        "/usr/include/freetype2"
        "/usr/include/GL"
        "/usr/include/gdk-pixbuf-2.0"
        "/usr/include/glib-2.0"
        "/usr/include/gtk-2.0"
        "/usr/include/harfbuzz"
        "/usr/include/libdrm"
        "/usr/include/libpng16"
        "/usr/include/pango-1.0"
        "/usr/include/pixman-1"
        
        "/usr/lib/glib-2.0/include"
        "/usr/lib/gtk-2.0/include"
    )
endif()

if(WIN32)
    set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/Compiled/mingw-64)
    
    set(DEFINITIONS
        -D__MINGW32_VERSION
    )
    
    set(INCLUDE_DIRS
        "/usr/x86_64-w64-mingw32/include"
        "/usr/x86_64-w64-mingw32/include/GL"
        "/usr/x86_64-w64-mingw32/include/cairo"
        "/usr/x86_64-w64-mingw32/include/freetype2"
    )
endif()

set(DEFINITIONS ${DEFINITIONS}
    -DTARGET_NO_SOUND
    -DFREEIMAGE_LIB
    -DPOCO_STATIC
    -DPOCO_NO_AUTOMATIC_LIB_INIT
)

set(INCLUDE_DIRS ${INCLUDE_DIRS}
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/3d"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/app"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/communication"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/events"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/gl"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/graphics"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/math"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/types"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/utils"
    
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/glfw"
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/glfw/include"
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/glfw/include/GLFW"
    
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/kiss"
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/kiss/include"
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/kiss/src"
    
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/poco"
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/poco/Crypto/include"
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/poco/Crypto/include/Poco"
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/poco/Crypto/include/Poco/Crypto"

    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/poco/Foundation/include"
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/poco/Foundation/include/Poco"
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/poco/Foundation/include/Poco/Dynamic"

    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/poco/Net/include"
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/poco/Net/include/Poco"
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/poco/Net/include/Poco/Net"

    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/poco/NetSSL_OpenSSL/include"
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/poco/NetSSL_OpenSSL/include/Poco"
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/poco/NetSSL_OpenSSL/include/Poco/Net"

    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/poco/Util/include"
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/poco/Util/include/Poco"
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/poco/Util/include/Poco/Util"
    
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/poco/XML/include"
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/poco/XML/include/Poco"
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/poco/XML/include/Poco/DOM"
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/poco/XML/include/Poco/SAX"
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/poco/XML/include/Poco/XML"
    
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/poco/Zip/include"
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/poco/Zip/include/Poco"
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/poco/Zip/include/Poco/Zip"
    
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/tess2"
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/tess2/include"
    "${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/Libs/tess2/Sources"
)

set(SOURCES
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/3d/of3dPrimitives.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/3d/ofMesh.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/3d/ofNode.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/3d/ofCamera.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/3d/of3dUtils.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/3d/ofEasyCam.cpp"
    
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/app/ofAppRunner.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/app/ofAppGlutWindow.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/app/ofAppNoWindow.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/app/ofAppGLFWWindow.cpp"
    
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/communication/ofSerial.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/communication/ofArduino.cpp"
    
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/events/ofEvents.cpp"
    
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/gl/ofGLProgrammableRenderer.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/gl/ofFbo.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/gl/ofMaterial.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/gl/ofVboMesh.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/gl/ofGLUtils.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/gl/ofShader.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/gl/ofTexture.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/gl/ofGLRenderer.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/gl/ofLight.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/gl/ofVbo.cpp"
    
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/graphics/ofTessellator.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/graphics/ofCairoRenderer.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/graphics/ofImage.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/graphics/ofRendererCollection.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/graphics/ofPixels.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/graphics/of3dGraphics.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/graphics/ofGraphics.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/graphics/ofTrueTypeFont.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/graphics/ofPath.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/graphics/ofBitmapFont.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/graphics/ofPolyline.cpp"
    
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/math/ofQuaternion.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/math/ofVec2f.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/math/ofMatrix4x4.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/math/ofVec4f.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/math/ofMath.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/math/ofMatrix3x3.cpp"
    
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/types/ofBaseTypes.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/types/ofRectangle.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/types/ofParameterGroup.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/types/ofColor.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/types/ofParameter.cpp"
    
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/utils/ofURLFileLoader.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/utils/ofUtils.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/utils/ofLog.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/utils/ofSystemUtils.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/utils/ofFileUtils.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/utils/ofXml.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/utils/ofMatrixStack.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/openFrameworks/utils/ofThread.cpp"
)

add_definitions(${DEFINITIONS})
include_directories(${INCLUDE_DIRS})
add_library(${BIN} STATIC ${SOURCES})

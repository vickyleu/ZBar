cmake_minimum_required(VERSION 3.4.1)

############<<<<<<<<<<<<<Iconv>>>>>>>>>>>>>>>>##########
#######################################################
#######################################################
add_library(iconv STATIC
                           src/main/cpp/iconv/lib/iconv.c
                           	src/main/cpp/iconv/libcharset/lib/localcharset.c
                           	src/main/cpp/iconv/lib/relocatable.c)
set(CMAKE_CXX_FLAGS "-Wno-multichar -D_ANDROID -DLIBDIR="c" -DBUILDING_LIBICONV -DBUILDING_LIBCHARSET -DIN_LIBRARY ${CMAKE_CXX_FLAGS}")
message(STATUS "设置CFlags")
target_include_directories(iconv PUBLIC
                            src/main/cpp/iconv/include
                            src/main/cpp/iconv/srclib
                            src/main/cpp/iconv/libcharset
  	                        src/main/cpp/iconv/libcharset/include)
#######################################################
#######################################################
############<<<<<<<<<<<<<Iconv>>>>>>>>>>>>>>>>##########

############<<<<<<<<<<<<<Zbar>>>>>>>>>>>>>>>>##########
#######################################################
#######################################################
add_library(Zbar SHARED
src/main/cpp/zbarjni.c
src/main/cpp/zbar/img_scanner.c
src/main/cpp/zbar/decoder.c 
src/main/cpp/zbar/image.c 
src/main/cpp/zbar/symbol.c 
src/main/cpp/zbar/convert.c 
src/main/cpp/zbar/config.c 
src/main/cpp/zbar/scanner.c 
src/main/cpp/zbar/error.c 
src/main/cpp/zbar/refcnt.c 
src/main/cpp/zbar/video.c 
src/main/cpp/zbar/video/null.c 
src/main/cpp/zbar/decoder/code128.c 
src/main/cpp/zbar/decoder/code39.c 
src/main/cpp/zbar/decoder/code93.c 
src/main/cpp/zbar/decoder/codabar.c 
src/main/cpp/zbar/decoder/databar.c 
src/main/cpp/zbar/decoder/ean.c 
src/main/cpp/zbar/decoder/i25.c 
src/main/cpp/zbar/decoder/qr_finder.c 
src/main/cpp/zbar/qrcode/bch15_5.c 
src/main/cpp/zbar/qrcode/binarize.c 
src/main/cpp/zbar/qrcode/isaac.c 
src/main/cpp/zbar/qrcode/qrdec.c 
src/main/cpp/zbar/qrcode/qrdectxt.c 
src/main/cpp/zbar/qrcode/rs.c 
src/main/cpp/zbar/qrcode/util.c)
set(CMAKE_CXX_FLAGS "liconv  ${CMAKE_CXX_FLAGS}")
target_include_directories(Zbar PUBLIC
                src/main/cpp/include
			    src/main/cpp/zbar
			    src/main/cpp/iconv/include)
#######################################################
#######################################################
############<<<<<<<<<<<<<Zbar>>>>>>>>>>>>>>>>##########
find_library(llog  log)
target_link_libraries(Zbar iconv  ${llog})



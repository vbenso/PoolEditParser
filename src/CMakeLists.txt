cmake_minimum_required(VERSION 3.0.0)
project(PoolEditParser VERSION 0.1.0)
project(PoolEditParser LANGUAGES C CXX)

include (CheckSymbolExists)
include (GNUInstallDirs)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wall -Wno-parentheses")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -fno-strict-aliasing")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -DSCM_TIMESTAMPING_OPT_STATS=54")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -g")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -O0")
# set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -pedantic")

set(CMAKE_CXX_FLAGS "${CMAKE_C_FLAGS}")

include_directories (.)
add_library(parser STATIC
    xml.cxx
    parser.cxx
)

add_executable(PoolEditParser pooleditparser.cxx )
target_link_libraries(PoolEditParser
    PRIVATE parser
    expat 
    pthread
)

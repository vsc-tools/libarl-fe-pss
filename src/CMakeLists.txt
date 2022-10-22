
file(GLOB libarl_fe_pss_SRC
  "*.h"
  "*.cpp"
  )

add_library(arl-fe-pss SHARED ${libarl_fe_pss_SRC})

target_include_directories(arl-fe-pss PUBLIC
    ${PROJECT_SOURCE_DIR}/src
    ${PROJECT_SOURCE_DIR}/src/include
    ${LIBVSC_DIR}/src/include
    ${CMAKE_BINARY_DIR}/include
    )

target_link_directories(arl-fe-pss PRIVATE
    ${CMAKE_BINARY_DIR}/lib
    ${CMAKE_BINARY_DIR}/lib64
    )

add_dependencies(arl-fe-pss LibARL)

add_library(arl-fe-pss_static STATIC ${libarl_fe_pss_SRC})

target_include_directories(arl-fe-pss_static PUBLIC
    ${PROJECT_SOURCE_DIR}/src
    ${PROJECT_SOURCE_DIR}/src/include
    ${LIBVSC_DIR}/src/include
    ${CMAKE_BINARY_DIR}/include
    ${Boolector_INCLUDE_DIR}
    )

target_link_directories(arl-fe-pss_static PRIVATE
    ${CMAKE_BINARY_DIR}/lib
    ${CMAKE_BINARY_DIR}/lib64
    )

add_dependencies(arl-fe-pss_static LibARL)

install(TARGETS arl-fe-pss_static
    DESTINATION lib
    EXPORT libarl-fe-pss-targets)


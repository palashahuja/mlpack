# Define the files we need to compile.
# Anything not in this list will not be compiled into mlpack.
set(SOURCES
  naive_bayes_classifier.hpp
  naive_bayes_classifier_impl.hpp
)

# Add directory name to sources.
set(DIR_SRCS)
foreach(file ${SOURCES})
  set(DIR_SRCS ${DIR_SRCS} ${CMAKE_CURRENT_SOURCE_DIR}/${file})
endforeach()
# Append sources (with directory name) to list of all mlpack sources (used at
# the parent scope).
set(MLPACK_SRCS ${MLPACK_SRCS} ${DIR_SRCS} PARENT_SCOPE)

add_executable(mlpack_nbc
  nbc_main.cpp
)
target_link_libraries(mlpack_nbc
  mlpack
)
install(TARGETS mlpack_nbc RUNTIME DESTINATION bin)

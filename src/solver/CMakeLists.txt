# Build library solver
add_library(solver checker.cc trainer.cc solver.cc)

# Build xlearn exe
set(LIBS solver base data loss reader score)

add_executable(xlearn_train train_main.cc)
target_link_libraries(xlearn_train ${LIBS})

add_executable(xlearn_predict predict_main.cc)
target_link_libraries(xlearn_predict ${LIBS})

# Install library and header files
install(TARGETS solver DESTINATION lib/solver)
FILE(GLOB HEADER_FILES "${CMAKE_CURRENT_SOURCE_DIR}/*.h")
install(FILES ${HEADER_FILES} DESTINATION include/solver)

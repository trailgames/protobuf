cmake_minimum_required(VERSION 3.0)

project(protobuf)

add_library(protobuf-lite
    src/google/protobuf/stubs/bytestream.cc                          
    src/google/protobuf/stubs/bytestream.h                           
    src/google/protobuf/stubs/common.cc                              
    src/google/protobuf/stubs/hash.h                                 
    src/google/protobuf/stubs/int128.cc                              
    src/google/protobuf/stubs/int128.h                               
    src/google/protobuf/stubs/io_win32.cc                            
    src/google/protobuf/stubs/io_win32.h                             
    src/google/protobuf/stubs/map_util.h                             
    src/google/protobuf/stubs/mathutil.h                             
    src/google/protobuf/stubs/status.cc                              
    src/google/protobuf/stubs/status.h                               
    src/google/protobuf/stubs/status_macros.h                        
    src/google/protobuf/stubs/statusor.cc                            
    src/google/protobuf/stubs/statusor.h                             
    src/google/protobuf/stubs/stringpiece.cc                         
    src/google/protobuf/stubs/stringpiece.h                          
    src/google/protobuf/stubs/stringprintf.cc                        
    src/google/protobuf/stubs/stringprintf.h                         
    src/google/protobuf/stubs/structurally_valid.cc                  
    src/google/protobuf/stubs/strutil.cc                             
    src/google/protobuf/stubs/strutil.h                              
    src/google/protobuf/stubs/time.cc                                
    src/google/protobuf/stubs/time.h                                 
    src/google/protobuf/arena.cc                                     
    src/google/protobuf/arenastring.cc                               
    src/google/protobuf/extension_set.cc                             
    src/google/protobuf/generated_message_util.cc                    
    src/google/protobuf/generated_message_table_driven_lite.h        
    src/google/protobuf/generated_message_table_driven_lite.cc       
    src/google/protobuf/implicit_weak_message.cc                     
    src/google/protobuf/message_lite.cc                              
    src/google/protobuf/repeated_field.cc                            
    src/google/protobuf/wire_format_lite.cc                          
    src/google/protobuf/io/coded_stream.cc                           
    src/google/protobuf/io/coded_stream_inl.h                        
    src/google/protobuf/io/zero_copy_stream.cc                       
    src/google/protobuf/io/zero_copy_stream_impl_lite.cc
    )

target_include_directories(protobuf-lite PUBLIC src)
target_compile_options(protobuf-lite PRIVATE -DHAVE_PTHREAD)
set_property(TARGET protobuf-lite PROPERTY POSITION_INDEPENDENT_CODE ON)

option(BUILD_PROTOC OFF)

if (BUILD_PROTOC)
    add_library(protobuf
        src/google/protobuf/any.pb.cc                                    
        src/google/protobuf/api.pb.cc                                    
        src/google/protobuf/stubs/mathlimits.cc                          
        src/google/protobuf/stubs/mathlimits.h                           
        src/google/protobuf/any.cc                                       
        src/google/protobuf/descriptor.cc                                
        src/google/protobuf/descriptor_database.cc                       
        src/google/protobuf/descriptor.pb.cc                             
        src/google/protobuf/duration.pb.cc                               
        src/google/protobuf/dynamic_message.cc                           
        src/google/protobuf/empty.pb.cc                                  
        src/google/protobuf/extension_set_heavy.cc                       
        src/google/protobuf/field_mask.pb.cc                             
        src/google/protobuf/generated_message_reflection.cc              
        src/google/protobuf/generated_message_table_driven_lite.h        
        src/google/protobuf/generated_message_table_driven.cc            
        src/google/protobuf/map_field.cc                                 
        src/google/protobuf/message.cc                                   
        src/google/protobuf/reflection_internal.h                        
        src/google/protobuf/reflection_ops.cc                            
        src/google/protobuf/service.cc                                   
        src/google/protobuf/source_context.pb.cc                         
        src/google/protobuf/struct.pb.cc                                 
        src/google/protobuf/stubs/substitute.cc                          
        src/google/protobuf/stubs/substitute.h                           
        src/google/protobuf/text_format.cc                               
        src/google/protobuf/timestamp.pb.cc                              
        src/google/protobuf/type.pb.cc                                   
        src/google/protobuf/unknown_field_set.cc                         
        src/google/protobuf/wire_format.cc                               
        src/google/protobuf/wrappers.pb.cc                               
        src/google/protobuf/io/gzip_stream.cc                            
        src/google/protobuf/io/printer.cc                                
        src/google/protobuf/io/strtod.cc                                 
        src/google/protobuf/io/tokenizer.cc                              
        src/google/protobuf/io/zero_copy_stream_impl.cc                  
        src/google/protobuf/compiler/importer.cc                         
        src/google/protobuf/compiler/parser.cc                           
        src/google/protobuf/util/delimited_message_util.cc               
        src/google/protobuf/util/field_comparator.cc                     
        src/google/protobuf/util/field_mask_util.cc                      
        src/google/protobuf/util/internal/constants.h                    
        src/google/protobuf/util/internal/datapiece.cc                   
        src/google/protobuf/util/internal/datapiece.h                    
        src/google/protobuf/util/internal/default_value_objectwriter.cc  
        src/google/protobuf/util/internal/default_value_objectwriter.h   
        src/google/protobuf/util/internal/error_listener.cc              
        src/google/protobuf/util/internal/error_listener.h               
        src/google/protobuf/util/internal/expecting_objectwriter.h       
        src/google/protobuf/util/internal/field_mask_utility.cc          
        src/google/protobuf/util/internal/field_mask_utility.h           
        src/google/protobuf/util/internal/json_escaping.cc               
        src/google/protobuf/util/internal/json_escaping.h                
        src/google/protobuf/util/internal/json_objectwriter.cc           
        src/google/protobuf/util/internal/json_objectwriter.h            
        src/google/protobuf/util/internal/json_stream_parser.cc          
        src/google/protobuf/util/internal/json_stream_parser.h           
        src/google/protobuf/util/internal/location_tracker.h             
        src/google/protobuf/util/internal/mock_error_listener.h          
        src/google/protobuf/util/internal/object_location_tracker.h      
        src/google/protobuf/util/internal/object_source.h                
        src/google/protobuf/util/internal/object_writer.cc               
        src/google/protobuf/util/internal/object_writer.h                
        src/google/protobuf/util/internal/protostream_objectsource.cc    
        src/google/protobuf/util/internal/protostream_objectsource.h     
        src/google/protobuf/util/internal/protostream_objectwriter.cc    
        src/google/protobuf/util/internal/protostream_objectwriter.h     
        src/google/protobuf/util/internal/proto_writer.cc                
        src/google/protobuf/util/internal/proto_writer.h                 
        src/google/protobuf/util/internal/structured_objectwriter.h      
        src/google/protobuf/util/internal/type_info.cc                   
        src/google/protobuf/util/internal/type_info.h                    
        src/google/protobuf/util/internal/type_info_test_helper.cc       
        src/google/protobuf/util/internal/type_info_test_helper.h        
        src/google/protobuf/util/internal/utility.cc                     
        src/google/protobuf/util/internal/utility.h                      
        src/google/protobuf/util/json_util.cc                            
        src/google/protobuf/util/message_differencer.cc                  
        src/google/protobuf/util/time_util.cc                            
        src/google/protobuf/util/type_resolver_util.cc
        )

    target_include_directories(protobuf PUBLIC src)
    target_link_libraries(protobuf protobuf-lite)

    add_executable(protoc
        src/google/protobuf/compiler/main.cc

        src/google/protobuf/compiler/code_generator.cc                   
        src/google/protobuf/compiler/command_line_interface.cc           
        src/google/protobuf/compiler/plugin.cc                           
        src/google/protobuf/compiler/plugin.pb.cc                        
        src/google/protobuf/compiler/subprocess.cc                       
        src/google/protobuf/compiler/subprocess.h                        
        src/google/protobuf/compiler/zip_writer.cc                       
        src/google/protobuf/compiler/zip_writer.h                        
        src/google/protobuf/compiler/cpp/cpp_enum.cc                     
        src/google/protobuf/compiler/cpp/cpp_enum.h                      
        src/google/protobuf/compiler/cpp/cpp_enum_field.cc               
        src/google/protobuf/compiler/cpp/cpp_enum_field.h                
        src/google/protobuf/compiler/cpp/cpp_extension.cc                
        src/google/protobuf/compiler/cpp/cpp_extension.h                 
        src/google/protobuf/compiler/cpp/cpp_field.cc                    
        src/google/protobuf/compiler/cpp/cpp_field.h                     
        src/google/protobuf/compiler/cpp/cpp_file.cc                     
        src/google/protobuf/compiler/cpp/cpp_file.h                      
        src/google/protobuf/compiler/cpp/cpp_generator.cc                
        src/google/protobuf/compiler/cpp/cpp_helpers.cc                  
        src/google/protobuf/compiler/cpp/cpp_helpers.h                   
        src/google/protobuf/compiler/cpp/cpp_map_field.cc                
        src/google/protobuf/compiler/cpp/cpp_map_field.h                 
        src/google/protobuf/compiler/cpp/cpp_message.cc                  
        src/google/protobuf/compiler/cpp/cpp_message.h                   
        src/google/protobuf/compiler/cpp/cpp_message_field.cc            
        src/google/protobuf/compiler/cpp/cpp_message_field.h             
        src/google/protobuf/compiler/cpp/cpp_message_layout_helper.h     
        src/google/protobuf/compiler/cpp/cpp_options.h                   
        src/google/protobuf/compiler/cpp/cpp_padding_optimizer.cc        
        src/google/protobuf/compiler/cpp/cpp_padding_optimizer.h         
        src/google/protobuf/compiler/cpp/cpp_primitive_field.cc          
        src/google/protobuf/compiler/cpp/cpp_primitive_field.h           
        src/google/protobuf/compiler/cpp/cpp_service.cc                  
        src/google/protobuf/compiler/cpp/cpp_service.h                   
        src/google/protobuf/compiler/cpp/cpp_string_field.cc             
        src/google/protobuf/compiler/cpp/cpp_string_field.h              
        )

    target_include_directories(protoc PUBLIC src)
    target_link_libraries(protoc protobuf pthread)
endif()

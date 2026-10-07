set(_espd_integration_srcs
    "bsp_io_stubs.c"
    "espd_runtime_config.c"
)

if(CONFIG_ESPD_AUDIO_BACKEND_BSP_CODEC)
    list(APPEND _espd_integration_srcs "espd_bsp_codec_dev.c")
endif()

idf_component_register(
    SRCS ${_espd_integration_srcs}
    INCLUDE_DIRS "include"
)

if(CONFIG_ESPD_AUDIO_BACKEND_BSP_CODEC)
    idf_component_optional_requires(PRIVATE espressif__esp_codec_dev esp_codec_dev)
endif()

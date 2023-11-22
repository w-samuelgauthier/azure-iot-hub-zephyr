#-------------------------------------------------------------------------------
# Zephyr Example Application
#
# Copyright (c) 2021 Nordic Semiconductor ASA
# SPDX-License-Identifier: Apache-2.0

cmake_minimum_required(VERSION 3.13.1)
find_package(Zephyr REQUIRED HINTS $ENV{ZEPHYR_BASE})

list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_LIST_DIR}/cmake-modules")
include(AddAzureSDKforC)


project(app LANGUAGES C)

# Include Azure SDK for C headers to app
target_include_directories(app PRIVATE ${azuresdkforc_SOURCE_DIR}/sdk/inc)

target_sources(app PRIVATE
    # Azure SDK for C
    # core lib
    # TODO: remove unnecessary dependencies
    ${azuresdkforc_SOURCE_DIR}/sdk/src/azure/core/az_context.c
    ${azuresdkforc_SOURCE_DIR}/sdk/src/azure/core/az_http_pipeline.c
    ${azuresdkforc_SOURCE_DIR}/sdk/src/azure/core/az_http_policy.c
    ${azuresdkforc_SOURCE_DIR}/sdk/src/azure/core/az_http_policy_logging.c
    ${azuresdkforc_SOURCE_DIR}/sdk/src/azure/core/az_http_policy_retry.c
    ${azuresdkforc_SOURCE_DIR}/sdk/src/azure/core/az_http_request.c
    ${azuresdkforc_SOURCE_DIR}/sdk/src/azure/core/az_http_response.c
    ${azuresdkforc_SOURCE_DIR}/sdk/src/azure/core/az_json_reader.c
    ${azuresdkforc_SOURCE_DIR}/sdk/src/azure/core/az_json_token.c
    ${azuresdkforc_SOURCE_DIR}/sdk/src/azure/core/az_json_writer.c
    ${azuresdkforc_SOURCE_DIR}/sdk/src/azure/core/az_log.c
    ${azuresdkforc_SOURCE_DIR}/sdk/src/azure/core/az_precondition.c
    ${azuresdkforc_SOURCE_DIR}/sdk/src/azure/core/az_span.c
    # IoT lib
    ${azuresdkforc_SOURCE_DIR}/sdk/src/azure/iot/az_iot_adu_client.c
    ${azuresdkforc_SOURCE_DIR}/sdk/src/azure/iot/az_iot_common.c
    ${azuresdkforc_SOURCE_DIR}/sdk/src/azure/iot/az_iot_hub_client.c
    ${azuresdkforc_SOURCE_DIR}/sdk/src/azure/iot/az_iot_hub_client_properties.c
    ${azuresdkforc_SOURCE_DIR}/sdk/src/azure/iot/az_iot_provisioning_client.c
    # Application sources
    src/main.c)

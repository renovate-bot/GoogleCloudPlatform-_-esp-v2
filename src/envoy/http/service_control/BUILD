load(
    "@envoy//bazel:envoy_build_system.bzl",
    "envoy_cc_library",
)

package(
    default_visibility = [
        "//src/envoy/http/service_control:__subpackages__",
        "//src/envoy:__subpackages__",
    ]
)

envoy_cc_library(
    name = "filter_lib",
    srcs = [
        "filter.cc",
        "http_call.cc",
        "token_fetcher.cc",
    ],
    hdrs = [
        "cancel_func.h",
        "filter.h",
        "filter_config.h",
        "http_call.h",
        "token_cache.h",
        "token_fetcher.h",
    ],
    repository = "@envoy",
    deps = [
        "//api/envoy/http/service_control:config_proto_cc",
        "//src/api_proxy/service_control:request_builder_lib",
        "@envoy//source/exe:envoy_common_lib",
    ],
)

envoy_cc_library(
    name = "filter_factory",
    srcs = ["filter_factory.cc"],
    repository = "@envoy",
    deps = [
        ":filter_lib",
        "@envoy//source/exe:envoy_common_lib",
    ],
    visibility = ["//src/envoy:__subpackages__"]
)

cc_library(
    name = "path_matcher_lib",
    srcs = [
        "http_template.cc",
        "http_template.h",
        "path_matcher.h",
        "path_matcher_node.cc",
        "path_matcher_node.h",
    ],
    visibility = ["//visibility:public"],
)

cc_test(
    name = "http_template_test",
    size = "small",
    srcs = ["http_template_test.cc"],
    linkopts = [
        "-lm",
        "-lpthread",
    ],
    linkstatic = 1,
    deps = [
        ":path_matcher_lib",
        "//external:googletest_main",
    ],
)

cc_test(
    name = "path_matcher_test",
    size = "small",
    srcs = ["path_matcher_test.cc"],
    linkopts = [
        "-lm",
        "-lpthread",
    ],
    linkstatic = 1,
    deps = [
        ":path_matcher_lib",
        "//external:googletest_main",
    ],
)
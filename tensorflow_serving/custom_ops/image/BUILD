licenses(["notice"])  # Apache 2.0

package(default_visibility = ["//visibility:public"])

cc_library(
    name = '_image_ops',
    srcs = [
        "cc/kernels/connected_components.cc",
        "cc/kernels/connected_components.h",
        "cc/kernels/euclidean_distance_transform_op.cc",
        "cc/kernels/euclidean_distance_transform_op.h",
        "cc/kernels/image_projective_transform_op.cc",
        "cc/kernels/image_projective_transform_op.h",
        "cc/ops/image_ops.cc",
    ],
    alwayslink = 1,
    deps = [
        "@org_tensorflow//tensorflow/core:framework",
    ]
)

cc_binary(
    name = '_image_ops.so',
    srcs = [
        "cc/kernels/connected_components.cc",
        "cc/kernels/connected_components.h",
        "cc/kernels/euclidean_distance_transform_op.cc",
        "cc/kernels/euclidean_distance_transform_op.h",
        "cc/kernels/image_projective_transform_op.cc",
        "cc/kernels/image_projective_transform_op.h",
        "cc/ops/image_ops.cc",
    ],
    linkshared = 1,
    deps = [
        "@local_config_tf//:libtensorflow_framework",
        "@local_config_tf//:tf_header_lib",
    ],
    features = select({
        ":windows": ["windows_export_all_symbols"],
        "//conditions:default": [],
    }),
    copts = select({
        ":windows": ["/DEIGEN_STRONG_INLINE=inline", "-DTENSORFLOW_MONOLITHIC_BUILD", "/DPLATFORM_WINDOWS", "/DEIGEN_HAS_C99_MATH", "/DTENSORFLOW_USE_EIGEN_THREADPOOL", "/DEIGEN_AVOID_STL_ARRAY", "/Iexternal/gemmlowp", "/wd4018", "/wd4577", "/DNOGDI", "/UTF_COMPILE_LIBRARY"],
        "//conditions:default": ["-pthread", "-std=c++11", "-D_GLIBCXX_USE_CXX11_ABI=0"],
    }),
)

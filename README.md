## About This Repository

This repository contains some changes to Qt 4.8.7, mostly to QMake, to make it easier to build Qt
with the following Visual Studio versions:

* Visual Studio 2010
* Visual Studio 2012
* Visual Studio 2013
* Visual Studio 2015
* Visual Studio 2017
* Visual Studio 2019

## Updates to Qt

Updated `tools/configure/configure.pro` and `tools/configure/configureapp.cpp` to recognize
`win32-msvc2019` as a valid `QMAKESPEC` for Windows.

## Updates to QMake

Added support for QMake variable `MSVC_VERSION`. This obviates the need to use registry and PATH to
deduce the version of Visual Studio for which the .vcxproj file is being generated. This must be
defined for QMake to work properly. The `qmake.conf` files under the following folders have been
updated to define it appropriately.

* mkspecs/win32-msvc2010
* mkspecs/win32-msvc2012
* mkspecs/win32-msvc2013
* mkspecs/win32-msvc2015
* mkspecs/win32-msvc2017
* mkspecs/win32-msvc2019

Added support for QMake variable `MSVC_TARGET_ARCH`. This obviates the need to deduce the target
architecture from the version of Visual Studio found in PATH. This is an optional variable. If this
is not defined, the target architecture defaults to `Win32`. The `qmake.conf` files under the
following folders have been updated to define it to `x64` by default.

* mkspecs/win32-msvc2010
* mkspecs/win32-msvc2012
* mkspecs/win32-msvc2013
* mkspecs/win32-msvc2015
* mkspecs/win32-msvc2017
* mkspecs/win32-msvc2019

Added support for QMake variable `VCPROJ_TARGET_PLATFORM_VERSION`. This variable is optional. This is
useful when there are multiple target platforms but the user want to build against a specific one.
If it is defined, its value is output in the Global PropertyGroup. E.g.

     <WindowsTargetPlatformVersion>10.0.14393.0</WindowsTargetPlatformVersion>


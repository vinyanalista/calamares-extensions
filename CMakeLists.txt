# === This file is part of Calamares - <https://github.com/calamares> ===
#
#   Calamares is free software: you can redistribute it and/or modify
#   it under the terms of the GNU General Public License as published by
#   the Free Software Foundation, either version 3 of the License, or
#   (at your option) any later version.
#
#   Calamares is distributed in the hope that it will be useful,
#   but WITHOUT ANY WARRANTY; without even the implied warranty of
#   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
#   GNU General Public License for more details.
#
#   You should have received a copy of the GNU General Public License
#   along with Calamares. If not, see <http://www.gnu.org/licenses/>.
#
#   SPDX-License-Identifier: GPL-3.0+
#   License-Filename: LICENSE
#
###
#
# This is an example of a repository containing Calamares branding-components
# and Calamares modules and Calamares configuration, showing how a single
# repository can be used to provide customisation for Calamares, so that a
# distro can use an unmodified (upstream) Calamares package and a local
# customisation package in tandem.
#
project(calamares-branding LANGUAGES CXX)
cmake_minimum_required(VERSION 3.2)

find_package(Calamares REQUIRED)
include( "${CALAMARES_USE_FILE}" )

### BRANDING
#
# Typically you would use only one branding, since that's
# the (single) branding for your distro.
#
calamares_add_branding_subdirectory( branding/default NAME default )
calamares_add_branding_subdirectory( branding/fancy NAME fancy )

# This one has files in subdirectories
calamares_add_branding_subdirectory( branding/samegame NAME samegame SUBDIRECTORIES img )

# KaOS branding, with translations
calamares_add_branding_subdirectory( branding/kaos_branding NAME kaos )

### MODULES
#
# Add one of more modules, either C++ or Python.
#
include_directories( ${CALAMARES_INCLUDE_DIRS} )

calamares_add_module_subdirectory( modules/filekeeper )

### CONFIGURATION
#
# (TODO)

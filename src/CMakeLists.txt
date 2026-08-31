# This file is part of FES library.
#
# FES is free software: you can redistribute it and/or modify it under the terms
# of the GNU LESSER GENERAL PUBLIC LICENSE as published by the Free Software
# Foundation, either version 3 of the License, or (at your option) any later
# version.
#
# FES is distributed in the hope that it will be useful, but WITHOUT ANY
# WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR
# A PARTICULAR PURPOSE.  See the GNU LESSER GENERAL PUBLIC LICENSE for more
# details.
#
# You should have received a copy of the GNU LESSER GENERAL PUBLIC LICENSE along
# with FES.  If not, see <http://www.gnu.org/licenses/>.
file(GLOB FES_SOURCES "*.c")
add_library(fes ${FES_SOURCES})
# The static library is linked into the Python extension, which is a shared
# object.  Its object files must therefore be position-independent on Linux.
set_target_properties(fes PROPERTIES POSITION_INDEPENDENT_CODE ON)
target_link_libraries(fes PUBLIC ${NETCDF_LIBRARIES})
install(TARGETS fes DESTINATION lib)

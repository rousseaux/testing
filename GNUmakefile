###############################################################################
# GNUmakefile                                                       [testing] #
# --------------------------------------------------------------------------- #
# This is a GNUmakefile with common high-level targets.                       #
# The .DEFAULT_GOAL identifies the target invoked when non are supplied.      #
# This corresponds to the 'default' attribute of an Ant BuildFile.            #
# Unhandled targets are redirected to the .DEFAULT target.                    #
# It seems Ant has no equivalent functionality for this.                      #
#                                                                             #
# The high-level targets kind of classify the action to be performed, like    #
# showing information, building targets, generating sources, creating         #
# packages, etc. Project specific targets can be named to indicate where they #
# are derived from, like 'build.LX' or 'info.show.history' and such.          #
#                                                                             #
# Recursion / traversion can be accomplished by standard target dependencies  #
# or recursive invocation of Make. It is also a good idea to isolate generic  #
# recipes in macros, so they can be used by multiple targets.                 #
###############################################################################
gnumake.project.name    := testing
gnumake.project.default := default
gnumake.project.id      := c79b229b-f0a7-4e1d-9b88-eabd3a9e7a0c

# Get the name of this Makefile (Should always be first statement)
SELF:=$(lastword $(MAKEFILE_LIST))

# Ant Simple Properties can be used in GNU Make !
include $(gnumake.project.name).properties

# The default target when none are specified.
.DEFAULT_GOAL:=$(gnumake.project.default)

# Prevent Make from deleting intermediate targets
#~ .SECONDARY:

# Prevent Make from applying stock rules
.SUFFIXES:

# Enable the use of $@ and target-specific variables in dependency lists
.SECONDEXPANSION:

# Undefined targets endup here
.DEFAULT:
	@echo [$@ -- UNHANDLED !]
	@echo !!!!!!!!!!!!!!!!!!!!!!!!!
	@echo !! NO ENTRY FOR TARGET !!
	@echo !!!!!!!!!!!!!!!!!!!!!!!!!

# This is the target that gets invoked when no targets are specified
default: info

# Do some initialization
init:
	@echo [$@]
	@echo "out: $(out)"

# Show (project / build) information
info:
	@echo [$@]

# Build the whole shebang
all:
	@echo [$@]

# Use this target to do some custom stuff
custom:
	@echo [$@]

# Generate whatever is needed
generate:
	@echo [$@]

# Build one or more targets
build: $(out)/main.elf
	@echo [$@]

# Create one or more packages for distribution
package: $(out)/testing.tgz
	@echo [$@]

# Distribute stuff to the system or other environments
distribute:
	@echo [$@]

# Install the created package(s)
install:
	@echo [$@]

# Remove the installed package(s)
remove:
	@echo [$@]

# This target can be used for testing
test:
	@echo [$@]

# Clean everything
clean:
	@echo [$@]
	@rm -rf $(out)

#
# -----------------------------------------------------------------------------
#

# Build the ELF executable
$(out)/main.elf: $(src)/main.c
	@mkdir -p out
	gcc $< -o $@

# Package it in a tarball
$(out)/testing.tgz: $(out)/main.elf
	@rm -f $@
	tar cvfz $@ -C $(out) $(notdir $<)

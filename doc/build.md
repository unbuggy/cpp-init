# Build Instructions

Building this project from scratch entails three steps.  Don't worry; unless something goes wrong, the build is fast and easy.  The caveats are as follows:

* The build system assumes OS X.  Porting to other Unixes should be straight-forward.

* Your shell is assumed to be Bash-like.  If you want to use csh, you'll need to do a little setup; for example, translating etc/profile to etc/login.

Patches are welcome.

First, make sure your environment is correctly configured.  Whenever you're going to work on this project from a new shell instance, configure the shell by sourcing etc/profile from the top of the repository:

    . etc/profile

This prepends the `bin` directory to your path, so you can call the Bake
makefile generator generator (sic) from the source directory:

    bake

Bake first builds the makefile generator `mkmk`, then generates a `Makefile`
and uses your system `make` command to build the code.  Going forward, you can
just call `make` from the source directory:

    cd src
    make

If you change physical dependencies -- e.g., you add a new source file, or a
`#include` of one file by another, just re-run `bake` once to regenerate the
`Makefile`.

# Environment modules

## Setup
On ubuntu 24.04, install `environment-modules` package.
Append to your `~/.bashrc`:

```bash
case "$0" in
          -sh|sh|*/sh)	modules_shell=sh ;;
       -ksh|ksh|*/ksh)	modules_shell=ksh ;;
       -zsh|zsh|*/zsh)	modules_shell=zsh ;;
    -bash|bash|*/bash)	modules_shell=bash ;;
esac
export MODULEPATH=~/modules
module() { eval `/usr/bin/tclsh8.6 '/usr/lib/x86_64-linux-gnu/modulecmd.tcl' $modules_shell $*`; }
```

Re-login for changes 

## Usage
Listing available and loaded modules:

```console
$ module avail

nohous@uss-lollipop:~/modules$ module avail
----------------------------------------- /home/nohous/modules -----------------------------------------
dsim     ghdl     qt       questa-intel  verilator  vivado-2019.2  
gcc-arm  openocd  quartus  verible       vivado     vivado-2024.1  

Key:
modulepath  
```

Multiple modules can be loaded at the same time, provided they do not interfere with other.

To load environment defined by a module, run:

```shell
module load vivado
```

A loaded module can be dynamically unloaded to rollback changes caused to your current environment:

```shell
module unload vivado
```

## Creating modules

Best advice is to have a look at some modules in this repo.
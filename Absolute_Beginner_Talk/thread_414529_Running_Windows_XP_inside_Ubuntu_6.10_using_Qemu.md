---
title: "Running Windows XP inside Ubuntu 6.10 using Qemu"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by esc0587 on 2007-04-19
I am a beginner and wanted to know how to run Windows XP inside Ubuntu 6.10 using Qemu. I have used this script to install Qemu and Kqemu.  The thing is that I have never done this before, so I wanted a step by step set of instructions on how to do this.  Remember I am a beginner!


#!/bin/bash
# This script was created by Felipe Caballero
#
# Meant (and tested) to be executed on Ubuntu 6.10, should work on 6.06 and 5.10 as well
# Probably works on regular Debian too
#
# This script installs qemu as a package, wich can be removed as a regular package
# via Synaptic or console typing: apt-get -r qemu
#
# No warranty is given, use it at your own risk - It shouldn't mess up your system anyway
#
# It will install several packages needed to compile Qemu by default, 
# it will not ask for confirmation to install this packages,
# to change this comment the variable IPBD

# This script is supposed to be run as root beacause it does administratif operations
if [ $USER != "root" -o $UID != 0 ]; then
	echo "This script is meant to be run as root"
	exit 1
fi

function clean {
	rm -rf $QEMU_HOME; rm -rf $KQEMU_HOME; rm -rf $QEMU_TAR; rm -rf $KQEMU_TAR
	echo ;
	echo "To avoid file corruption and/or IO errors, tar are deleted and directories too"
	echo "See the log files and then run the script again"
	echo ; echo ;
}

# These are the variables needed
echo "Creating Variables..." ; echo ;

QEMUVERSION=0.8.2
KQEMUVERSION=1.3.0pre9
# The following two variables are the package (file) name
QEMU_TAR=qemu-${QEMUVERSION}.tar.gz
KQEMU_TAR=kqemu-${KQEMUVERSION}.tar.gz
# The next two variables are the download url to download Qemu and KQemu
# If it doesn't work for the version of Qemu or KQemu, verify the url's
QEMUPKGSOURCE=http://fabrice.bellard.free.fr/qemu/${QEMU_TAR}
KQEMUPKGSOURCE=http://fabrice.bellard.free.fr/qemu/${KQEMU_TAR}

# Self explanatory variables
INSTALL_HOME=/home/${USER}/qemu+kqemu
QEMU_HOME=${INSTALL_HOME}/qemu-$QEMUVERSION
KQEMU_HOME=${INSTALL_HOME}/kqemu-${KQEMUVERSION}
LOG=${INSTALL_HOME}/log
ERROR_LOG=${INSTALL_HOME}/error_log
IPBD="--yes"

mkdir -p $INSTALL_HOME
cd $INSTALL_HOME

# Log and error_log are removed every time the script is executed for practical reasons
touch $LOG; rm $LOG ; touch $LOG;
touch $ERROR_LOG; rm $ERROR_LOG; touch $ERROR_LOG;

echo "To see the output, look at the log file in $INSTALL_HOME/log"
echo "To see the error output, look at the log file in $INSTALL_HOME/error_log"
echo 
# QEmu's source as well as KQemu binaries
echo "Retrieving Packages (i.e qemu source code and kqemu binaries)..."
echo "wget -nv $QEMUPKGSOURCE"
wget -nv $QEMUPKGSOURCE >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR downloading Qemu Source Package"; clean; exit 1; }
echo "wget -nv $KQEMUPKGSOURCE"
wget -nv $KQEMUPKGSOURCE >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR downloading KQemu Binary Package"; clean; exit 1; }
echo

# Downloaded packages are unpackaged
echo "unpackaging retrieved packages..."
tar xzf qemu-${QEMUVERSION}.tar.gz >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR doing untar of Qemu Source Package"; clean; exit 1; }
tar xzf kqemu-${KQEMUVERSION}.tar.gz >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR doing untar of KQemu Binary Package"; clean; exit 1; }
echo

# Necessary packages are installed
echo "Installing needed extra packages..."
echo "apt-get install gcc-3.4..."
apt-get install gcc-3.4 $IPBD >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR installing: gcc-3.4"; clean; exit 1; }
echo "apt-get install libsdl1.2debian-all libsdl1.2-dev"
apt-get install libsdl1.2debian-all libsdl1.2-dev --yes >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR installing: libsdl1.2debian-all libsdl1.2-dev"; clean; exit 1; }
echo "apt-get install linux-headers-$(uname -r)"
apt-get install linux-headers-$(uname -r) --yes >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR installing: linux-headers-$(uname -r)"; clean; exit 1; }
echo "apt-get install checkinstall"
apt-get install checkinstall --yes >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR installing: checkinstall"; echo "Please load \"Community maintained Open Source software (universe)\" from Synaptic Package Manager"; echo "or edit apt source files"; clean; exit 1; }
echo "apt-get build-dep qemu"
apt-get build-dep qemu --yes >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR doing: apt-get build-dep qemu"; clean; exit 1; }
echo

cd $QEMU_HOME

# Preparing compilation
echo "Runing the configuration script for Qemu..."
./configure --cc=gcc-3.4 --host-cc=gcc-3.4 --kernel-path=/usr/src/linux-headers-$(uname -r)  >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR runing the configuration script for Qemu"; clean; exit 1; }
echo

# The file usb-linux.c is problematic under Ubuntu 6.10
# some changes are necessary
echo "Configuring file usb-linux.c ..."
sed -i "s/#include <linux\/compiler.h>/#include <\/usr\/src\/linux-headers-$(uname -r)\/include\/linux\/compiler.h>/" usb-linux.c >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR editing usb-linx.c"; clean; exit 1; }
echo

# Qemu gets compiled
echo "Qemu compilation"
echo "make clean..."
make clean >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR: make clean"; clean; exit 1; }
echo "make..."
make >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR: make"; clean; exit 1; }
echo

# Qemu package is made
echo "Creating Installation package and Installing it..."
checkinstall -y --pkgname=qemu --pkgversion=${QEMUVERSION} --pkgrelease=1 --pkglicense=Restricted --pkggroup="Miscellaneous - Text Based" --pkgsource=$QEMUPKGSOURCE --exclude=kqemu/install.sh >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR creating Qemu package"; clean; exit 1; }
echo

# KQemu gets installed
echo "KQemu installation"
cd $KQEMU_HOME
echo "Configuring KQemu..."
./configure >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR configuring KQemu"; clean; exit 1; }
echo "make..."
make >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR: make"; clean; exit 1; }
echo "make install"
make install >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR: make install"; clean; exit 1; }

---

### Post by rich.bradshaw on 2007-04-20
I just did

apt-get install qemu kqemu

to install.

I would advise never doing things a complex way when there is an easy way...

---

### Post by esc0587 on 2007-04-20
After Installing qemu and kqemu, how did you run windows.  Sorry but can you give me a more specific command on how to actually run windows once qemu is installed?

---

### Post by kwilliam on 2007-04-21
Edit:  Oh, I just found this page: [https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo).  This has a lot more information.  I suggest using it instead of what I just wrote. :-)

Original message:

Try this:

First navigate to the directory you want to keep your "virtual machines" in.  (I made a folder called "Virtual_Machines" in my home directory.)
```
cd ~/Virtual_Machines
```

Create a file for the virtual disk drive. Using the '-f qcow' option as shown below saves space, by not using the space until the guest does (till the maximum size of the disk is read). 
```
qemu-img create myimage.img -f qcow 6G
```

Insert the Windows install CD and run: 
```
qemu -no-acpi -m 384 -cdrom /dev/cdrom -boot d myimage.img
```


I got these instructions from [this page](https://help.ubuntu.com/community/KVM) which is for KVM and modified them to use qemu instead of kvm.  It ought to work, because KVM is basically an extension of qemu.

---


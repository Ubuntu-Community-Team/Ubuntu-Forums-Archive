---
title: "script file/diff files"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-03-30
here is a script file
and below is the diff file which part of the diff file files goes in the script file please?
thanks

Lex1:o 
---------------------------
script file

#!/bin/sh
#
# How to write a shell script
# [http://vertigo.hsrl.rutgers.edu/ug/shell_help.html](http://vertigo.hsrl.rutgers.edu/ug/shell_help.html)
#

# Script configuration
# ====================
  BASE_DIR=/root
# BASE_DIR=/usr/local
# BASE_DIR=/tmp
	SRC_DIR=qemu-src
	QEMUVERSION=0.7.2
	PKGSOURCE=http://fabrice.bellard.free.fr/qemu/qemu-${QEMUVERSION}.tar.gz

# Script starts executing here
# ============================
echo
echo "InsQEMU - version 0.1 (2005-12-15)"
echo "======= by Nando Florestan -- http://oui.com.br/n"
echo "This script downloads and installs QEMU ${QEMUVERSION},"
echo "with the KQEMU accellerator, in Ubuntu 5.10 Breezy Badger."
echo "Based on:"
echo "http://www.hants.lug.org.uk/cgi-bin/wiki.pl?LinuxHints/QemuCompilation"
echo
echo "If this script succeeds, you will see a message at the end saying:"
echo "\"InsQEMU SUCCEEDED!\""
echo "...else you have some problem."
echo
echo "If you have any difficulties, you can edit the script yourself."
echo "It is heavily commented so as to help."
echo "Please send any bug corrections to [email]nandoflorestan@gmail.com[/email]"
echo

if [ $USER != "root" -o $UID != 0 ]; then
	echo "This script must be run as root. Type this to become root:"
	echo "sudo -s"
	echo "...then run this script again."
	echo
	exit 1
fi

echo "First of all, we install the dependencies."
# Ubuntu Breezy 5.10 and Debian Sid come with GCC 4.0 by default, but
# Qemu 0.72 will not compile with GCC 4.0 so we need to install GCC 3.4
# The SDL packages should provide sound support
# zlib is a compression library
# checkinstall is for generating .deb packages
apt-get install gcc-3.4 g++-3.4 libsdl1.2debian libsdl1.2debian-all build-essential libsdl1.2-dev zlib1g-dev checkinstall || exit 2

echo
echo "Finding out whether your kernel is i386 or i686."
# Run "uname -m" and store the result in the variable KERNEL
KERNEL=`uname -m` || exit 10

# Depending on KERNEL, get a package
if [ $KERNEL=="i686" ]; then
	echo "Downloading Linux headers for i686..."
	apt-get install linux-headers-686  || exit 11
else
	echo "Downloading Linux headers for i386..."
	apt-get install linux-headers-386  || exit 12
fi
echo

cd   ${BASE_DIR} || exit 3
mkdir ${SRC_DIR} || echo
cd    ${SRC_DIR} || exit 4
echo

# If the directory does NOT exist yet
if [ ! -d qemu-${QEMUVERSION}/kqemu ]; then
	echo "Downloading QEMU..."
	wget -nv ${PKGSOURCE}  || exit 5
	echo
	echo "Downloading KQEMU..."
	wget -nv http://fabrice.bellard.free.fr/qemu/kqemu-${QEMUVERSION}.tar.gz || exit 6
	echo
	echo "Uncompressing QEMU..."
	tar zxvf qemu-${QEMUVERSION}.tar.gz     || exit 7
	echo
	echo "Entering source dir."
	cd qemu-${QEMUVERSION}                  || exit 8
	echo
	echo "Uncompressing KQEMU..."
	tar zxvf ../kqemu-${QEMUVERSION}.tar.gz || exit 9
else
	echo "Directory already exists: ${BASE_DIR}/qemu-src/qemu-${QEMUVERSION}"
	echo "I will use its files instead of downloading them from the internet."
	cd qemu-${QEMUVERSION}
fi

echo "BEGINNING CONFIGURE !"
# sh configure  || exit 13
export CPP=g++-3.4
export CC=gcc-3.4
sh ./configure --prefix=/usr --cc=gcc-3.4 --host-cc=gcc-3.4 --kernel-path=/usr/src/linux-headers-$(uname -r)/ || exit 13
echo
echo

echo "BUILDING QEMU !"
# In Ubuntu Breezy, if you just `make`, it will use GCC 4.0
# even though we configured for GCC 3.4. So we need this workaround:
# Change the symlink, compile, then change the symlink back
mv     /usr/bin/gcc     /usr/bin/gcc.bak
ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc
make
EXITCODE=$?
mv     /usr/bin/gcc.bak /usr/bin/gcc
echo

if [ $EXITCODE != 0 ]; then
	echo "PROBLEM IN MAKE: ${EXITCODE}"
	exit 14
fi

echo "Now let us remove Qemu if it is installed..."
apt-get remove qemu  || exit 15
echo

# Now make the PACKAGE. Using checkinstall is a great way to
# install applications because it makes '.deb' packages.
# This means Qemu can later be removed via apt-get or Synaptic.
echo "QEMU is a generic processor emulator. This package was compiled by InstQEMU.sh and also contains the KQEMU accellerator. http://fabrice.bellard.free.fr/qemu" > description-pak || exit 16
# The reason for overwriting install.sh so it is empty is
# to ensure the package made with checkinstall can install cleanly
cat /dev/null > kqemu/install.sh                || exit 17
# Create the .deb package
checkinstall -y --pkgname=qemu --pkgversion=${QEMUVERSION} --pkgrelease=1 --pkglicense=Restricted --pkggroup="Miscellaneous - Text Based" --pkgsource=$PKGSOURCE --exclude=kqemu/install.sh           || exit 18

echo "QEMU is now installed."
echo
echo "Loading the KQEMU kernel module..."
mkdir -p /lib/modules/$(uname -r)/misc && cp kqemu/kqemu.ko /lib/modules/$(uname -r)/misc && depmod -a
modprobe kqemu           || exit 19 # Load the kernel module
mknod /dev/kqemu c 250 0 || exit 20 # Create the KQEMU device
chmod 666 /dev/kqemu     || exit 21 # Make it accessible to all users    
echo

echo "When you reboot, the KQEMU accellerator will not load anymore."
echo "But you can add a few lines to a boot script to fix this."
echo "For more details, please refer to:"
echo "http://fabrice.bellard.free.fr/qemu/kqemu-doc.html"
echo
echo "InsQEMU SUCCEEDED!"
exit 0
-------------------------------------------------------------------------------------------------

here is diff file

# diff -su insQEMU.sh~ insQEMU.sh |less


--- insQEMU.sh~ 2006-01-10 11:45:32.000000000 -0500
+++ insQEMU.sh  2006-03-30 06:48:39.000000000 -0500
@@ -49,18 +49,19 @@
 apt-get install gcc-3.4 g++-3.4 libsdl1.2debian libsdl1.2debian-all build-essential libsdl1.2-dev zlib1g-dev checkinstall || exit 2

 echo
-echo "Finding out whether your kernel is i386 or i686."
+#TEST#echo "Finding out whether your kernel is i386 or i686."
 # Run "uname -m" and store the result in the variable KERNEL
+#TEST#KERNEL=`uname -m` || exit 10
 KERNEL=`uname -m` || exit 10

 # Depending on KERNEL, get a package
-if [ $KERNEL=="i686" ]; then
-       echo "Downloading Linux headers for i686..."
-       apt-get install linux-headers-686  || exit 11
-else
+#TEST#if [ $KERNEL=="i686" ]; then
+       #TEST#echo "Downloading Linux headers for i686..."
+       #TEST#apt-get install linux-headers-686  || exit 11
+#TEST#else
        echo "Downloading Linux headers for i386..."
        apt-get install linux-headers-386  || exit 12
-fi
+#TEST#fi
 echo

 cd   ${BASE_DIR} || exit 3

--------------------------------------------------------------------------------------------

---

### Post by htinn on 2006-03-31
patch < somefile.diff

---


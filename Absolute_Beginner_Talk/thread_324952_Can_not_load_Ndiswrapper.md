---
title: "Can not load Ndiswrapper"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by jlr4u on 2006-12-24
Ndiswrapper Wireless

I am having trouble connecting my wireless card. Since I do not have internet connection, I downloaded ndiswrapper-1.32.tar.gz on another computer and copied the file to my desktop and extracted it to the desktop. From there I opened up the Install file which stated:

ls /lib/modules/`uname -r`/build

should have at least 'include' directory and '.config' file.

The include file was listed, but I did not see any directory with a .config.file.
I went ahead with the load from a terminal window as follows:

CD Desktop/ndiswrapper-1.32
make uninstall
make

sudo -i --Login as root and run
make install

Each command I run has errors:

The first error is in the Make Uninstall and is
removing /lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper
/bin/rm: cannot remove `/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper': Permission denied

My questions are:

1. What is going on with Permission denied?
2. What is the 'include' directory and '.config' file. .config not showing up.

---

### Post by MkfIbK7a on 2006-12-24
i suggest downloading 
ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb, and
ndiswrapper-common_1.18-1ubuntu2_all.deb
and installing them the doing



Code:

 $ sudo mv /usr/sbin/ndiswrapper /usr/sbin/ndiswrapper_blah [To make a backup, the name reflects my frustration ;) ) 
 $ sudo cp /usr/sbin/ndiswrapper-1.8 /usr/sbin/ndiswrapper [Replace the broken bin with the older, stable version]

---

### Post by spockrock on 2006-12-24
the first command should be;
sudo make uninstall

then if you want to do a fresh re-install, then do this; make clean
then run;

make 
sudo make install

then load the windows driver into ndiswrapper, and then load ndiswrapper module into the kernel.

---


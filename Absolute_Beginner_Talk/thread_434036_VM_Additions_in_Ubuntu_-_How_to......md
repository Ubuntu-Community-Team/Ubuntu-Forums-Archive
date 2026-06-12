---
title: "VM Additions in Ubuntu - How to....."
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Loki-uk on 2007-05-05
OK this was a bit of a misison, I'm a linux newbie so this took me a couple 
of weeks to figure out. This is how to install the VM Additions for Linux into Ubuntu under Virtual PC. 

First you need the following packages installed (and their dependancies) - 

alien
build-essential
fileutils
linux-headers-2.x.xx-xx-386 where the xx's are oyur kernel version
(you can find your kernel version by using 'uname -r' in the terminal)
linux-image-2.x.xx-xx-386 - should already be installed
linux-restricted-modules-2.x.xx-xx-386
linux-source-2.x.xx

Reboot once these are installed

Download chkconfig from [http://www.fastcoder.net/downloads/](http://www.fastcoder.net/downloads/)

from a terminal unpack it using 'tar xvf chkconfig-1.3.30a.tar.bz2'

Then use the following commands to build it

sudo -i
enter your user password when prompted
cd /home/YOUR USER NAME/ANY OTHER FOLDERS/chkconfig-1.3.30a
./configure --enable-ntsysv
make
make install
ln -fs /usr/local/sbin/chkconfig /usr/bin
ln -fs /usr/local/sbin/ntsysv /usr/bin
ln -fs /usr/local/sbin/chkconfig /sbin

mount the vm additions iso and then you need to change to your cdrom 

cd /media/cdrom

sudo -i
enter your user password when prompted

rpm -ivh vmadd-full-0.0.1-1.i386.rpm --force --nodeps

Then to start the vmadd service type 

/etc/init.d/vmadd start

Then 

/etc/init.d/vmadd-SERVICENAME start

You will need to add 'vmadd start' and the 'vmadd-servicename start' to 
modules to start them automatically each time ubuntu boots.

Loki-uk

---


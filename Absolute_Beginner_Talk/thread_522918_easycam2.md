---
title: "easycam2"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by lxstoian on 2007-08-11
I have a problem after installing and running easycam2. When i click install driver it says it can't run Make Install.:confused:

---

### Post by yorkie on 2007-08-11
did you use    sudo make install
just in case you missed some command have alook at
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

---

### Post by Fedora314 on 2007-12-27
I've been having much the same problem. The camera works despite the error... just. Images are unusually dark (as opposed to the same camera running in Windows)

This is the output from running **sudo lauchcam2**:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.22-14-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libgnucrypto-java libcairo-jni libgtk-jni libcairo-java libglib-jni
  libbcprov-java libglib-java libgtk-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ln: creating symbolic link `/lib/modules/2.6.22-14-generic/build/linux-headers-2.6.22-14-generic' to `/usr/src/linux-headers-2.6.22-14-generic': File exists
ERROR: Module spca5xx does not exist in /proc/modules
mkdir: cannot create directory `/lib/modules/2.6.22-14-generic/kernel/drivers/usb/media-back': File exists
cp: cannot stat `/lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/*': No such file or directory
mknod: `/dev/video0': File exists
mknod: `/dev/video1': File exists
ln: creating symbolic link `/dev/video' to `/dev/video0': File exists
rm -r -f drivers/usb/*.o drivers/usb/.spcadecoder.o.cmd \
        drivers/usb/.spca5xx.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i
mkdir -p /lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/
rm -f /lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/spca50x.ko
rm -f /lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/et61x.ko
install -c -m 0644 spca5xx.ko /lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/
install: cannot stat `spca5xx.ko': No such file or directory
make: *** [install] Error 1

---

### Post by hax80r on 2007-12-27
I have the same problem.

> Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-headers-2.6.22-14-generic is already the newest version.
The following packages were automatically installed and are no longer required:
libgnucrypto-java libcairo-jni libgtk-jni libcairo-java libglib-jni
libbcprov-java libglib-java libgtk-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ln: creating symbolic link `/lib/modules/2.6.22-14-generic/build/linux-headers-2.6.22-14-generic' to `/usr/src/linux-headers-2.6.22-14-generic': File exists
ERROR: Module spca5xx does not exist in /proc/modules
mkdir: cannot create directory `/lib/modules/2.6.22-14-generic/kernel/drivers/usb/media-back': File exists
cp: cannot stat `/lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/*': No such file or directory
mknod: `/dev/video0': File exists
mknod: `/dev/video1': File exists
ln: creating symbolic link `/dev/video' to `/dev/video0': File exists
rm -r -f drivers/usb/*.o drivers/usb/.spcadecoder.o.cmd \
drivers/usb/.spca5xx.o.cmd *.o *.ko *.mod.* .[a-z]* core *.i
mkdir -p /lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/
rm -f /lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/spca50x.ko
rm -f /lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/et61x.ko
install -c -m 0644 spca5xx.ko /lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/
install: cannot stat `spca5xx.ko': No such file or directory
make: *** [install] Error 1

---

### Post by Carnevagorion on 2008-01-31
I have also the same problem. Here is what I get when I try to install a webcamdriver with Easycam2:

bram@Bram:~$ sudo lauchcam2
[sudo] password for bram:
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
Reading state information... Klaar
linux-headers-2.6.22-14-generic is reeds de nieuwste versie.
The following packages were automatically installed and are no longer required:
  libboost-date-time1.34.1
Use 'apt-get autoremove' to remove them.
0 pakketten opgewaardeerd, 0 pakketten nieuw geïnstalleerd, 0 te verwijderen en 2 niet opgewaardeerd.
ln: creating symbolic link `/lib/modules/2.6.22-14-generic/build/linux-headers-2.6.22-14-generic' to `/usr/src/linux-headers-2.6.22-14-generic': File exists
ERROR: Module spca5xx does not exist in /proc/modules
mkdir: cannot create directory `/lib/modules/2.6.22-14-generic/kernel/drivers/usb/media-back': File exists
mknod: `/dev/video0': File exists
mknod: `/dev/video1': File exists
ln: creating symbolic link `/dev/video' to `/dev/video0': File exists
rm -r -f drivers/usb/*.o drivers/usb/.spcadecoder.o.cmd \
        drivers/usb/.spca5xx.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i
mkdir -p /lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/
rm -f /lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/spca50x.ko
rm -f /lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/et61x.ko
install -c -m 0644 spca5xx.ko /lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/
install: cannot stat `spca5xx.ko': No such file or directory
make: *** [install] Error 1
bram@Bram:~$ 


What can I do about it? Anyone any suggestions?

Greetings from the Netherlands, Bram

---

### Post by eekfonky on 2008-02-17
Same here:

```
chris@ubuntu:~$ lauchcam2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.22-14-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  thunderbird-locale-en-gb mozilla-firefox-locale-en-gb
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
rm -r -f drivers/usb/*.o drivers/usb/.spcadecoder.o.cmd \
        drivers/usb/.spca5xx.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i
mkdir -p /lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/
rm -f /lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/spca50x.ko
rm -f /lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/et61x.ko
install -c -m 0644 spca5xx.ko /lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/
install: cannot stat `spca5xx.ko': No such file or directory

```

---


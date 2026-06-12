---
title: "Webcam (make problem)"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by DiscoKiller on 2006-01-11
Hi all, 

I`m trying to install the spca5xx drivers to try and breathe some life into my new webcam but as yet to no avail. I`ve seen people with problems installing this driver but i seem to be having a different problem as they are. My problem is this... the HowTo tells me to enter this command into the terminal

cd spca5xx-<version>; make;

upon doing this i get an error message as follows...

mike@ResNetUser-CefnyCoed-147:~/Desktop$ cd spca5xx-20051212; make;
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/mike/Desktop/spca5xx-20051212 CC=cc modules
make: *** /lib/modules/2.6.12-10-386/build: No such file or directory.  Stop.
make: *** [default] Error 2

when i look in /lib/modules/2.6.12-10-386 there is a file called build but it is a broken link. How do i correct this as i`ve just bought a webcam and really want it to work :S

---

### Post by DiscoKiller on 2006-01-11
Fixed it......for now :D

my solution was to install missing packages which i presume created a new 'build' file

the command i used was 

apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4 

peace DK

---

### Post by az on 2006-01-11
There is a wiki page about this.  It works.

---

### Post by DiscoKiller on 2006-01-13
thats what i tried to start off with but i`m having no luck

i put in what it tells me to then i get a holw load of other stuff i dont understand

i`ll get it eventually

---

### Post by chele on 2006-01-14
I used this  [https://wiki.ubuntu.com/Webcam]("https://wiki.ubuntu.com/Webcam") to automagically build new drivers for my webcam.

---


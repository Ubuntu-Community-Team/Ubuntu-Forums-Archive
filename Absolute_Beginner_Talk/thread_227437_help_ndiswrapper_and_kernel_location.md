---
title: "help: ndiswrapper and kernel location"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by gary201147 on 2006-08-01
im trying to install drivers for my wireless usb device

right now i am trying to install ndiswrapper. i was missing the "build essential" package, which allowed to use the command <make>

but when i try to "make install" i get this:

Can't find kernel build files in /lib/modules/2.6.15-23-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make

i have already been to the official ubuntu help site for ndiswrapper and driver installation.

i followed the command line to create a link:

ln -s /usr/src/linux-2.6.15-23-386 /lib/modules/2.6.15-23-386/build

but the problem is that the link goes to /usr/src/linux-2.6.15-23-386 which does not exist. in fact, where is the kernel?

also, i am trying to see if there are any usable drivers in the linux-wlan-ng package. i have already downloaded/installed the package using synaptec but i dont know where they are installed! what is the default directory for package installation? i know that programs are stored in /usr/lib but i couldnt find it there. 

help!!

tia,gary

---

### Post by sas on 2006-08-01
Do you have linux-source and linux-headers-386 installed?

---

### Post by gary201147 on 2006-08-01
seeing that they are available to download on synaptec, i would assume that I dont have these packages. i am downloading them now, what then? should the appropriate folders/directories show up?

also, what is actually installed when ubuntu is installed. i feel like there are so many packages that should be included on the installation disk. for example, you are extremely limited to what you can do if you dont have the build essential meta package...

---

### Post by sas on 2006-08-01
I'm guessing so. I'm not certain though.

If I remember correctly build-essential will be installed by default with the next release.

---


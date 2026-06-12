---
title: "New compiled kernel doesn't show up in GRUB"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by fd9_ on 2007-07-17
I am trying to follow the instructions here ( 
[http://forums.fedoraforum.org/forum/showthread.php?t=159550](http://forums.fedoraforum.org/forum/showthread.php?t=159550) )  in order to install the Intel drivers for my 4965 a/g/n wifi card. I believe I have successfully  recompiled my kernel using the following commands:

make oldconfig
make
make modules_install
make install

...but the new kernel is not showing up in GRUB. I have tried doing this twice, with two  different kernels, and neither of them show up in GRUB.

---

### Post by glennric on 2007-07-17
Follow the directions on the [Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158") to compile a kernel.

---

### Post by deadlikeoscar on 2007-07-17
Do these instructions look similar?

[http://ubuntuforums.org/showthread.php?t=311158]("http://ubuntuforums.org/showthread.php?t=311158")

---

### Post by fd9_ on 2007-07-17
I am now following the instructions at the link you provided, and I am trying to do:

```

cp /boot/config-`uname -r` .config && make oldconfig
```

but i get the error: "cp: cannot start '/boot/config-uname -r': No such file or directory"

Typing these commands in the console is very frustrating...if you guys told me what needed to be done via GUI I could probably do it much faster and easier. I noticed that most of these commands are just moving files or creating folders.

---

### Post by fd9_ on 2007-07-18
Also, when I try:

```
sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget libncurses5 libncurses5-dev
```

I get:

```
E: Couldn't find package bin86
```

Any suggestions?

---

### Post by 5-HT on 2007-07-18
> **fd9_ said:**
> I am trying to follow the instructions here ( 
[http://forums.fedoraforum.org/forum/showthread.php?t=159550](http://forums.fedoraforum.org/forum/showthread.php?t=159550) )  in order to install the Intel drivers for my 4965 a/g/n wifi card. I believe I have successfully  recompiled my kernel using the following commands:

make oldconfig
make
make modules_install
make install

...but the new kernel is not showing up in GRUB. I have tried doing this twice, with two  different kernels, and neither of them show up in GRUB.

GRUB will not automagically update itself, you need to do that yourself. 
Debian and Ubuntu do have a nifty script that will update GRUB for you, but you'll need to compile your kernel the 'Ubuntu Way' to create the appropriate .debs so your kernel and all associated components can be integrated into apt and the script can do its magic.

> **glennric said:**
> Follow the directions on the [Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158") to compile a kernel.

This Thread will show you how to compile a kernel the 'Ubuntu Way' so that GRUB will update itself automagically.

> **fd9_ said:**
> I am now following the instructions at the link you provided, and I am trying to do:

```

cp /boot/config-`uname -r` .config && make oldconfig
```but i get the error: "cp: cannot start '/boot/config-uname -r': No such file or directory"

Typing these commands in the console is very frustrating...if you guys told me what needed to be done via GUI I could probably do it much faster and easier. I noticed that most of these commands are just moving files or creating folders.

What version of Ubuntu are you running? Kernel configuration files *should* be placed in /boot/config-*kernel_version*. That cp command will copy over the kernel config from your currently running kernel to the current working directory. The error says that the file is not present- maybe it's not there. Did you make sure to include the backsticks (`), because those are necessary in order for BASH to complete the `uname -` into the appropriate string for your currently running kernel.

GUI way? Of course!
```
gksudo nautilus /boot 
```That will bring up a file-manager with root privs showing the contents of /boot. Look for the appropriate config file there, and copy it over to the top-level directory in which you are doing the kernel compilation.

> **fd9_ said:**
> Also, when I try:

```
sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget libncurses5 libncurses5-dev
```I get:

```
E: Couldn't find package bin86
```Any suggestions?

bin86 is in the official repos for all Ubuntu releases. Try a 'sudo apt-get update' prior to installing the package. If there's still a problem, there may be a problem with your /etc/apt/sources.list which needs to be addresses. An easy way to grab the package without dealing with your sources.list would be to venture over to packages.ubuntu.com and grab bin86 from there.


** NOTE:** The iwlwifi driver will need the new mac80211 wireless subsystem installed. If you are running a kernel >=2.6.22 which has the new subsystem included, or a kernel which has already been patched for it, there is no need to recompile your kernel: simply compile and install the iwlwifi driver against your current kernel and install the firmware (you'll need the kernel headers and/or source for that). Normally, however, there would be absolutely no need to go through a kernel compilation to compile and install a driver. 

Cheers,

---


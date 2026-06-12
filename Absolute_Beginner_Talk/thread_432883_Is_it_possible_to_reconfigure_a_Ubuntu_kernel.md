---
title: "Is it possible to reconfigure a Ubuntu kernel??"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-05-04
Hi,

I'd like to reconfigure my kernel to remove support for multi-processor because this is causing problems with CPU scaling on my single processor system (Centrino M 750). Aside of this I want to undervolt my CPU to save some battery power. Normally this can be achieved by using a Vanilla kernel, patching it with the undervolting software (Linux PHC), configuring it and compile it. I've tried that and it works but I'd prefer use the kernel in Feisty Fawn (the one made by Ubuntu) because it contains some very interesting drivers such as Virtualbox stuff etc that are not present in the Vanilla kernels. Moreover I've seen that it is possible to use Linux PHC) as a loadable module instead of having to compile a new kernel but that would be good if I can patch my current kernel and recompile it too.

Is there a way I can reconfigure and patch my current Ubuntu Feisty kernel?? In which folder of /usr/src is the kernel??? There are 2 folders: linux-header-2.6.20-15 and linux-header-2.6.20-15-generic and I don't know which one I should point to to apply the patch.

Anyone knows?

Thanks

---

### Post by 5-HT on 2007-05-04
> Is there a way I can reconfigure and patch my current Ubuntu Feisty kernel?? In which folder of /usr/src is the kernel??? You can certainly reconfigure and patch the Feisty kernel. You'll first need to download the Ubuntu 2.6.20 kernel source though as it is not installed by default.
```
sudo apt-get source linux-source-2.6.20
```It will download to the current working directory, and you'll need to unpack it to /usr/src and then make a /usr/src/linux symlink pointing to the unpacked kernel source.

For reference on compiling kernels in Ubuntu: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---

### Post by kilou on 2007-05-04
Great, thanks! That'll probably be better than using a Vanilla kernel. However I wonder what will happen if a kernel update is available in the future through the update manager. What will happen if I run the update? Will it keep the settings I will set now or overwrite them with default?? What about the applied patches, will they still be available in the updated kernel or will I have to recompile everytime a kernel update is available (no big deal though)?

---

### Post by kilou on 2007-05-04
Also is it possible to apply the Con Kolivas patch to the Ubuntu kernel or is this patch only suitable for a Vanilla kernel?????

---

### Post by octoberdan on 2007-05-04
> **kilou said:**
> Also is it possible to apply the Con Kolivas patch to the Ubuntu kernel or is this patch only suitable for a Vanilla kernel?????

I believe it is possible. Give it a shot and let us know! As far as future upgrades are concerned, I believe the configuration will carry over.

You may also be interested in this: [http://linuxmonitor.net/blog/2007/03/ultimate-ubuntu-performance-tweaking.html](http://linuxmonitor.net/blog/2007/03/ultimate-ubuntu-performance-tweaking.html)

---

### Post by kilou on 2007-05-05
I'll try that Thanks! But it seems many people have trouble booting with the new kernel + patch although the compiling was done properly... I'll try anyway.

---

### Post by kilou on 2007-05-05
I tried to apply the patches to the Ubuntu kernel but it doesn't seem to work. Here is what I did:

&#65279;sudo su

rm -f /bin/sh
ln -s /bin/bash /bin/sh

aptitude install kernel-package libncurses5-dev fakeroot wget bzip2

cd /usr/src
sudo apt-get source linux-source-2.6.20 ###This also created a linux-source-2.6.20-2.6.20 directory in /usr/src

ln -s linux-source-2.6.20-2.6.20 linux
cd /usr/src/linux

#Patch Con Kolivas
wget [http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.20/2.6.20-ck1/patch-2.6.20-ck1.bz2](http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.20/2.6.20-ck1/patch-2.6.20-ck1.bz2)
bzcat patch-2.6.20-ck1.bz2 |patch -p1

When applying the patch some stuff work and some don't. I get some errors saying that some "hunks" failed :confused: I guess that CK patch is done for Vanilla only. Moreover the Linux PHC patch for undervolting is only available for Vanilla in 2.6.20. The last patch for a Ubuntu kernel was for 2.6.17. So probably I'll need to use a Vanilla kernel to apply those patches.

Now the obvious question: is it possible to apply Ubuntu patches to a Vanilla kernel to kind of rebuild a Feisty kernel from a Vanilla one???? I know Feisty kernel is 2.6.20-15 and the last 2.6.20 Vanilla kernel is 2.6.20.11......is that a problem??? Where can I downoad the specific Ubuntu patches if these exist?

Thanks

---


---
title: "Help Recompiling Kernel"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by Inhumane on 2007-02-05
I'm trying to follow this guide to recompile the current kernel into 2.6.20: [http://ubuntuforums.org/showthread.php?t=157560](http://ubuntuforums.org/showthread.php?t=157560)
I'm of course replacing the .16s with .20s, other than that I'm doing the same steps (except the patching step). I always get an error after trying to make the .deb file:
```
net/ipv4/ip_forward.c:123: internal compiler error: in pop_scope, at c-decl.c:855
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.1/README.Bugs>.
The bug is not reproducible, so it is likely a hardware or OS problem.
make[3]: *** [net/ipv4/ip_forward.o] Error 1
make[2]: *** [net/ipv4] Error 2
make[1]: *** [net] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.20'
make: *** [debian/stamp-build-kernel] Error 2

```
It seems to give me that error at a random step, because it wasn't ipv4 the last two times I tried doing it, it was two other different things.... I really don't understand what's going on and I REALLY want to recompile my own kernel, so please try to help !

---

### Post by Inhumane on 2007-02-05
Bump

---

### Post by jvc26 on 2007-02-05
As the instructions are for the 2.6.16 kernel the method may have changed slightly. How much different is the link posted below in comparison with the one you're following, if its really different you may need to change your method.
[http://www.ubuntuforums.org/showthread.php?t=311158](http://www.ubuntuforums.org/showthread.php?t=311158)
Il

---

### Post by Inhumane on 2007-02-05
I followed the guide and it compiled just fine, though now I have a new problem: After I try to boot into the Kernel, it goes into the loading bar screen, but gets stuck there without moving. I went into recovery mode kernel for 2.6.20 and it gets stuck after it's loading my mouse and keyboard USB ports.... Any solution to this? #-o

---

### Post by Inhumane on 2007-02-05
Shameless Bump

After letting it sit for a few min on the loading screen, it comes up with this error:
[BusyBox] "sh: can't access tty; job control turned off"
And below that pops [COLOR="Red"]Ininitramfs[/COLOR] command line

---

### Post by Inhumane on 2007-02-06
:(

---

### Post by sibrand on 2007-02-07
I've just tried to compile the 2.6.20... and I've got the same problem (loading bar won't change, followed by an error).

I really don't know what's wrong; I just copied the settings from my current kernel.  :confused:

---

### Post by sibrand on 2007-02-08
Hmm, I've checked the whole xconfig-thingie and apparently the SATA/PATA-drivers were not selected (Nvidia for me). 
Perhaps the same thing happened to you ?

---

### Post by Inhumane on 2007-02-08
> **sibrand said:**
> Hmm, I've checked the whole xconfig-thingie and apparently the SATA/PATA-drivers were not selected (Nvidia for me). 
Perhaps the same thing happened to you ?

Actually, in that guide posted by the second poster in this thread, there's a troubleshooting section it mentions something about the SATA drivers and how it hangs if you don't install them, so I selected the SATA things during the configuration process, and it didn't help. But that is probably our problem. What do you think we could do?

---

### Post by Inhumane on 2007-02-08
> **sibrand said:**
> Hmm, I've checked the whole xconfig-thingie and apparently the SATA/PATA-drivers were not selected (Nvidia for me). 
Perhaps the same thing happened to you ?

OK, recompiled with extra nVidia SATA/PATA options alongside other possibly relevant SATA options, and still no go.

---

### Post by Inhumane on 2007-02-09
> **sibrand said:**
> Hmm, I've checked the whole xconfig-thingie and apparently the SATA/PATA-drivers were not selected (Nvidia for me). 
Perhaps the same thing happened to you ?

Can you tell me which SATA options you exactly enabled? If it did fix your problem..

---

### Post by mr.v. on 2007-02-09
I'm using 2.6.20 but I sure didn't do it like that link posted did--

I've mostly used slackware before so I'm not saying this is the prettiest method but it will absolutely work. This is for building 32-bit kernel...things should be similar for 64-bit but since I don't have a 64-bit processor I haven't had the issue yet =) 

The first thing that is a bit funky with that guys instructions is importing your previous .config from an older kernel version. I've never done this and I have ALWAYS generated a new config file for each kernel from menuconfig. That's not to say that it won't work...i'm just not sure how stable they keep the config settings from kernel to kernel. The only time I use old settings is with the same kernel if I missed an option or something.

Anyway, my method is more manual than his. The first thing I did was go into synaptic and lock the current kernel version installed so it wouldn't automatically update kernels and mess up my menu.lst.

You obviously will need the development packages for this to work (binutils, gcc, glibc, make, etc).

Then I downloaded linux-2.6.20.tar.bz2 from kernel.org into /usr/src
**tar xjf linux-2.6.20.tar.bz2** unpacks the files into /usr/src/linux-2.6.20
switch to root (or do everything that follows with sudo commands)
now update the /usr/src/linux symlink to /usr/src/linux-2.6.20.
**rm /usr/src/linux**
**ln -s /usr/src/linux-2.6.20 /usr/src/linux**

now return the kernel to the base state with make mrproper
**make mrproper**
and then it's time to configure:
**make menuconfig**
*NOTE* for menuconfig to work you need the libncurses5-dev package (so that it can make the menu program)
Here's the ugly part...going through each option and selecting what you want and don't want. Ouput from lspci to identify hardware, the help files, documentation, and questions on forums as to what you should add will help you get through it. Once you learn everything, configuring takes much less time and you end up with a smaller, faster kernel.

Once you've done selecting everything you desire, save your config and exit.
Now just type
**make bzImage**
**make modules**
**make modules_install**
this will take a while. Once all are done you're ready to copy your bzImage to /boot
**cp /usr/src/linux-2.6.20/arch/i386/boot/bzImage /boot/vmlinuz-2.6.20-custom**
and the System.map
**cp /usr/src/linux-2.6.20/System.map /boot/System.map-2.6.20-custom**

now to your /boot/grub/menu.lst add the following entry:```

title		Ubuntu, kernel 2.6.20-custom
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.20-custom root=/dev/hda1 ro vga=773 quiet splash
boot
```

#NOTE the root (hd0,0) entry NEEDS TO REFLECT WHERE YOUR UBUNTU PARTITION IS...MINE IS hd0,0 YOURS MAY/WILL BE DIFFERENT. same with root=/dev/hda1. Look at your other entries in menu.lst to see what these values should be. Also I included a framebuffer console support in my kernel. If you don't want this or it complains about an unidentified video mode, don't add vga=773.

Also this kills the pretty ubuntu startup graphic but boots like 500x faster =). I'm working on how to get it back. It may be some custom kernel mod or depend on a specific setting in the kernel that I don't generally include. If anyone knows, let me know too =)

Anyway, everything works great and I have no complaints other than the death of the startup graphic.

---

### Post by Inhumane on 2007-02-09
> **mr.v. said:**
> I'm using 2.6.20 but I sure didn't do it like that link posted did--

I've mostly used slackware before so I'm not saying this is the prettiest method but it will absolutely work. This is for building 32-bit kernel...things should be similar for 64-bit but since I don't have a 64-bit processor I haven't had the issue yet =) 

The first thing that is a bit funky with that guys instructions is importing your previous .config from an older kernel version. I've never done this and I have ALWAYS generated a new config file for each kernel from menuconfig. That's not to say that it won't work...i'm just not sure how stable they keep the config settings from kernel to kernel. The only time I use old settings is with the same kernel if I missed an option or something.

Anyway, my method is more manual than his. The first thing I did was go into synaptic and lock the current kernel version installed so it wouldn't automatically update kernels and mess up my menu.lst.

You obviously will need the development packages for this to work (binutils, gcc, glibc, make, etc).

Then I downloaded linux-2.6.20.tar.bz2 from kernel.org into /usr/src
**tar xjf linux-2.6.20.tar.bz2** unpacks the files into /usr/src/linux-2.6.20
switch to root (or do everything that follows with sudo commands)
now update the /usr/src/linux symlink to /usr/src/linux-2.6.20.
**rm /usr/src/linux**
**ln -s /usr/src/linux-2.6.20 /usr/src/linux**

now return the kernel to the base state with make mrproper
**make mrproper**
and then it's time to configure:
**make menuconfig**
*NOTE* for menuconfig to work you need the libncurses5-dev package (so that it can make the menu program)
Here's the ugly part...going through each option and selecting what you want and don't want. Ouput from lspci to identify hardware, the help files, documentation, and questions on forums as to what you should add will help you get through it. Once you learn everything, configuring takes much less time and you end up with a smaller, faster kernel.

Once you've done selecting everything you desire, save your config and exit.
Now just type
**make bzImage**
**make modules**
**make modules_install**
this will take a while. Once all are done you're ready to copy your bzImage to /boot
**cp /usr/src/linux-2.6.20/arch/i386/boot/bzImage /boot/vmlinuz-2.6.20-custom**
and the System.map
**cp /usr/src/linux-2.6.20/System.map /boot/System.map-2.6.20-custom**

now to your /boot/grub/menu.lst add the following entry:```

title		Ubuntu, kernel 2.6.20-custom
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.20-custom root=/dev/hda1 ro vga=773 quiet splash
boot
```

#NOTE the root (hd0,0) entry NEEDS TO REFLECT WHERE YOUR UBUNTU PARTITION IS...MINE IS hd0,0 YOURS MAY/WILL BE DIFFERENT. same with root=/dev/hda1. Look at your other entries in menu.lst to see what these values should be. Also I included a framebuffer console support in my kernel. If you don't want this or it complains about an unidentified video mode, don't add vga=773.

Also this kills the pretty ubuntu startup graphic but boots like 500x faster =). I'm working on how to get it back. It may be some custom kernel mod or depend on a specific setting in the kernel that I don't generally include. If anyone knows, let me know too =)

Anyway, everything works great and I have no complaints other than the death of the startup graphic.
I just tried it. When I attempt to boot I get an error mentioning how it can't access root on VFS or something (but I disabled a BUNCH more things than in my previous config, so it is probably the cause, but I don't want to do it all over again. 
Your method is almost similar to the other guide, just a bit more complex, I think. 
To enable your logo, I think you can go to Graphics Support --->Logo configuration ----> enable bootup logo and the stuff under it.


I would also appreciate if the person who commented about the SATA would reply again =/

---

### Post by mr.v. on 2007-02-09
> **Inhumane said:**
> I just tried it. When I attempt to boot I get an error mentioning how it can't access root on VFS or something (but I disabled a BUNCH more things than in my previous config, so it is probably the cause...

```
sudo cp /boot/config-`uname -r` .config && sudo make oldconfig && sudo make menuconfig
```
after you do this step from the other guy's method...can you attach your .config file in the /usr/src/linux-2.6.20 directory? that may help us figure out what you did that caused it to pause. Also post the results of **lspci** on your computer...we may be able to figure out what the problem was with your kernel config.

> but I don't want to do it all over again.
errr...I don't know what to say... compiling a kernel with all your settings just right is tough. I'm sure there are those among us who never have a problem and were compiling kernels out of the womb...for the rest of us it take a bit of patience and trial and error. But after the steep learning curve...it gets much easier after that.

> To enable your logo, I think you can go to Graphics Support --->Logo configuration ----> enable bootup logo and the stuff under it. that gives you a penguin on your framebuffer console but not the ubuntu splash screen with the loading bar. I think it must be one of the kernel patches.

---

### Post by Inhumane on 2007-02-09
> **mr.v. said:**
> ```
sudo cp /boot/config-`uname -r` .config && sudo make oldconfig && sudo make menuconfig
```
after you do this step from the other guy's method...can you attach your .config file in the /usr/src/linux-2.6.20 directory? that may help us figure out what you did that caused it to pause. Also post the results of **lspci** on your computer...we may be able to figure out what the problem was with your kernel config.


errr...I don't know what to say... compiling a kernel with all your settings just right is tough. I'm sure there are those among us who never have a problem and were compiling kernels out of the womb...for the rest of us it take a bit of patience and trial and error. But after the steep learning curve...it gets much easier after that.

 that gives you a penguin on your framebuffer console but not the ubuntu splash screen with the loading bar. I think it must be one of the kernel patches.

Well :D I got it rolling! I still used the previous tutorial, only this time I enabled a bunch more ATA settings. Though it still hangs at the loading bar now and then (1 out of 5 boots or so, so far)
I also still have the loading bar. That is weird that you don't have it.

---

### Post by sibrand on 2007-02-11
> **Inhumane said:**
> Can you tell me which SATA options you exactly enabled? If it did fix your problem..I only checked the nvidia drivers (and somewhere else I've unchecked some ATA drivers because they were deprecated). 

I've got a MSI K8N Neo4-FI btw. ;)

---

### Post by Inhumane on 2007-02-11
> **sibrand said:**
> I only checked the nvidia drivers (and somewhere else I've unchecked some ATA drivers because they were deprecated). 

I've got a MSI K8N Neo4-FI btw. ;)

Since you're back here, I have another question for you.

Even after I personally enabled all those SATA drives, 60 or so percent of the time it would still get stuck at the loading bar, so it obviously was not a SATA problem. I need to restart my computer 3 times every couple of reboots for it to finish loading. 

I don't suppose this is happening to you too, right?

---

### Post by sibrand on 2007-02-11
> **Inhumane said:**
> Since you're back here, I have another question for you.

Even after I personally enabled all those SATA drives, 60 or so percent of the time it would still get stuck at the loading bar, so it obviously was not a SATA problem. I need to restart my computer 3 times every couple of reboots for it to finish loading. 

I don't suppose this is happening to you too, right?No, I don't have that problem.

And I'm not a Linux-expert, so honestly... I don't know what the solution for your problem could be. :-|

---

### Post by zaazu48 on 2007-02-13
I am having problem with my HP 500 touch pad... they said the kernel is malfunctioning and i need to install a patch..... how can I go about it.....

[http://ubuntuforums.org/showthread.php?p=2150551#post2150551](http://ubuntuforums.org/showthread.php?p=2150551#post2150551)

---


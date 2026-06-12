---
title: "Best Virtual machine"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by jazzman84116 on 2007-05-29
What is the best Virtual machine  to use and how do you install it?

---

### Post by lreyes6 on 2007-05-29
i use InnoTek Virtual box... you can search it on synaptics or aptitude :D

---

### Post by lazyart on 2007-05-29
Search the forums for VirtualBox and VMware.  It's a pretty animated discussion and no one really wins.

Both are free, VMware is in the repos, Virtual box is at [www.virtualbox.org]("www.virtualbox.org").

---

### Post by Psicolonia on 2007-05-29
virtual box is my opinion also. i've tried plenty!!! and virtual box is currently winning. FOR ME OF COURSE! please don't bug me with my opinion! ;)

---

### Post by mijj on 2007-05-29
I was settled into VirtualBox ...

... until ... after the kernel update, I got an error message from VirtualBox mentioning the UUIDs for the virtual machines - i dont have a clue how to get the winXP virtual os going again.

So .. I'm afraid of trusting VirtualBox .. i guess i have shuffle over to the VMware camp.

:(

---

### Post by bodhi.zazen on 2007-05-29
> **mijj said:**
> I was settled into VirtualBox ...

... until ... after the kernel update, I got an error message from VirtualBox mentioning the UUIDs for the virtual machines - i dont have a clue how to get the winXP virtual os going again.

So .. I'm afraid of trusting VirtualBox .. i guess i have shuffle over to the VMware camp.

:(

:lolflag:

[http://doc.gwos.org/index.php/VirtualBox#Kernel_Updates](http://doc.gwos.org/index.php/VirtualBox#Kernel_Updates)

If that does not fix the problem, describe it better ....



VirtualBox is great and IMO the place to start if you are new to virtualization. They have a nice GUI and it is easy to start. Virtualbox is based on qemu.

qemu is also very nice. Install kqemu as well to enhance speed. The gui tool is powerful, but it is easier to understand (for me) after you use the command to start qemu for a while. qemu is the only fully open source option.

VMWare is for "industrial" needs. The player and server are fun to play with though.

---

### Post by GrueTamer on 2007-05-29
I prefer qemu, but virtualbox is nice.  But qemu is just really nice, because I can run it with simple terminal commands instead of with a gui icon, and even if it looks like it would be hard to set up, it's not.  But if you're a gui person, go with virtualbox...unless you want to use qemu.  Note: I've never messed with kqemu before, so I can't say anything about it.

---

### Post by bodhi.zazen on 2007-05-29
kqemu will make qemu run faster. I would not run qemu without it.

Try it, I'll bet you will like it very much.

kqemu is now in the repos (you used to have to compile it)

:lolflag:

VirtualBox has a gui, but you have several options of running from the CLI, including running headless, which is very cool. You do not see the machine until you ssh -X into it (or if it is a windows guest rdp). The headless server is available to your entire network. These features are not on the GUI.

If fact, as with most things, you can not access all of the features from the gui.

---

### Post by hoheszeh on 2007-05-30
> **jazzman84116 said:**
> What is the best Virtual machine  to use and how do you install it?

For me it is Virtualbox because you can share a folder between a Linux/Ubuntu host and a Windows XP guest without problems and without a running network connection.

---

### Post by mijj on 2007-05-31
i'll mention this in case someone may find it of interest or use:

i sorted out (sidestepped) my weird virtualBox problem. 

the problem was: I restored a three day old backup of my Kubuntu partition and my virtualbox XP  wouldnt start - it complained about UUIDs in the virtualbox xml.  - i dont know if this is relevant - but .. in this case, the most recent virtualbox XP snapshot was more recent than the restored Kubuntu partition.

The reason i had to fall back to a backed up Kubuntu is the kernel update.   The update messed up the menu.lst with a uuid that didnt correspond to my Kubuntu partition so it just hung on boot up.

Fortunately, i'd saved the kernel updated Kubuntu that hung on boot up. ... after discovering that virtualbox woudnt work with the restored 3day old partition, i thought i'd have a shot at getting the updated Kubuntu working. 

After restoring the unbootable ext3 Kubuntu partition and using a grub boot disk that went to teh grub command line instead of menu.lst, i managed to boot into the updated Kubuntu (using paths instead of UUID) and fix the menu.lst with the proper UUIDs for the partition (from an old backed up menu.lst).  -- I'm a noob - this took me aaaaaaaaages of blood, toil, sweat and tears.  - does this kinda thing happen each time there's an update to the kernel?

anyhoo - when i managed to get back in to the updated linux, virtualbox behaved as expected (no errors mentioning uuids - just the vbox mentioned kernel fix that worked without fuss) and now it's up and running ok.

however .. the disturbing thing is ... the virtualbox in the older restored partition didn;t work.  Maybe VirtualBox reinstalled from scratch may have worked - i dunno.

p.s.  ... i couldnt fix the messed up menu.lst for the non-booting Kubuntu from windows using ext2ifs in windows cos kernel updated Kubuntu failed to shut down properly so the journaling was messed up .. so the drive was not visible to ext2ifs in windows.

---

### Post by Cyvros on 2007-05-31
I'd go for VirtualBox (open-source and it has some interesting features coming up), but VMware has support for 64-bit guests, which VirtualBox lacks. I'm fairly sure QEMU does have support for 64-bit guests, though - QEMU's good because it's portable, easy-to-use cross-platform (no installation) and fairly easy to configure. I find it's better for smaller OSes (Kqemu works wonders, though).

---

### Post by GabrielDunn on 2007-05-31
I like vmware workstation.  They have a lot of free 'appliances' you can download and I especially like the ubuntu stripped down for secure browsing.  It's a real life saver when you're doing shady surfing.  I even use it on my xp box too.

---

### Post by starfry on 2007-07-16
what's the command for installing kqemu from the repos without compiling please (I'm on Feisty) ?

---

### Post by bodhi.zazen on 2007-07-16
sudo apt-get install kqemu

---

### Post by starfry on 2007-07-16
Thanks, I tried that before without luck...

```
jl-dual% sudo apt-get install kqemu
Reading package lists... Done
Building dependency tree        
Reading state information... Done
E: Couldn't find package kqemu
jl-dual% 
```

I guess I need something else in my sources.list? What an I missing?

Thanks!

---

### Post by Eddi3 on 2007-07-23
I found that installing that package didn't work. I followed this HowTo:

[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

Althought the howto revolves around getting Windows to run under Qemu, it also covers getting kqemu working in detail.

---


---
title: "ubuntu in win xp"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by kevmore on 2007-05-29
Is it possible to install Ubuntu in win xp so that It is not a dual boot system?  I want to run Ubuntu in a windows window.  Or is it better to run windows in an Ubuntu window?  I am a total newbie to linux, but I have quite a bit of experience with dos/win 3.1/win 95/win 98/win 2000/ME/XP .  I did search for this, but with the rapid response time I thought somebody could straighten me out quicker.

Thanks

---

### Post by sankarv on 2007-05-29
There are emulators which can run any OSes inside other OSes. Some of them are VMWare, Bochs, QEMU, etc.  The ISO image of the Ubuntu needs to be present in your machine and u can configure any of these emulators to run Ubuntu inside windows. You can refer the help given in the respective emulator sites. VMWare is not freeware i suppose. I am not sure if you can install the OS in it.

---

### Post by Inxsible on 2007-05-29
Why do you want to run Ubuntu in a windows environment and make is susceptible to Windows viruses ??

---

### Post by irish_flu on 2007-05-29
If you want to run Ubuntu (or any Linux flavor, or even another Windows install) in a window withing Windows, check out VMWare:
[http://www.vmware.com](http://www.vmware.com)

get the free (as in beer, not as in open source) "VMWare Server".  Then, you'll be able to install an OS as a Virtual Machine and have it live right inside Windows.

You can also get "Virtual appliances", which are pre-built virtual machines, and download them (yeah, there's one with Ubuntu) from VMWare's "VMTN" site:
[http://www.vmware.com/vmtn/](http://www.vmware.com/vmtn/)

---

### Post by irish_flu on 2007-05-29
> **Inxsible said:**
> Why do you want to run Ubuntu in a windows environment and make is susceptible to Windows viruses ??

Hey man, to each his own.  His Ubuntu VM still won't get viruses (then again, neither does my Windows box)....

---

### Post by SoulinEther on 2007-05-29
The better option IMO would be to run a really lightweight Ubuntu running something like Fluxbox or IceWM with a virtual Windows. But that's just me.

---

### Post by sankarv on 2007-05-29
then u can try the light weight Fluxubuntu. Search for more details. It is not as latest as ubuntu i suppose. Xubuntu is lighter than ubuntu/ kubuntu.

---

### Post by SoulinEther on 2007-05-29
Suggested the option because I just read this, hehe. 8) [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by sankarv on 2007-05-29
looks good. there are more than one options for light weight scenario.

---

### Post by Cyvros on 2007-05-29
There is an alternative not addressed above, [AndLinux](http://wiki.gp2x.org/wiki/AndLinux) - it's built on CoLinux and basically allows you to run virtualised Ubuntu windows, apps, etc. (it mainly uses Xfce because it's far lighter) directly in Windows. Currently, it only really supports XP and is in beta, but it's one of the options.

It's sort of similar to Parallels' Coherence feature.

Another one to look out for is [LINA](http://www.openlina.com/), which is rather similar - run Linux apps in Windows or OSX.

But the safest option would still probably be a virtual machine. I'd recommend going for [VirtualBox](http://virtualbox.org) if you want (free speech and/or beer) free, but VMware's still probably the top free beer option at the moment.

A 'Coherence'-like feature is being planned for VirtualBox in the near future, so my absolute advice would be to go for VirtualBox.

It's, er... good for your health (and cross-platform, so you can keep your VM if you ever switch OSes).

But, and here comes more useless advice, you might want to wait until the next version of VirtualBox, as you'll be able to use VMware images and disks for it (currently it uses a different virtual machine format).

---

### Post by kevmore on 2007-06-18
After I made a backup image of my windoze machine, I did a complete ubuntu install.  I like it.  I have seen the light.

Later folks. Thanks for the help and encouragement

---


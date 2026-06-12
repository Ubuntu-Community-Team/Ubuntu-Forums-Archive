---
title: "Linux on Mac Intel?what about it?"
date: 2007-08-25
forum: Apple Intel Users
---

### Post by ivelasco on 2007-08-25
Hello

First, excuse for my poor english.

The question is that I have an ppc powerbook,but as my favorite SO is linux,that architecture has been a frustration for me,because of the linux limitations on it
 Now, I have to buy a new notebook an I am thinking about this 15" macbook pro:

    * 2.2GHz Intel Core 2 Duo
    * 1440 x 900 resolution
    * 2GB memory
    * 120GB hard drive1
    * 8x double-layer SuperDrive
    * NVIDIA GeForce 8600M GT graphics with 128MB SDRAM

I have two questions:

- First: it is ubuntu linux the SAME ubuntu linux that you can run in a standard x86 pc?I know that the instalation process is not the same,but I want to know if the apps,java,flash,win32 codecs,beryl,wifi etc run normally.There is any limitation?

So it is recomendable to buy this notebook for to use almost only with ubuntu?I love this hard and its quality

- About the hardware compatibility.What about the drivers?Airpot,Nvidia,tv-out,dual monitors,power management,special keys etc...

I would apreciate any help.

Thanks in advane

---

### Post by Greywhind on 2007-08-25
1. Ubuntu is the same on any Intel Mac as on a standard x86 machine (you use the same installation CD, and really, the installation process is nearly the same).

2. I haven't looked up all the hardware on the newest MacBook Pro, since I don't have one, but I know the NVidia graphics card works well (better than ATI, certainly), Airport should work with a little effort unless things have changed drastically since the last version of the MacBook Pro. I'm not sure about power management... I know it's not working on my Intel iMac (though I hear I could fix it by using the Gutsy kernel), but you can search for other threads on this forum to find out.

Really, most problems you might initially have with hardware/drivers are usually fixable.  It is a good idea to research the hardware beforehand, though.

---

### Post by black_raven2525 on 2007-08-25
I have the 15" MBP setup in a triple boot to XP, OS X, and Kubuntu.  Ive got all the hardware working fairly easily except power management and for some reason the mad wifi drivers don't work after I installed the Nvidia binary blob.  Integrated Ethernet works out of the box, but everything else needs to be tweaked before it preforms to exceptable standards.  All our information on howto install is located in [this]("http://ubuntuforums.org/showthread.php?t=474144&page=1") thread and should help you decide whether or not all the work is worth all the extra work.  Not saying you shouldn't get the MBP, but another options is the always wonderful Thinkpad T series.  Ive ready some pretty good reviews for the T61 and even though it might not have quite as much punch but the are sturdy and durable.

---

### Post by cyberdork33 on 2007-08-25
Honestly, if you want a linux-only machine, you might be better off getting something with a bit more fully linux-compatible hardware in it, like the new Dell laptops, or something from system76.

---

### Post by Viro on 2007-08-28
This might sound stupid, but if you're really interested in running Linux on your laptop and don't need all the bells and whistles of the latest 3D graphics card, get the Macbook not the Macbook Pro. 

Intel has done a tremendous job of supporting open source. As a result, the intel graphics chips are very very well supported under Linux and you don't even need to install a binary driver like nVidia or ATI. This has advantages, for example where the driver won't break if you upgrade your kernel.

Of course, the 3D performance isn't that great but I'm still able to play WOW and Dawn of War with good settings on my Macbook, so it can't be that bad :)

---

### Post by daveadams on 2007-08-28
Does the newest Macbook work as smoothly with Ubuntu as the first generation?

---

### Post by cyberdork33 on 2007-08-28
> **daveadams said:**
> Does the newest Macbook work as smoothly with Ubuntu as the first generation?
I think there are differences with the WiFi...

---

### Post by Viro on 2007-08-29
The current Macbooks use a newer wireless chipset, which require a newer version of the madwifi drivers than what Ubuntu ships with.

While this is a problem with Ubuntu 7.04, it should no longer be an issue with 7.10.

---

### Post by ivesjd on 2007-08-29
I triple boot on my MacBook. Ubuntu runs much better then windows. I have compiz fusion setup and it looks pretty good. In OS X I played WoW for abit and it runs great. But I get a flicker in windows, its almost like the desktop is refreshing wrong. Oh well, I never really use windows anyway. That said, I would recommend something else to run Ubuntu alone on. There are some things like lack of a right click button (I have the right Cmd button mapped to it) that just start to get old after awhile.

---

### Post by guidop on 2007-08-30
I have Kubuntu 7.04 installed on an Oct 2006 release 2.33 GHz ATI Graphics Macbook Pro.

The default installed synaptics trackpad driver mapped a 2 finger tap to a middle click (mouse button 3), and a three finger tap to a right click (mouse button 2).  A single tap mapped to the standard left click.  The right side of the trackpad acts as a scrollbar.

As far as I know, I didn't do anything to configure this behavior, a clean install of 7.04 had it set up automatically.  Other forum posts indicate that trackpad behavior can be configured to suit by editing the "Synaptics Touchpad" section of xorg.conf.

---

### Post by ronocdh on 2007-08-31
> **cyberdork33 said:**
> Honestly, if you want a linux-only machine, you might be better off getting something with a bit more fully linux-compatible hardware in it, like the new Dell laptops, or something from system76.
It's said a lot, but consider keeping a very small partition for OS X to live on in order to grab firmware updates and the like. This will of course carry over to your hardware when you use it in Linux, but the updates can only be obtained via OS X.

Also, regarding wireless performance, you could always fall back on ndiswrapper if the newest madwifi is giving you trouble. Please do try the madwifi drivers first, though! But remember that you'll need either a wired ethernet connection (or an OS X partition with working wireless) to grab the packages necessary to set up the wireless.

---


---
title: "Practice for my eventual Raspberry Pi"
date: 2013-02-17
forum: Any Other OS
---

### Post by motocollage on 2013-02-17
Hello All,

I'm currently running 12.04LTS on my older acer aspire D250 as a dual-boot with windows 7 starter. I love everything linux/open source! I'm an artist currently in my terminal (MFA) program, attempting to specialize in New Media and installation. Basically, any materials or technology I can get my hands on I want to turn into some sort of other-worldly thing.

So, not sure where to start, but I've only really asked for help on the forums for one major problem, and I was ASTOUNDED how awesome the community is. Another user jumped on my problem, and it was great being able to perform under the hood maintenance to my computer. This is my current goal:

I have this old desktop that is running Ubuntu/LXDE but it is SO SLOW. I am wondering if I try to use it as a primer for raspberry pi, wipe it clean, and start installing packages from scratch and really understanding how a system is built. I have been experimenting with analog electronics and arduino in the attempts to create work that is kinetic and sensor-based. I'll stick with that stuff for now, but I know that raspberry pi will open up even more doors for me. I was thinking Debian, but I might have to research a little more to see what the optimal rpi systems are.

I would like to find a basic use for the old desktop. (I also have an old compaq with no HD-I've played with running it off the live cd, but maybe I can just find a distro to install that will allow me to save to a thumbdrive. A Puppy maybe?).

Anyone interested in tackling any of these problems?

---

### Post by mbarland on 2013-02-17
Any distro will allow you to install to a usb drive, they show as /dev/hd(x) just like a SATA HDD during the install. So just install as normal to the USB drive.

Raspbian is the recommended and probably most popular of the Rpi distros, it is based on Debian. Ubuntu abandoned the version of Arm used by the Rpi's processor, so no *buntu distros on the pi. Ubuntu is based on Debian, so if you are familiar with Ubuntu, switching to Debian is pretty painless. Raspbian includes a full LXDE graphical environment and boots off an SD card, so it runs like a persistent live cd.

---

### Post by papibe on 2013-02-18
Hi motocollage.

Lubuntu (uses LXDE) is the version that take less resource of all the Ubuntu family.

There are alternative on other distros. One based on Ubuntu would be [Bodhi Linux]("http://www.bodhilinux.com/") (it uses the Enlightenment Desktop).

[Crunchbang]("http://crunchbang.org/") would be another alternative (uses OpenBox). Even though is not based directly on Ubuntu, it is based on Debian.

Another alternatives would be Damn Small Linux, Puppy Linux, SliTaz, and Tiny Core Linux (may be the ultimate light distro).

Now, you may attempt to accomplish the same goals as Bodhi and Crunchbang, by installing the Ubuntu command line minimal install (tutorial [here]("http://www.psychocats.net/ubuntu/minimal")), and then installing e16 (Enlightenment), or Openbox.

Finally, I would consider using it as a server (no GUI). There so much things you could do with it. For instance: file server (samba or nfs), DNS, DHCP, backup server, media repository, music streaming, etc.

I hope that helps. Tell us how it goes.
Regards.

---

### Post by ke4nt on 2013-02-18
> 
Another alternatives would be Damn Small Linux, Puppy Linux, SliTaz, and Tiny Core Linux (may be the ultimate light distro).


Note: TinyCoreLinux now has a new section for ARM processors,
for use in a variety of devices including RaspberryPi.

[http://www.tinycorelinux.net/arm.html](http://www.tinycorelinux.net/arm.html)

---

### Post by sanderj on 2013-02-18
An acer aspire D250 is a netbook with 1GB RAM, right?

If so, it's not very old, and you can run Lubuntu and Xubuntu on it. I've a Netbook and I even run Ubuntu 11.10 on it. As long as you have a swap space on your harddisc.

---

### Post by ridgeland on 2013-02-19
I'm having fun with my Raspberry PI and Arduino.  I use the RPI with VNC over SSH so I connect using my PC.  The RPI then doesn't need a keyboard or display. The RPI uses Raspbian with LXDE.  Arch is also available. AdaFruit made a disto too. I have the Raspberry PI using serial communication to the Arduino using a CD4050 chip.  So a chain of my PC to the RPI to the Arduino.  The RPI can host the Arduino IDE.

I have an old 1997 Pentium 5 PC that is 200MHz with 256MB of RAM.  It still works and uses Slitaz Linux.  Slitaz boots in 60 seconds, compared to all the other light distros I've found needing 5 minutes to boot.  The old PC serves no real purpose now, just a novelty.  It can surf the web though.  Slitaz's site:
[http://www.slitaz.org/en/](http://www.slitaz.org/en/)

---

### Post by tgalati4 on 2013-02-19
For art purposes, you will be informed by:

[http://processing.org/](http://processing.org/)

Use the raspberry pi or arduino to sense the world around you and display it with processing.

---

### Post by motocollage on 2013-02-20
Wow, a lot of great responses! Let me see if I can clarify/ask a few things. Let me apologize in advance for not QUOTING properly:

**_mbarland_**
So, could I theoretically boot up my old HD-less Compaq with a 10.04 live cd and do a minimal install, (or I have a crunchbang and macpup disk as well), then install to an 8gb flash drive? I just need a system that I can update to network, and maybe room for some arduino/processing files. For some reason, I had the impression that when the system boots, it won't know to look for the usb port. The BIOS doesn't allow it to boot from usb, just cd/dvd drive.

The old old desktop is a Lenovo. Should there be any problem installing Raspbian to the clunky Lenovo?

**_papibe_**
I think I'll try to emulate the Raspberry Pi on the Lenovo, but might try to follow the advice above to install Crunchbang or one of the other lightweight distros on my Compaq. I understand Crunchbang is not entirely stable....I'm assuming Damn Small LInux and Tiny Core linux can both install to a flash drive AND run LXDE if needed? (is it OpenBox that gives Crunchbang that nice, clean and minimal desktop? What are other distros that use OpenBox?)

I don't think I'll use it as a server at this point. I want to use these as minimal systems for one or more of the following: a) a simple media player for short video/animation that will be presented in a sculptural space, b) a system to run arduino/processing in said space, all in anticipation of using RaspPi for the same reasons. 

And thanks for UBUNTU minimal link!

**_ke4nt_**
TinyCoreLinux sounds like an option. I'll do a little research, but at my level, I think finding the 'most popular', hence larger user community distro for raspberry pi is my first step. So maybe you and mbarland can debate which distro is best for my needs.

**_sanderj_**
I like my netbook, but I got it around 2008/9. It runs Unity pretty well, but I'd like to keep LXDE as an alternative.

**_ridgeland_**
once I get a little more in depth, I may pick your brain. Your first paragraph went way over my head :) I'll have to check out slitaz thought

**_tgalati4_**
I have processing, but haven't spent much time with it. Trying to focus on Arduino-once I feel a bit better with it I'm sure the programming language will be more intuitive w/Processing. Do you happen to have any specific examples of using Processing to display Arduino outputs? I'm interested in having sculptural works that respond to sensors, but in what ways do you think I can 'actuate' some of the information/voltages in Processing?

THANKS ALL FOR THE ENTHUSIASTIC RESPONSES! I'll keep you posted. In the meantime, you can check out this rough cut of video documentation of a strictly electronic art:

[http://vimeo.com/59961514]("http://vimeo.com/59961514")

---

### Post by papibe on 2013-02-20
> **motocollage said:**
> I'm assuming Damn Small LInux and Tiny Core linux can both install to a flash drive...
Yes.

> **motocollage said:**
> ...AND run LXDE if needed?
I imagine you can, but some of those tiny distros work well because they use a custom combo of software. For instance Tinycore use BusyBox, and FLWM. Installing LXDE may decrease its performance a little bit.

> **motocollage said:**
> What are other distros that use OpenBox?
Most distributions have OpenBox as an optional package. Here's an incomplete [list]("http://openbox.org/wiki/Help:Distros_and_DEs_using_Openbox") of the ones that include it by default.

Regards.

---

### Post by kiyop on 2013-02-20
> **motocollage said:**
> So, could I theoretically boot up my old HD-less Compaq with a 10.04 live cd and do a minimal install, (or I have a crunchbang and macpup disk as well), then install to an 8gb flash drive? I just need a system that I can update to network, and maybe room for some arduino/processing files. For some reason, I had the impression that when the system boots, it won't know to look for the usb port. The BIOS doesn't allow it to boot from usb, just cd/dvd drive.
I could install debian squeeze onto 8GB USB flash by similar installation method as that to a partition on a HDD, and I have updated. So the debian installed onto the USB flash is up-to-date.
As for the BIOS which cannot enable boot from USB flash, you can use Super Grub2 disk, and so on. [My tool]("http://kiyoandkei.blog68.fc2.com/blog-entry-52.html") may help you.
To refuse bloat softwares, uncheck all at tasksel (package selection) during installation step of debian.

---

### Post by tgalati4 on 2013-02-20
A quick google search brings up several links including:

[http://www.youtube.com/watch?v=nr2tm0vpzB8](http://www.youtube.com/watch?v=nr2tm0vpzB8)

[http://dorkbyte.com/2010/05/19/two-projects-where-art-meets-arduino/](http://dorkbyte.com/2010/05/19/two-projects-where-art-meets-arduino/)

---

### Post by motocollage on 2013-02-27
> **kiyop said:**
> I could install debian squeeze onto 8GB USB flash by similar installation method as that to a partition on a HDD, and I have updated. So the debian installed onto the USB flash is up-to-date.
As for the BIOS which cannot enable boot from USB flash, you can use Super Grub2 disk, and so on. [My tool]("http://kiyoandkei.blog68.fc2.com/blog-entry-52.html") may help you.
To refuse bloat softwares, uncheck all at tasksel (package selection) during installation step of debian.

So, are you suggesting that once I install to the flash drive, my machine will not know to boot from it (just like I can't live boot from usb) unless I use Super Grub2 disk? I looked at the 'tool' you provided, but it is a little unclear for me what/how to use it.

AND, these are just questions for now regarding my Compaq (the one w/o HDD). Currently, I am working with installing Ubuntu Minimal to my Lenovo (old old desktop) and HPdv6000, so that is my primary focus.

---

### Post by kiyop on 2013-03-02
> **motocollage said:**
> So, are you suggesting that once I install to the flash drive, my machine will not know to boot from it (just like I can't live boot from usb) unless I use Super Grub2 disk?
Unless you use some kernel loaders on some bootable media such as CD/DVD, instead of USB.
You mentioned that your PC cannot boot from USB media, although I am not sure whether your PC can boot from USB media.
Such kernel loaders include Super Grub2 disk, Rescatux, RIP Linux, kexec-loader and my tool. You should write these kernel loaders onto CD/DVD. You can also use PLoP boot manager to chainload to USB media on PC the BIOS of which does not support boot from USB.

> **motocollage said:**
> I looked at the 'tool' you provided, but it is a little unclear for me what/how to use it.
First, you must boot with some debian (squeeze, version 6), either live debian [http://live.debian.net/](http://live.debian.net/) or installed debian.
Then, follow [http://kiyoandkei.blog68.fc2.com/blog-entry-52.html#generation](http://kiyoandkei.blog68.fc2.com/blog-entry-52.html#generation)

> **motocollage said:**
> AND, these are just questions for now regarding my Compaq (the one w/o HDD). Currently, I am working with installing Ubuntu Minimal to my Lenovo (old old desktop) and HPdv6000, so that is my primary focus.
I see. :)

---


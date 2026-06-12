---
title: "looking for a specific distro, any help?"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by benji.ijneb on 2008-03-15
i'm looking for a linux distro that will do all the following:

work well/fast on 128MB RAM
similar to windows
as powerful/user friendly/easy as ubuntu
can install easily to HD
can boot off of a USB stick - i have no cd drive on this PC.

the pc is an old dell lattitude L400

I know it's a lot to ask, but...

---

### Post by Cresho on 2008-03-15
try damnsmalllinux

[http://damnsmalllinux.org/](http://damnsmalllinux.org/)

50mb BIG! Last time i used it, i was saving stuff on the usb flash drive.   The laptop was an old compaq, 64mb memory, no hardrive 300mhz Intel pentium2.  It ran so fast, i thought it was a new laptop.  I'm not kidding.

---

### Post by wjp.reg on 2008-03-15
> **benji.ijneb said:**
> i'm looking for a linux distro that will do all the following:

work well/fast on 128MB RAM
similar to windows
as powerful/user friendly/easy as ubuntu
can install easily to HD
can boot off of a USB stick - i have no cd drive on this PC.

the pc is an old dell lattitude L400

I know it's a lot to ask, but...

check this out for installation on USB and suggested distros

[http://www.pendrivelinux.com/]("http://www.pendrivelinux.com/")

DSL is pretty good

---

### Post by ugm6hr on 2008-03-15
PuppyLinux is a good choice, and perhaps a little friendlier than DSL:
[http://www.puppylinux.org](http://www.puppylinux.org)

But DSL is a good choice as previously mentioned.

---

### Post by benji.ijneb on 2008-03-15
> **Cresho said:**
> try damnsmalllinux

[http://damnsmalllinux.org/](http://damnsmalllinux.org/)

50mb BIG

Last time i used it, i was saving stuff on the usb flash drive.   The laptop was an old compaq, 64mb memory, no hardrive 300mhz Intel pentium2

thanks, i've tried it and i hated it. sorry!

---

### Post by Iowan on 2008-03-15
[Puppy]("http://www.puppylinux.com/") seems popular.

---

### Post by MONODA on 2008-03-15
puppy linux is exactly what you asked for.

---

### Post by jprophet420 on 2008-03-15
I have never used any of the distros mentioned but I used [slax popcorn]("http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/SLAX-Popcorn-Edition-2255.shtml") in a similar situation. It did a spectacular job on an older PC I was using with only 128mb of ram. I found this info on how to make it bootable:

Download the "syslinux" package (syslinux-xy.tar.gz) from the website [www.kernel.org](www.kernel.org) - we need it later on. 

1. Boot SLAX from CD with inserted usb stick. 
2. Prepair the stick for your wishes (1 or 2 partitions) - I made a 128 MB primary FAT16 partition for SLAX (modified) and took the rest for a logical drive on a extended partition, also FAT16. This you can already do out of MS Windows before you boot SLAX or out of running SLAX with "cfdisk /dev/sda" and after reboot with "mkdosfs /dev/sda1" "mkdosfs /dev/sdaxy" and so on. 
3. Mount the stick - can be that it is mounted already - and do: 
4. "cd /boot" 
5. "cp -ra * /where_your_stick_is_mounted" 
6. "cd /where_your_stick_is_mounted/boot" 
7. "cp vmlinuz /where_your_stick_is_mounted" 
8. "cp initrd.gz /where_your_stick_is_mounted" 
9. "cp isolinux.cfg /where_your_stick_is_mounted/syslinux.cfg" 
10. "cd .." 
11. "mcedit syslinux.cfg" 
12. Here you have to remove "/boot" from the expression "/boot/vmlinuz" and "/boot/initrd.gz" so that it is "vmlinuz" and "initrd.gz". Save the changes and close the file. 
13. Extract the package syslinux to /tmp: "cd /tmp" and "tar xzvf syslinux-xy.tar.gz". 
14. "cd syslinux*/unix" 
15. "syslinux -s /dev/sda1" 

Now you can reboot and SLAX will boot from usb stick. 

[Source]("http://www.linuxforums.org/forum/slackware-linux-help/33934-slax-popcorn-5-0-5-iso-image-usb.html")

---

### Post by ugm6hr on 2008-03-15
This has a good review of the main contenders: [http://www.informationweek.com/news/showArticle.jhtml?articleID=203100989&pgno=1&queryText=](http://www.informationweek.com/news/showArticle.jhtml?articleID=203100989&pgno=1&queryText=)

---

### Post by Cresho on 2008-03-15
> **benji.ijneb said:**
> thanks, i've tried it and i hated it. sorry!

please make sure you add in your description exactly what you want!

---

### Post by kerry_s on 2008-03-15
> **benji.ijneb said:**
> thanks, i've tried it and i hated it. sorry!


dsl's a good starting point. if your a little picky go custom. grab the debian net installer.
how to-> [http://www.debian.org/releases/stable/i386/ch04s04.html.en](http://www.debian.org/releases/stable/i386/ch04s04.html.en)
image-> [http://ftp.nl.debian.org/debian/dists/etch/main/installer-i386/current/images/hd-media/](http://ftp.nl.debian.org/debian/dists/etch/main/installer-i386/current/images/hd-media/)

then just grab only what you want.

i use a custom debian install almost like dsl, i use the same window manager "jwm" it is really light and very configurable, it's really under estimated, most people look at the stock jwm look and just don't like it, but they never think to change it. i talked robert into the toolbar icons, but it can do so much more. the looks is what you make it.

i start my build with->
apt-get install xorg synaptic jwm rox-filer leafpad

i don't use a login manager, i set up auto login and startx on my own.
here's what my start up looks like->
[http://video.google.com/videoplay?docid=3007650994959497284&hl=en](http://video.google.com/videoplay?docid=3007650994959497284&hl=en)

here's some pics, yes, i do most of the icons myself using the blanks.

---

### Post by ugm6hr on 2008-03-16
> **kerry_s said:**
> dsl's a good starting point. if your a little picky go custom. grab the debian net installer.

An Ubuntu custom install will probably run with 128MB too:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by kerry_s on 2008-03-16
> **ugm6hr said:**
> An Ubuntu custom install will probably run with 128MB too:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

that would work to, but debians better on the old stuff. also when your dealing with machines where you got to get complicated with the install you only want to do it once. ubuntu is a snap shot distro, debian is a rolling release, as long as you upgrade from time to time you always get newer packages than you can get with ubuntu.

---


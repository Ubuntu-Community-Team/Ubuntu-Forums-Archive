---
title: "Need Small PPC Linux"
date: 2007-06-14
forum: Apple PPC Users
---

### Post by Da Flo-rid-eee-an on 2007-06-14
I have a PowerBook 1400cs/166 with around 24-16Mb RAM and a 166Mhz 603 PPC processer

My problem is that I cannot find and micro linuxes for the PPC. I was wondering if anybody knew of any linuxes for my computers.

---

### Post by testube_babies on 2007-06-14
This will probably be a difficult undertaking, but here's a good place to start:
[http://www.eskimo.com/~pristine/unix.html](http://www.eskimo.com/~pristine/unix.html)

---

### Post by ccfjeff on 2007-06-14
> **Da Flo-rid-eee-an said:**
> I have a PowerBook 1400cs/166 with around 24-16Mb RAM and a 166Mhz 603 PPC processer

My problem is that I cannot find and micro linuxes for the PPC. I was wondering if anybody knew of any linuxes for my computers.

Two distros that seem to be tailor made for older computers:

Damn Small Linux  [www.damnsmalllinux.org/]("http://www.damnsmalllinux.org/")

and 

Puppy Linux:  [www.puppylinux.org/user/viewpage.php?page_id=1]("http://www.puppylinux.org/user/viewpage.php?page_id=1")

---

### Post by kerry_s on 2007-06-14
> **ccfjeff said:**
> Two distros that seem to be tailor made for older computers:

Damn Small Linux  [www.damnsmalllinux.org/]("http://www.damnsmalllinux.org/")

and 

Puppy Linux:  [www.puppylinux.org/user/viewpage.php?page_id=1]("http://www.puppylinux.org/user/viewpage.php?page_id=1")

I guessed you missed the ppc part, those are i386 only.

---

### Post by kerry_s on 2007-06-14
> **Da Flo-rid-eee-an said:**
> I have a PowerBook 1400cs/166 with around 24-16Mb RAM and a 166Mhz 603 PPC processer

My problem is that I cannot find and micro linuxes for the PPC. I was wondering if anybody knew of any linuxes for my computers.


Go debian, you can learn to do the custom install to build your very own small linux.

this is the net installer, you can install a base system-> [http://mirrors.kernel.org/debian-cd/current/powerpc/iso-cd/debian-40r0-powerpc-businesscard.iso](http://mirrors.kernel.org/debian-cd/current/powerpc/iso-cd/debian-40r0-powerpc-businesscard.iso)

install the base system, that means when it comes to the package selection uncheck all the packages(standard and desktop, i think)
after the reboot, there won't be a gui yet
login as root
apt-get install xorg gdm synaptic fluxbox emelfm leafpad dillo
reboot(ctrl+alt+delete)
select fluxbox from the session menu  <important
login
open synaptic and get what ever else you want,
emelfm is a filemanager
leafpad is a text editor
dillo is a small web browser

---

### Post by John.Michael.Kane on 2007-06-14
[Yellow Dog Linux]("http://www.terrasoftsolutions.com/resources/ftp_mirrors.shtml")

[TA-Linux]("http://talinux.tal.org/")

Or you can try kerry_s method.

---

### Post by Da Flo-rid-eee-an on 2007-06-17
i put the cd in the drive but when i reboot it still comes up as mac 8. is there a button i have to press?

thanks-me

---

### Post by John.Michael.Kane on 2007-06-17
> **Da Flo-rid-eee-an said:**
> i put the cd in the drive but when i reboot it still comes up as mac 8. is there a button i have to press?

thanks-me

You can try holding down 'C' while booting, and it should  then boot from the CD.

For other info [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by ssam on 2007-06-17
if you know linux/unix will yo could try linux from scratch. [http://www.linuxfromscratch.org/lfs/](http://www.linuxfromscratch.org/lfs/)

you should probably contact them and ask how well it works for powerpc. it is even more source based than gentoo so processor architecture should not be an issue.

---

### Post by Da Flo-rid-eee-an on 2007-06-17
The "C" buton trick doesn't work. does killdisk work?

---

### Post by ssam on 2007-06-17
> **Da Flo-rid-eee-an said:**
> The "C" buton trick doesn't work. does killdisk work?

i think the ubuntu CDs can only boot on newworld mac. yours is definately oldworld

---

### Post by 3rdalbum on 2007-06-18
> **Da Flo-rid-eee-an said:**
> I have a PowerBook 1400cs/166 with around 24-16Mb RAM and a 166Mhz 603 PPC processer

My problem is that I cannot find and micro linuxes for the PPC. I was wondering if anybody knew of any linuxes for my computers.

Your best bet would be NetBSD. I think that's the only thing that will boot up with such low memory on a Mac. It's not exactly Linux, but it might be similar enough for what you need. Note that you are extremely unlikely to be able to get a graphical display, much less a desktop, with such low memory.

---

### Post by Da Flo-rid-eee-an on 2007-08-26
What if somebody modded Damn Small of Basic Linux so they ran on the PPC???

---

### Post by oswaldkelso on 2007-08-26
Hi I think you need bootx [http://penguinppc.org/bootloaders/bootx/]("http://penguinppc.org/bootloaders/bootx/")
from memorey on a similar mac 32mb 200mhz. avoid yellowdog I got it to install but it was painfully slow, minuets to open a window.
1. partition your mac with a mac install disk, making the mac partition as small as posible (200mb?) the rest as free space.
2 install bootx. bootx is a extention that lets you switch between mac os and linux.
3. I seem to remember down loading the linux kernel so bootx could select it but things are a bit foggy. Hopfully somone else can help here.
4 use debian 

5 just found this should help [http://www.stocksy.co.uk/articles/Linux/linux_on_an_oldworld_power_mac/](http://www.stocksy.co.uk/articles/Linux/linux_on_an_oldworld_power_mac/)[http://www.stocksy.co.uk/articles/Linux/linux_on_an_oldworld_power_mac/]("http://www.stocksy.co.uk/articles/Linux/linux_on_an_oldworld_power_mac/")

edit once you get debian up and running do what  Kerry_s said. good luck!!!

P.s you may want to use an older 2.4 kernel as it will make your machine faster than 2.6 at the expense of some features

---

### Post by Ptero-4 on 2007-09-09
Also, to add to kerry's advice. Use xdm instead of gdm. That will avoid the installation of the dependant gnome libraries and metacity WM.

---


---
title: "Installing Lilo to multi boot?"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by xahxhax on 2008-02-19
How can I install Lilo so that I can run XP and Ubuntu on two seperate hard drives?

Or better yet is there a way to add Ubuntu to boot.ini in XP?

---

### Post by Presto123 on 2008-02-19
Grub is the bootloader that is auto-installed with Ubuntu and will take care of this need. :)

Please see: [http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)

---

### Post by xahxhax on 2008-02-19
No offense, but GRUB is an unmitigated PoS that has given me nothing but problems and made the Ubuntu experience worse for the fact.  I happen to like leaving my external harddrive plugged in when I boot--unplugging it every time is a major nuisance--and if GRUB can't handle something so radical then it needs to die.

Somebody recommended Lilo as an alternative, but I have no idea how to set that up.

---

### Post by crf on 2008-02-19
grub manual. [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)
--

Lilo should be easy to set up though. You can get lilo and lilo-doc using synaptic, then read its documentation.
Try it :-)
If you make a bad mistake, you should be able to boot using your ubuntu cd anyway, to correct it.

--

Also you may look in your computer's bios. I think you may be able to set it so that it either looks first at the internal drive or the external usb drive to find one to boot off of.

---

### Post by xahxhax on 2008-02-19
I'll check on that, how do I boot Ubuntu sans boot loader though?

---

### Post by bodhi.zazen on 2008-02-19
> **xahxhax said:**
> No offense, but GRUB is an unmitigated PoS that has given me nothing but problems and made the Ubuntu experience worse for the fact.  I happen to like leaving my external harddrive plugged in when I boot--unplugging it every time is a major nuisance--and if GRUB can't handle something so radical then it needs to die.

Somebody recommended Lilo as an alternative, but I have no idea how to set that up.

For the record, if you go through the install process and accept the defaults GRUB works 99 % + of the time and if there is a problem please post and it can be easily fixed most of the time. Most of the problems, IMO, come when people try to change the defaults without reading the documentation, although there are exceptions.

FYI here is a how-to for GRUB :

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)


Lilo is a fine alternate, but configuring it for Ubuntu requires some additional configuration :
	
[http://www.bauer-power.net/2007/08/changing-from-grub-to-lilo-ubuntu-704.html](http://www.bauer-power.net/2007/08/changing-from-grub-to-lilo-ubuntu-704.html)

Hermanzone : [http://users.bigpond.net.au/hermanzone/p4.html](http://users.bigpond.net.au/hermanzone/p4.html)


If you prefer you can use the windows boot loader, although I do not know how to configure it.

---

### Post by andrew.46 on 2008-02-20
Hi,

 It is not exactly what you are after but my own setup may be start for you. I have lilo installed to the MBR running Slackware on hda1, Hardy Heron on hda2 and swap on hda3:
```
# LILO configuration file
# LILO global section
boot = /dev/hda
prompt
timeout = 300
vga = normal
lba32
# End LILO global section
# Linux bootable partition config begins
# Default boot is Slackware 12:
image = /boot/vmlinuz-generic-smp-2.6.21.5-smp
  initrd = /boot/initrd.gz
  root = /dev/hda1
  label = Slackware
  read-only 
# Hardy Heron
other=/dev/hda2
    label= Hardy
    table=/dev/hda
```

The 'other' section is lilo's version of chainloading. In this example Hardy Heron is installed to hda2 and I have *also* installed Grub to the hda2: (hd0,1) so when the Hardy Heron option is selected grub is loaded. (Watch the grub syntax carefully!!!) I imagine that Windows could be added in the same way but I have *not* used windows in this fashion.

Lilo for me is much more intuitive than Grub but the virtue of the above setup is that Grub takes care of the many kernel changes of ubuntu without having to rewrite lilo.conf all the time.

Perhaps you can use some of this?

      Andrew

---

### Post by jken146 on 2008-02-20
> **xahxhax said:**
> how do I boot Ubuntu sans boot loader though?

You don't.  You install GRUB on the same partition as Ubuntu's / instead of the MBR.  Then you can use your BIOS to choose which drive to boot from each time.

---


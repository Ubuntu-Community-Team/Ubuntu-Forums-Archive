---
title: "usb thumb drive xubuntu system"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by d3adp00l on 2008-04-06
I have read a lot of threads on this subject but they are all old, and outdated so I thought I would ask again.

Goal: To have xubuntu x64 Running and booting from an 8g thumb drive (corsair). 

Tried: Alot, but none worked except installing xub on the thumb and the boot loader on an hd. The whole point of this other than my own system, is for a second HOUSE computer for everyone else, no need for storage its just a net and word processor computer, having no hd means no one can drop a bunch of junk in it. 

Last attempt I had no hd on the system, I partitioned the thumb drive into two partitions one 3g and one 5g, they were mounted as / and /home, no swap(I have 2g of ram). The install went fine, but on boot it dies and errors. 

Has anyone got this working? If so how is the bootloader made to work, and yes you'll have to explain it to me like I am 2yrs old, small words, very slowly, and very descriptively.

---

### Post by Mark_in_Hollywood on 2008-04-06
see:

USB Ubuntu 7.10 Gutsy Gibbon install

[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

PLEASE let me know how this goes for you.

---

### Post by d3adp00l on 2008-04-06
well sad to say mark, but it didn't work, well not the first try at least. Given the fact that I don't know what most of the commands are doing after the partitioning, but after the reboot, this is what it said, :grub v 1.5
grub loading
error 17


any ideas?

---

### Post by myusername on 2008-04-06
well are you sure your system is capable of booting from usb?

you probably just need to edit your grub men.list (/boot/grub/menu.list) and make sure the linux part has the right drive

---

### Post by d3adp00l on 2008-04-07
So what use the terminal and type that in? Sorry but I don't know a whole lot, this is part of the learning curve, sure I can install Ub any idiot can, but to do this I have to actually learn what all the parts do. 

And yes it will boot from the thumb drive, not yet with Ub but it will.

---

### Post by Mark_in_Hollywood on 2008-04-09
Try here:

[http://www.gentoo.org/doc/en/grub-error-guide.xml](http://www.gentoo.org/doc/en/grub-error-guide.xml)

get back to me.

---


---
title: "SATA Disks and Ubuntu"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by jethro10 on 2006-08-15
Hi,
I've been sent a Serial ATA disk in error. Rather than returning it for and IDE I was gonna install it as my only disk.
I see from the forums it seems to be a bit patchy.

Are there any issues i'm likely to come across before I start.


J

---

### Post by anaconda on 2006-08-15
I have a SATA-disk, and have noticed only one problem with it.. 

Installation goes without problems, and GRUB is installed where it should be installed (ie. beginning of SATA hd) 
BUT the problem is that GRUB thinks that my SATA hd is 2nd hd, and that my IDE is 1st hd (In reality SATA is the primary 1st and IDE is 2nd, so machine starts booting from SATA hd, as it should..) But each time I update kernel, or re-install ubuntu the grubs menu.lst is AUTOMATICALLY modified so that the machine wont boot anymore, until I manually edit the /boot/grub/menu.lst and change "root (hd1,0)" to "root	(hd0,0)"...


But if you have only 1 hdd, you cant have the same problem..

What do you mean, "SATA support is a bit patchy" ?? It should work just fine..

---

### Post by jethro10 on 2006-08-15
> **anaconda said:**
> 

What do you mean, "SATA support is a bit patchy" ?? It should work just fine..

Before I decided to keep the disk, I looked thru the forums and found more problems with SATA than IDE with a presumably much smaller install base and pehaps wrongly assumed it was less solid than IDE support. Sort of like wifi compared to wired Network cards.
But you've convinced me to "just do it"-tm.

J

---

### Post by handaxe on 2006-08-15
Hmmm, - I have an Acer TM 5610 with a SATA hd and there are problems in this instance - lock ups, ACPI interference??? - difficult to know but I get repeated SATA related error messages.

So, YMMV.

HA

> **jethro10 said:**
> Before I decided to keep the disk, I looked thru the forums and found more problems with SATA than IDE with a presumably much smaller install base and pehaps wrongly assumed it was less solid than IDE support. Sort of like wifi compared to wired Network cards.
But you've convinced me to "just do it"-tm.

J

---

### Post by jrjr on 2006-08-15
.

---

### Post by syedn on 2006-08-15
I'm currently runninb Ubuntu and XP dual-booted with two SATA hard drives (a 160 gig hitachi and a 250 gig seagate) and I've yet to encounter any problems.

---

### Post by bobpur on 2006-08-15
No problems with a 200 gb SATA on My HP Pavilion a820n with Dapper v6.06.1

---

### Post by drummer on 2006-08-15
I have 2 sata drives, one 80gb Hitachi and a 300gb Seagate (/home). No problems at all exept for the grub install, which is easily fixed, and I'm not sure if it's a problem anymore with Dapper.

---

### Post by Pro_photoguy on 2006-08-16
I have two SATA discs installed now. I am trying to get Windows and Ubuntu Linux to run on the same SATA drive. I even bought a special SATA controller card which supports Linux to try to get Linux to run on my tower. Linux won't boot when the SATA drive is plugged into the motherboard. When it is plugged into the motherboard it boots directly into Windows. When I plug the SATA drive into the controller card it boots to the grub and says GRUB 1.5. and stalls there. It won't finish booting into Linux. I'm still stuck on how I can fix this. Can anyone help???:shock:

---

### Post by Zalbor on 2006-08-17
My main hard disk is SATA, no problems with it at all.

> **anaconda said:**
> the problem is that GRUB thinks that my SATA hd is 2nd hd, and that my IDE is 1st hd (In reality SATA is the primary 1st and IDE is 2nd, so machine starts booting from SATA hd, as it should..) But each time I update kernel, or re-install ubuntu the grubs menu.lst is AUTOMATICALLY modified so that the machine wont boot anymore, until I manually edit the /boot/grub/menu.lst and change "root (hd1,0)" to "root	(hd0,0)"...
That's how it used to be for me, but it's fixable. Edit menu.lst. There's a part that will be like this:
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)
```
You can simply change the last line to groot=(hd0,0) (DO NOT UNCOMMENT IT, like it says earlier on the file) and with any update the kernels will be found there.

---

### Post by jethro10 on 2006-08-23
Incase anyone is interested.

The disk installed ok, ubuntu installed ok and everyone is happy.

J

---

### Post by doodsangel on 2006-08-23
> **anaconda said:**
> I have a SATA-disk, and have noticed only one problem with it.. 

Installation goes without problems, and GRUB is installed where it should be installed (ie. beginning of SATA hd) 
BUT the problem is that GRUB thinks that my SATA hd is 2nd hd, and that my IDE is 1st hd (In reality SATA is the primary 1st and IDE is 2nd, so machine starts booting from SATA hd, as it should..) But each time I update kernel, or re-install ubuntu the grubs menu.lst is AUTOMATICALLY modified so that the machine wont boot anymore, until I manually edit the /boot/grub/menu.lst and change "root (hd1,0)" to "root	(hd0,0)"...


But if you have only 1 hdd, you cant have the same problem..

What do you mean, "SATA support is a bit patchy" ?? It should work just fine..


On this, How do I configure grub to to boot Ubuntu from /dev/hda5?
Currently I get the error message after install:
[B]root(hd0,0)
Filesystem type unknown, partition type 0x7
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash[/B]
My installation resides on */dev/hda5* and not *root=/dev/hda1*

---

### Post by anaconda on 2006-08-23
Thank you Zalbor!! Will try the fix..

And doodsangel. The (more) right wersion would be:

```

tittle  Ubuntu 1
root(hd0,4)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda5 ro quiet splash
initrd /boot/initrd.img-2.6.12-9-386
savedefault
boot

```

---

### Post by doodsangel on 2006-08-23
Great. I thank you losts.:-D

---


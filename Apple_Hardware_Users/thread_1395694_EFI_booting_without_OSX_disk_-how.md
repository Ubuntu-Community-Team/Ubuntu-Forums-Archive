---
title: "EFI booting without OSX disk -how?"
date: 2010-02-01
forum: Apple Hardware Users
---

### Post by chronicanon on 2010-02-01
I have a Mac Pro 2,1 which I bought mainly because it was a silent box as well as well built, not because I am much of an OSX user.

I keep the original OSX disk for contingency --in case Apple releases firmware updates etc.

The disk I am actually using has 2 OSes on it: Ubuntu 9.10 and Windows 7.

This setup works, but not as well as it should. I need to improve things.

First, I'd like to boot under EFI --I don't want to wait for the pseudo BIOS, especially after I have seen OSX come up nearly instantly.

Secondly, booting under EFI means I can use AHCI instead of ordinary SATA interface. 

This is important for me not just because of speed increase, but also because I can use all 6 SATA ports on Mac Pro.

Here is my problem:

While Ubuntu 9.10 does create an EFIboot partition, it does not seem to use it --all I see on that partition is 2 files, BCD and BCD.LOG.

Also, while Ubuntu 9.10 also uses (can use) EFI grub (grub2), it resides in /boot (not in EFIboot partition) which means that Mac Pro has to go through its pseudo-BIOS before it gives me a menu to choose an OS. I have also tried using rEFIt, but it had no effect.

Plus, I have not been able to locate any usable information about how I can (force-)activate AHCI in grub2.

So, to cut it short(er); on a Mac Pro 2,1 with Ubuntu 9.10 + grub2:

i) How can I boot using EFI --without an OSX disk?

ii) How can I force activate AHCI under EFI?

---

### Post by linuxopjemac on 2010-02-01
there is an experimental wiki about it, maybe you can try that first:
[https://help.ubuntu.com/community/MactelSupportTeam/EFI-Boot-Mactel](https://help.ubuntu.com/community/MactelSupportTeam/EFI-Boot-Mactel)

2. maybe this is of help:
[http://www.insanelymac.com/forum/index.php?showtopic=126089](http://www.insanelymac.com/forum/index.php?showtopic=126089)

---

### Post by linuxopjemac on 2010-02-01
[http://forums.macrumors.com/showthread.php?t=486671](http://forums.macrumors.com/showthread.php?t=486671)

---

### Post by chronicanon on 2010-02-01
> **linuxopjemac said:**
> there is an experimental wiki about it, maybe you can try that first:
[https://help.ubuntu.com/community/MactelSupportTeam/EFI-Boot-Mactel](https://help.ubuntu.com/community/MactelSupportTeam/EFI-Boot-Mactel)

2. maybe this is of help:
[http://www.insanelymac.com/forum/index.php?showtopic=126089](http://www.insanelymac.com/forum/index.php?showtopic=126089) Thank you. I had read both (including further links from them) through; trouble is, one of the links (AHCI issue) assumes grub v1, and the other, assumes that OSX disk will be present.. [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]

Similarly, the macrumors thread applies only to grub v1 --as there is no Stage1 file in grub2 anymore. It's a completely different beast.

---

### Post by linuxopjemac on 2010-02-01
why don't you go for GRUB1?

I run Karmic on a MacBook 2,1 with GRUB1. I installed Jaunty first. Later I just installed Karmic over the Jaunty root partition, keeping GRUB1 (I am at one of the latest development version, i.e. grub-1.97~beta4).

---

### Post by chronicanon on 2010-02-01
> **linuxopjemac said:**
> Later I just installed Karmic over the Jaunty root partition, keeping GRUB1 (I am at one of the latest development version, i.e. **grub-1.97~beta4**).

Hang on.. that is what it show on my box too.

Are you sure v1.97 belongs grub v1 series?

I thought anything less than v1.00 was grub1, and above that grub2.

---

### Post by linuxopjemac on 2010-02-01
oops, I think you are right :( It is becoming Grub2 (we are at 1.97)

---

### Post by chronicanon on 2010-02-01
> **linuxopjemac said:**
> oops, I think you are right :( It is becoming Grub2 (we are at 1.97)

I am not so sure. There are various reasons for that.

First, this is what Grub Wiki says [ [http://grub.enbug.org/](http://grub.enbug.org/) ]:[INDENT]GRUB Legacy is a synonym of version 0.9x. GRUB Legacy provides rich features, but it has many design and implementation faults. GRUB Legacy is not maintained any longer. If you want more features, please use GRUB 2. 
[/INDENT]Secondly, when I check  /boot/grub, I don't see a Stage1 file at all [this is a fresh install], nor there's a menu.lst etc. IOW, I am pretty sure this is grub v2; because any change (such as disabling that darn ipv6) I want to to it can only be reflected to it by 'update-grub2'.

---

### Post by chronicanon on 2010-02-01
Sorry. I didn't see last post --was busy reading and writing a response your reply.

So.. if you are also on v2, how did you manage activating AHCI --or, is it a *perceived* improvement?

---

### Post by linuxopjemac on 2010-02-01
I meant to say in my former post that your are right and that 1.97 is indeed Grub 2....

---

### Post by linuxopjemac on 2010-02-01
I never activated AHCI, as I am not on a Mac Pro...

---


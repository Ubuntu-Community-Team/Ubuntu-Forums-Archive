---
title: "Grub Loader Wants To Be Boss"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by the.eagle on 2007-09-27
i HAVE 2 HARD DRIVES, XP AND UBUNTU. BOTH SET AS MASTER, AND I USE A 3RD PARTY BOOT MANAGER. WHEN I BOOT INTO UBUNTU IT SETS UP ITS OWN BOOT LOADER AND RE-SETS THE HDD ORDER IN THE BIOS. HOW DO I RESOLVE THIS? OR IS IT THE NATURE OF THE THING, AS THE BOOT MANAGER( ACRONIS) SAYS IT SUPPORTS LINUX. CHEERS ...:)  IAN

---

### Post by lisati on 2007-09-27
Ubuntu replaces the Windows loader with its own (grub). If you do a "dual boot" it will let you choose..

A friendly note: typing in ALL CAPITALS is consider to be "shouting" by many people, and doesn't always go down too well.

---

### Post by justleen on 2007-09-27
you should be able to add ubuntu to acronis.

Ubuntu can change any BIOS settings, though it can have its own boot order of drives..

I think acronis is messing with your CAPSlock as well, not just your MBR :)

---

### Post by the.eagle on 2007-09-27
Thank you, I tried that but it keeps on doing it. Also i didn't realise the caps were on, sorry.

---

### Post by dreadlord_chris on 2007-09-27
How about just not installing GRUB?

pretty sure it **is** is option when installing Ubuntu..

---

### Post by Mr.Beast on 2007-09-27
> **the.eagle said:**
> i HAVE 2 HARD DRIVES, XP AND UBUNTU. BOTH SET AS MASTER, AND I USE A 3RD PARTY BOOT MANAGER. WHEN I BOOT INTO UBUNTU IT SETS UP ITS OWN BOOT LOADER AND RE-SETS THE HDD ORDER IN THE BIOS. HOW DO I RESOLVE THIS? OR IS IT THE NATURE OF THE THING, AS THE BOOT MANAGER( ACRONIS) SAYS IT SUPPORTS LINUX. CHEERS ...:)  IAN

Hi.
When you say both are set as master, I'm a little confused.
You can only Boot from one disk. (Let's not get into raid, n stuff and assume you have a normal IDE, or SATA config).
So, you have a boot partition on both disks, one has acronis on it, and one has grub.
Now I'm not sure how your hard disks are organised in terms of Master and slave, or cable select, but you should be able to boot from either physical disk.

My guess at the moment is that acronis is on the primary disk (the one that wants to boot) and when you boot into ubnuntu, it tries to install grub but gets intercepted by acronis?
I think you need someone who is familiar with acronis more than I but have I explained it correctly?

---

### Post by davedumas0 on 2007-09-27
do u have a recovery partition on your windows HD if so its somehow messing with grub
 i could not dual boot worth a damn untill i made recovery disks (for windows) and deleted the recovery partition

---


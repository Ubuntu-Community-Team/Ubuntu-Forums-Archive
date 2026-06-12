---
title: "Can't Install Ubuntu 5.10, Grub 1.5 Error"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by slinga on 2006-01-28
Hey all, 

I'm trying to install Ubuntu 5.10 on an AMD 64 machine and I'm having a weird problem. The install completes no problem, but when it reboots it gives me a grub error. The exact error is: "GRUD Loading Stage1.5Read Error". 

I tried to use the live CD to boot into rescue mode, but that didn't work either. Can you give me some advice? I'm not trying to do anything fancy like dual boot and I'm giving Ubuntu all hard disk I have in there. Why won't this work? Also this is IDE, not SATA, as I know Ubuntu can't handle Sata installs either. Thanks in advance.

---

### Post by Pragmatist on 2006-02-05
stage1.5 loads the filesystem configuration.  Both stage1.5 and stage2  are located in /boot/grub  So at least stage1 in your MBR works!

Personally, I would use Knoppix  go to [www.knoppix.org](www.knoppix.org)  and burn a copy.  Once in the system, send us the partition table by using ```
fdisk /dev/hda
``` if /dev/hda is the harddisk your interested in.  then type ```
p
``` to print the partition table.  Note the partition with an * next to it indicating it is a boot partition.

Also, send us the contents of /boot/grub/menu.lst

---


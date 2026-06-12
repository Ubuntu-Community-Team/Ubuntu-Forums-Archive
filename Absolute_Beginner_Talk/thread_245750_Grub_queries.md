---
title: "Grub queries"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by Gerry Atric on 2006-08-28
Can anyone please help me with the correct procedure and/or code to locate exactly where on a dual boot system with Win XP on H/disk 1 on the first part sda and Ubuntu on the first part of H/disk 2 on sdb. Where would:-

1.  The MBR and Part Table for Win XP be located.
2.  The MBR, Part Table for Ubuntu and Grub Stage1 and Grub stage2 be located
3.  How to find the locations.

Win XP was first installed and Ubuntu was added to the second disk first partition later. Grub boots to Ubuntu first. 

Can the locations of the Grub Stage 1&2 be ascertained from the command line? or is it needed to boot to the Live or Rescue Disk.

---

### Post by janbockaert on 2006-08-28
not sure i understand your problem, so i'm not sure this will help: [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_change_default_Operating_System_boot-up_for_GRUB_menu](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_change_default_Operating_System_boot-up_for_GRUB_menu)

but maybe, you will find the answer on the same site. (or maybe, i just pointed to somthing silly you already knew)

---

### Post by jerry_c on 2006-08-28
Gerry. 

Booting from the live CD and using ```
sudo gparted
``` will show you your partitions. 

You can also use ```
sudo nautilus
``` to browse your /dev directory for hdxx and sdxx partitions. You can then mount them to your file system and browse them with nautilus to see their contents. 

There's also a thread specifically devoted to grub issues here: [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

Good luck.

---

### Post by Gerry Atric on 2006-08-29
Thanks for your help, I need all I can get. Much appreciated

---


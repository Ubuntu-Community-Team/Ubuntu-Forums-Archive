---
title: "error: Unable to mount the selected volume"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by sivro on 2007-09-04
I wanted to install Ubuntu 6.06. LTS on my laptop with external dvd drive (matshita). Just on the beginning, boot freeze after i got message: IRQ not accepting adress bla bla. I started ubuntu setup with parameter noapic nolapic and everything worked. After installation I boot und logged in Ubuntu and wanted to access NTFS partition and there was error:
[B]
Unable to mount the selected volume.
error: device /dev/hda1 is not removable
error: could not execute pmount[/B]


How do I mount my two NTFS partitions?

my disk:

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1931    15510726    7  HPFS/NTFS
/dev/hda2            1932        3978    16442527+   7  HPFS/NTFS
/dev/hda3            3979        4709     5871757+  83  Linux
/dev/hda4            4710        4786      618502+   f  W95 Ext'd (LBA)
/dev/hda5            4746        4786      329269+  82  Linux swap / Solaris
/dev/hda6            4710        4745      289107   82  Linux swap / Solaris

---

### Post by ray bot on 2007-09-06
Try this: ```
sudo apt-get install ntfs-3g
```

---

### Post by sivro on 2007-09-16
After typing 

sudo apt-get install ntfs-3g  

I got the following error:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ntfs-3g

---

### Post by logos34 on 2007-09-16
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by sivro on 2007-09-19
Thanx a lot! Everything works fine now!

---


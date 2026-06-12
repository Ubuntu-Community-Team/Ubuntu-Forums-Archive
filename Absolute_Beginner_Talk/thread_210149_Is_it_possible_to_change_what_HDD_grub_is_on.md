---
title: "Is it possible to change what HDD grub is on?"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by IDontKnow9998 on 2006-07-06
This has been bugging me for a while now.... When I installed linux grub installed itself on the completely wrong hdd (yeah, major wtf).... and im replacing that HDD in 1-2 months.... Is it possible to install grub on the HDD with my windows/linux is on?

---

### Post by mlind on 2006-07-06
yes, 

```

sudo grub-install */dev/xxx*

```
where /dev/xxx is the actual device (not a partition).


To list available partitions, use
```

sudo fdisk -l

```

---

### Post by IDontKnow9998 on 2006-07-06
> Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sdb2           12749       23943    89923837+  83  Linux
/dev/sdb3           23944       24321     3036285    5  Extended
/dev/sdb5           23944       24321     3036253+  82  Linux swap / Solaris


I did: "sudo grub-install /dev/sdb3"... It said completed successfully or something like. I rebooted, changed boot priority in bios, restarted. It was like grub was never installed, it just booted into Windows xp...

---

### Post by mlind on 2006-07-06
[QUOTE=IDontKnow9998]I did: "sudo grub-install /dev/sdb3"... It said completed successfully or something like. I rebooted, changed boot priority in bios, restarted. It was like grub was never installed, it just booted into Windows xp...[/QUOTE]

You should have installed it on /dev/sdb

---

### Post by IDontKnow9998 on 2006-07-06
[QUOTE=mlind]You should have installed it on /dev/sdb[/QUOTE]

i tried that... Both my Linux and Windows XP wont work....

On Linux I get this error message:
> root (hd3,1)
Error22: No such partition
Press any key to continue...

I also compared both the info in grub from both HDDs and they are both the exact same thing (when you hit e to edit it).

---

### Post by shoot2kill on 2006-07-06
you may need to change your menu.lst... post your menu.lst here

/boot/grub/menu.lst

grub is looking on hd3 for linux, not sdb

---

### Post by mlind on 2006-07-06
Did you remove hdd or disable one from bios?
If drive ordering changes, you must update grub to know that.

---

### Post by IDontKnow9998 on 2006-07-06
[QUOTE=mlind]Did you remove hdd or disable one from bios?
If drive ordering changes, you must update grub to know that.[/QUOTE]

I changed the boot priority. I have 4 HDDs. 

shoot2kill: How? If I get this list in linux then its useless if it changes when I change my boot priority.

---

### Post by rccharles on 2006-07-06
[QUOTE=IDontKnow9998]I did: "sudo grub-install /dev/sdb3"... [/QUOTE]
I am not a expert, but...

Could this have caused a problem by writing over the first sector in the partition?

Robert

---

### Post by IDontKnow9998 on 2006-07-07
Anyone?

---

### Post by mlind on 2006-07-07
Could you post the full output of fdisk -l

---

### Post by IDontKnow9998 on 2006-07-07
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      484521   244198552+   7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sdb2           12749       23943    89923837+  83  Linux
/dev/sdb3           23944       24321     3036285    5  Extended
/dev/sdb5           23944       24321     3036253+  82  Linux swap / Solaris

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19079   153252036    7  HPFS/NTFS
/dev/hda3           19080       19457     3036285    5  Extended

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       30401   244196001    7  HPFS/NTFS
```
 .

---

### Post by mlind on 2006-07-07
Could you try if either 0, 1, 2 or 3 refenrece to your root partition on GRUB menu? You can try this by editing (press 'e' on GRUB menu) the boot parameters of a kernel and using TAB to autocomplete.

/dev/sdb seems to have 4 partitions, so type
root (hd1,

and press TAB to show available partitions.
There's info about naming conventions on GRUB manual
[http://www.gnu.org/software/grub/manual/grub.html#Naming-convention](http://www.gnu.org/software/grub/manual/grub.html#Naming-convention)

(I'm curious why your only Linux partition, /dev/sdb2, doesn't have bootable flag on...)

---


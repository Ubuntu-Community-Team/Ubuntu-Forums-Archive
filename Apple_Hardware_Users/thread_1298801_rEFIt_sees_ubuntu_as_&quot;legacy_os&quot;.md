---
title: "rEFIt sees ubuntu as &quot;legacy os&quot;"
date: 2009-10-23
forum: Apple Hardware Users
---

### Post by firemoth on 2009-10-23
Hey guys,

Maybe somebody can help me with this strange issue.  I set up a triple boot with Snow Leopard, Windows 7 Pro, and Karmic. Here are my partitions:
```

nick@Macbook:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd89d2429

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2              26       24428   196007520   af  HFS / HFS+
/dev/sda3           24444       31679    58113024    7  HPFS/NTFS
/dev/sda4   *       31679       38914    58114048   83  Linux


```I followed what most guides said and installed grub to /dev/sda4.  Everything's fine...rEFIt gives me 3 options...boot Mac OSX, boot Windows, and boot Legacy OS.  The OSX and Windows options boot directly and perfectly.  When I choose "Legacy OS," grub starts and I can choose Ubuntu.  My question is why won't rEFIt see Linux as Linux?

---

### Post by maflynn on 2009-10-23
I saw that too.  rEFIt probably needs to be updated to see that 9.10 is Ubuntu/Linux.

Personally, I'm not really bothered by the representation as long as it boots up, and for me it does

---

### Post by Bachstelze on 2009-10-23
> **firemoth said:**
> My question is why won't rEFIt see Linux as Linux?

Because it doesn't (yet) recogize GRUB 2 (basically, rEFIT thinks that "a Linux system is a system with GRUB O.97). So if you want your Karmic to appear as Linux, you'll have to install GRUB 0.97 on it, or wait for a rEFIt update that will recognize GRUB 2 as "Linux".

---

### Post by Eadz on 2009-10-23
This is the bug tracker entry for the item. 

[http://sourceforge.net/tracker/?func=detail&aid=2861566&group_id=161917&atid=821764](http://sourceforge.net/tracker/?func=detail&aid=2861566&group_id=161917&atid=821764)

---

### Post by mabovo on 2009-10-23
[http://ubuntuforums.org/showthread.php?p=8155026&posted=1#post8155026](http://ubuntuforums.org/showthread.php?p=8155026&posted=1#post8155026)

---

### Post by macaholic on 2009-10-26
Personally I've never had rEFIt recognize any of my partitions as linux, they are always listed as legacy OS. I just hold down alt when i'm booting now, it seems to load faster than rEFIt. Apple's bootloader recognizes all my windows partitions as "Windows".

---


---
title: "Mounting old /home in new installation"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by V-600 on 2007-05-10
hi all

I had ubuntu 6.10 set up with /home on its own separate partition. I used the system upgrade to get ubuntu 7.04.

I should point out now that everything works (with the odd exception that totem freezes the system when playing mp3's) but it has left me with an untidy system. There are bits of the old ubuntu install lying about. The reason I created the separate /home partition was to make updates easier but in reading a few posts I have heard of a UUID.

As things stand here is my fstab. You can see that hda1 and hda5 have a UUID but the partition I created does not.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=af5bcf45-8547-4545-affb-b4bb22b8f046 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=8c907ff6-8be3-4e85-ac00-4988eadeeb9a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/cdrom        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda3 /home ext3 nodev,nosuid 0 2


Do I need a UUID (and what does it do) to remount my /home if I wipe hda1 and reinstall ubuntu 7.04? I had planned simply to rewrite the last line into the new fstab but would like confirmation that this will work with the new install.

many thanks

nathan

---

### Post by Bachstelze on 2007-05-10
In a terminal, run the command

```
blkid
```

that should give you the UUID of your partitions, you can then use them to add an entry about them in your fstab. The "old school" /dev/hdaX should work too but better do it the new way ;)

---

### Post by V-600 on 2007-05-10
thanks.

you learn something new everyday, as they say

---

### Post by V-600 on 2007-05-11
Maybe i shouldn't have spoken so soon. All blkid gives is the following. There is no UUID for hda3.

/dev/hda1: UUID="af5bcf45-8547-4545-affb-b4bb22b8f046" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda5: UUID="8c907ff6-8be3-4e85-ac00-4988eadeeb9a" TYPE="swap" 

Also could someone tell me how to get the coloured indents/backgrounds people use when pasting terminal outputs and commands.:D

---


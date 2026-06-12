---
title: "Lots of Issues"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by moomintroll on 2007-03-09
OK, I really want to make this work but keep coming across really frustrating issues - I'm a complete noob and although I have searched the forums I just can't solve some of these issues.

Got Edgy Ultimate 1.2 and XP dual boot

1) No read / write access to HDB1 ntfs partition - only read access

Here's my fstab # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=1b1ff971-080b-4e33-b1af-429181be0846 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1
UUID=667480A074807519 /media/hdb1     ntfs    defaults,nls=utf8,umask=0222,gid=46 0       1
# /dev/hda3
UUID=7db7597f-fb6b-4f81-b840-7ca0bed7951b none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,auto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,auto     0       0

2)Can only boot in to windows if I boot in to Ubuntu and then restart and then select windows from grub list.  If I try to boot in to windows from cold start it fails after a momentary  view of the XP splashscreen before rebooting itself.

3) I dont seem to be able to add another user to be able to allow them access to the Sudo terminal prompt.  I dont know if my system/administration/ users-groups program is working correctly because i dont seem to be able to change the user properties to anything - no option available.

Any help would be most appreciated - I really dont want to start again or worse give up on this Linux thing.  Thx

---

### Post by Aberrix on 2007-03-09
> **moomintroll said:**
> 
1) No read / write access to HDB1 ntfs partition - only read access


linux cannot natively write to ntfs partitions, you'll have to install a 3rd party app like ntfs-3g in order to read/write to it.

---


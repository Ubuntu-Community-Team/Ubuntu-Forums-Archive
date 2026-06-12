---
title: "&quot;IO charset iso8859-1 not found&quot;, can't mount USB Stick!!"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by taekr on 2008-01-20
When plugging in my usb stick, I keep getting the error:

mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
missing codepage or other error or helper program or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

Thus, I do "dmesg | tail" and I get:

sd 6:0:0:0: [sdc] Assuming drive cache: write through
sd 6:0:0:0: [sdc] 2013184 512-byte hardware sectors (1031 MB)
sd 6:0:0:0: [sdc] Write Protect is off
sd 6:0:0:0: [sdc] Mode Sense: 23 00 00 00
sd 6:0:0:0: [sdc] Assuming drive cache: write through
 sdc: sdc1
sd 6:0:0:0: [sdc] Attached SCSI removable disk
sd 6:0:0:0: Attached scsi generic sg3 type 0
Unable to load NLS charset iso8859-1
FAT: IO charset iso8859-1 not found


I goggled 'IO charset iso8859-1 not found'  and found a suggestion:

"I tried recompiling the kernel again, only with iso8859-1 as a module instead of compiled directly into the kernel, and it works! Strange, though, my roommate's kernel has it compiled directly in and his works fine...."

Well, I have no idea how to compile the kernel again. and not sure whether this is the solution or not. 

I'm using ubuntu 7.10. I complied Kernel according to Master Kernel, [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158) 

i do dual-boot .. xp and ubuntu. Ubuntu mounts NTFS drive. It mounts my two USB portable harddisk (both NTFS).  two memory sticks are fomated with Fat 32. I start wondering if it is because of the file system.  

Any suggestion on how to mount usb sticks?

cheers,

---


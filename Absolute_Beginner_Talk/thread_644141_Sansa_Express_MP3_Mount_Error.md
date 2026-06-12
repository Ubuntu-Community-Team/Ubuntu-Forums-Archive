---
title: "Sansa Express MP3 Mount Error"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by 0point on 2007-12-18
Running Ubuntu Gutsy
This is a problem i have run into twice now, once with my new Sansa Express mp3 player and earlier with my ANCIENT Creative nomad 2 (tiny 256mg old mp3 player)
whenever i insert the Sansa Express mp3 player into the usb hub i get this error message:
mount: wrong fs type, bad option, bad superblock on /dev/sdc1, missing codepage or helper program, or other error.

when i bring up dmesg | tail i get this:
[52770.449089] sd 3:0:0:0: Attached scsi generic sg2 type 0
[52770.450650] sd 3:0:0:1: Attached scsi removable disk sdd
[52770.450687] sd 3:0:0:1: Attached scsi generic sg3 type 0
[52770.878354] FAT: Unrecognized mount option "usefree" or missing value
[52876.120809] FAT: Unrecognized mount option "usefree" or missing value
[52936.162546] FAT: Unrecognized mount option "usefree" or missing value
[52964.822456] FAT: Unrecognized mount option "usefree" or missing value
[53871.093194] FAT: Unrecognized mount option "usefree" or missing value
[53936.572427] FAT: Unrecognized mount option "usefree" or missing value
[53966.287459] FAT: Unrecognized mount option "usefree" or missing value

i went searching around and found that alot of people wanted to know about the fstab file, so here's that as well

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=0afe33c1-a254-4cba-9f4d-86f228e8fcf4 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=c3862718-1f0f-4c71-8019-55ac0287f252 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/sda1 /media/sda1 ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sdb1 /media/sdb1 ntfs-3g defaults,locale=en_US.utf8 0 0

this has been driving me crazy as of late, any help would be greatly appreciated

---

### Post by legend2440 on 2007-12-19
0point
Go to System>>Preferences>>Removeable Drives and Media>>Storage and make sure first three boxes are checked.
Hope that helps

---


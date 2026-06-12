---
title: "seen anyting like this? strange unknown duplicated partition"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by julbuntu on 2006-12-24
hi,

i am new in linux,as you can see on attached screenshot, i am having a second "unknown" HDD as the one & only i have,a 100gib HDD.It didnt happen right away when i first load up Ubuntu,but i am not sure what causes it.I used Gparted on live CD for partitioning & no error was shown.Its doesnt cause any problem so far but its just anoying having it on my ubuntu.

Thanks for the help!

jul

<a href="http://photobucket.com/" target="_blank"><img src="http://i130.photobucket.com/albums/p260/julphoto/Screenshot.png" border="0" alt="Photobucket - Video and Image Hosting"></a>

---

### Post by julbuntu on 2006-12-24
hi,

i am new in linux,as you can see on attached screenshot, i am having a second "unknown" HDD as the one & only i have,a 100gib HDD.It didnt happen right away when i first load up Ubuntu,but i am not sure what causes it.I used Gparted on live CD for partitioning & no error was shown.Its doesnt cause any problem so far but its just anoying having it on my ubuntu.

Thanks for the help!

jul

[HTML]<a href="http://photobucket.com/" target="_blank"><img src="http://i130.photobucket.com/albums/p260/julphoto/Screenshot.png" border="0" alt="Photobucket - Video and Image Hosting"></a>[/HTML]

---

### Post by haxer on 2006-12-24
Maybe you should fix the link? :-k

---

### Post by julbuntu on 2006-12-24
hi,

i am new in linux,as you can see on attached screenshot, i am having a second "unknown" HDD as the one & only i have,a 100gib HDD.It didnt happen right away when i first load up Ubuntu,but i am not sure what causes it.I used Gparted on live CD for partitioning & no error was shown.Its doesnt cause any problem so far but its just anoying having it on my ubuntu.

Thanks for the help!

jul

---

### Post by RAV TUX on 2006-12-24
[julbuntu]("http://www.ubuntuforums.org/member.php?u=212822") please use the "EDIT" button as opposed to posting multiply threads.

---

### Post by julbuntu on 2006-12-24
sorry,got it awfuly wrong there,seldom post in forums:P...i think the link is ok now?


jul

---

### Post by po0f on 2006-12-24
julbuntu,

Open up a terminal and tell what this command says:
```
[FONT="Courier New"]$ sudo fdisk -l[/FONT]
```
It will ask for a password, type the password you use to login with.

---

### Post by RAV TUX on 2006-12-24
do you have dual core?

---

### Post by julbuntu on 2006-12-24
> **po0f said:**
> julbuntu,

Open up a terminal and tell what this command says:
```
[FONT="Courier New"]$ sudo fdisk -l[/FONT]
```
It will ask for a password, type the password you use to login with.
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2           12031       12161     1052257+  d7  Unknown
/dev/sda3            5100        6501    11261565   83  Linux
/dev/sda4            6502       12030    44411692+   5  Extended
/dev/sda5            6502       10963    35840983+   7  HPFS/NTFS
/dev/sda6           10964       11094     1052226   82  Linux swap / Solaris
/dev/sda7           11095       12030     7518388+   b  W95 FAT32

Partition table entries are not in disk order

---

### Post by julbuntu on 2006-12-24
> **RAV TUX said:**
> do you have dual core?
yes,i have a intel dual-core on hp dv2000 laptop

---

### Post by julbuntu on 2006-12-24
> **RAV TUX said:**
> [julbuntu]("http://www.ubuntuforums.org/member.php?u=212822") please use the "EDIT" button as opposed to posting multiply threads.
sorry

---


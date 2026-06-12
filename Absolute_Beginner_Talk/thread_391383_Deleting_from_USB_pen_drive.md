---
title: "Deleting from USB pen drive"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by adam s on 2007-03-23
Hi guys,

I just bought a cheap USB pen drive to put my kids MP3 songs on it.

I managed to install some files onto it - but in folders.

I am now trying to delete the files - and it does not allow me in either nautilus or the command line. It does not matter whether I run as root or my normal login.

An  fdisk command gives :

Disk /dev/sdb: 515 MB, 515899392 bytes
16 heads, 32 sectors/track, 1968 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1968      503792    e  W95 FAT16 (LBA)


Any ideas?

Thanks,

Adam

---

### Post by slimdog360 on 2007-03-23
it not allow you? do you mean its like a permissions thing?

Ive noticed on my mp3 player when I go to delete songs it puts them into a .Trash folder (a hidden folder) inside the player. So they are not actually deleted. All I have to do is when in Nautilis check the 'show hidden folders' button from one of the menus. Then delete the trash folder it creates.

But Im guessing its a permissions thing so try this in a terminal after you insert the thing
```
sudo chmod 777 -R /dev/sdb
```
If that works let me (or someone else know by posting back here).

---

### Post by adam s on 2007-03-23
Hi,

It just didn't allow me. I had the correct permissions.

I have just found out that 1 of the files was corrupted - maybe this was the reason?

Thanks,

Adam.

---


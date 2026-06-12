---
title: "corrupt directory - Read-only file system"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by mspendlo on 2007-04-13
Hi

I am on 6.10 dual booted with winXP.

I have a FAT32 external Lacie drive that I use for storage. I downloaded some MP3s the other day from an online store on another windows latop. Attached the drive to my laptop and booted Ubuntu and played the files OK.

Upon next boot of ubuntu I noticed the directory was corrupt (can't remember if this was after an boot into winXP or not..). Problem now is I can't delete the directory (in Windows or Ubuntu).

I have run `chkdsk' successfully from winXP. 

`dosfsck' gives me :

matt@matt-laptop:/media/LACIE/music/purchased$ dosfsck /media/LACIE/music/purchased/
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Read 512 bytes at 0:Is a directory

The files all have "strange" garbled names (winXP just shows them all as one corrupt file). If I pick one :

matt@matt-laptop:/media/LACIE/music/purchased$ rm a.i 
rm: cannot remove `a.i': Read-only file system

or try to create a file in this dir :

matt@matt-laptop:/media/LACIE/music/purchased$ touch msp.test
touch: cannot touch `msp.test': Read-only file system

the rest of the disk is OK as far as I can tell. It's fairly new..

Any pointers or suggestions appreciated.

Matt

---

### Post by nixclusive on 2007-04-13
> **mspendlo said:**
> Hi

I am on 6.10 dual booted with winXP.

I have a FAT32 external Lacie drive that I use for storage. I downloaded some MP3s the other day from an online store on another windows latop. Attached the drive to my laptop and booted Ubuntu and played the files OK.

Upon next boot of ubuntu I noticed the directory was corrupt (can't remember if this was after an boot into winXP or not..). Problem now is I can't delete the directory (in Windows or Ubuntu).

I have run `chkdsk' successfully from winXP. 

`dosfsck' gives me :

matt@matt-laptop:/media/LACIE/music/purchased$ dosfsck /media/LACIE/music/purchased/
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Read 512 bytes at 0:Is a directory

The files all have "strange" garbled names (winXP just shows them all as one corrupt file). If I pick one :

matt@matt-laptop:/media/LACIE/music/purchased$ rm a.i 
rm: cannot remove `a.i': Read-only file system

or try to create a file in this dir :

matt@matt-laptop:/media/LACIE/music/purchased$ touch msp.test
touch: cannot touch `msp.test': Read-only file system

the rest of the disk is OK as far as I can tell. It's fairly new..

Any pointers or suggestions appreciated.

Matt

I'm not sure exactly what may have happened.. a filesystem, especially the FAT file system, can go currupt for a lot of reasons. If data recovery is not absolutly necessary for you, go ahead and re-format the drive and check whether its still usable.

---

### Post by nixclusive on 2007-04-13
> **nixclusive said:**
> I'm not sure exactly what may have happened.. a filesystem, especially the FAT file system, can go currupt for a lot of reasons. If data recovery is not absolutly necessary for you, go ahead and re-format the drive and check whether its still usable.

Just a quick note again.. if you REALLY need to recover that data, make sure you have a raw image of the whole device before attempting anything that might lead to further damage.

```
dd if=/dev/<device> of=$HOME/backup.bin bs=64k
```

where <device> is the file corresponding to your device. After that, if anything goes wrong or you think you need to a rollback, just dump the binary image back onto the device:

```
dd if=$HOME/backup.bin of=/dev/<device> bs=64k conv=notrunc
```

Note: the binary image will be as large as your device. Make sure you have enough space.. or maybe try piping dd's output through gzip or something... 

Good Luck :-)

---

### Post by mspendlo on 2007-04-13
> **nixclusive said:**
> I'm not sure exactly what may have happened.. a filesystem, especially the FAT file system, can go currupt for a lot of reasons. If data recovery is not absolutly necessary for you, go ahead and re-format the drive and check whether its still usable.

This'll make me popular I'm sure BUT I never had a problem with fat32 before until dual booting linux...

I am "on the road" for the next coupla months so I can't revert to backups or reformat (not enough space to create an image). 

Don't know much about it but I find it hard to believe I must reformat because of one corrupt directory ? The disk seems to function perfectly otherwise.. 

It's having knock on effects though as, for example, RhythmBox is unhappy unless I unwatch the root music directory as it obvious tries to read the corrupt sub dir.

I don't need to recover the corrupt dir, just delete it. Anything else I can do ?

---


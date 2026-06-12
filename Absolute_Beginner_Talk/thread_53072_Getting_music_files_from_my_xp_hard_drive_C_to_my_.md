---
title: "Getting music files from my xp hard drive C: to my new drive with Ubuntu"
date: 2005-07-30
forum: Absolute Beginner Talk
---

### Post by lifewillfadeaway on 2005-07-30
Can anyone help me on Getting music files from my xp hard drive C: to my new drive with Ubuntu?

---

### Post by bored2k on 2005-07-30
1. Execute the commands in Terminal mode (Applications -> System Tools -> Terminal)
2. sudo fdisk -l

Here you would get a list of your partition table. You can then post it here and tell us wich partition do you want mounted.

[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

---

### Post by lifewillfadeaway on 2005-07-30
Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9399    75497436   83  Linux
/dev/hdc2            9400        9729     2650725    5  Extended
/dev/hdc5            9400        9729     2650693+  82  Linux swap / Solaris

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14946   120053713+   7  HPFS/NTFS

------------------------------------------------------------------------------------------------------

---

### Post by bored2k on 2005-07-30
You forgot to mention wich one do you want mounted. I suppose it's your NTFS drive.

Mount point will be /media/windows
```
read my following post
```

Edit: You must know you will only get Read access to this drive. If you want full write&read access, convert it to FAT32 (make sure you tell us about it, because the previous line will have to change ;)).

---

### Post by lifewillfadeaway on 2005-07-30
My mistake. You are correct it is indeed the NTFS i want mounted  :)  
However: sudo echo /dev/sda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0 >> /etc/fstab

keeps giving me bash: /etc/fstab: Permission denied

---

### Post by bored2k on 2005-07-30
[QUOTE=lifewillfadeaway]My mistake. You are correct it is indeed the NTFS i want mounted  :)  
However: sudo echo /dev/sda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0 >> /etc/fstab

keeps giving me bash: /etc/fstab: Permission denied[/QUOTE]
 Weird.. Ok my bad then. Try this instead:

1. sudo gedit /etc/fstab
2.Append the following lines:
> SMACKS HEAD IN DISBELIEF. Read following post..
3. Save and close
4. sudo mount -a

---

### Post by lifewillfadeaway on 2005-07-30
Alrighty got /etc/fstab appended.
however now when:  sudo mount -a
                                [mntent]: line 10 in /etc/fstab is bad

---

### Post by bored2k on 2005-07-30
[QUOTE=lifewillfadeaway]Alrighty got /etc/fstab appended.
however now when:  sudo mount -a
                                [mntent]: line 10 in /etc/fstab is bad[/QUOTE]
 OMG I'm so sleepy and wreckless!
The line is 
>  /dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0
*Gomen nasai :(!!*

---

### Post by lifewillfadeaway on 2005-07-30
Nevermind.... took out sudo echo and it mounted just fine! Thank for your help, much appreciated.  :razz:

---

### Post by bored2k on 2005-07-30
[QUOTE=lifewillfadeaway]Nevermind.... took out sudo echo and it mounted just fine! Thank for your help, much appreciated.  :razz:[/QUOTE]
 Sorry for my mal-oriented help. It's 4am. I'm usually not that bad..

---

### Post by lifewillfadeaway on 2005-07-30
Hehe no worries! It's 2:00 here and im already getting foggy!

---

### Post by whodat on 2005-07-30
Are you only allowed to read NTFS because, when I try to write to my windows drive, it says this drive is read-only?

On the guide for mounting the windows drive, there is a read/write for FAT, but none for NFTS.

Is there anyway to change permissions, so that I can write to my windows drive(NFTS)?

---

### Post by bored2k on 2005-07-30
[QUOTE=whodat]Are you only allowed to read NTFS because, when I try to write to my windows drive, it says this drive is read-only?

On the guide for mounting the windows drive, there is a read/write for FAT, but none for NFTS.

Is there anyway to change permissions, so that I can write to my windows drive(NFTS)?[/QUOTE]
 You can't write to NTFS. Some say you could but you're better off _not_ trying.

---


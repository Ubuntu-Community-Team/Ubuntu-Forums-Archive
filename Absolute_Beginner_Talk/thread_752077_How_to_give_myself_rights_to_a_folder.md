---
title: "How to give myself rights to a folder?"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by kramer65 on 2008-04-11
Hello,

I have a folder on an external hard drive (fat32) which contains my music. I want to add things to it but it won't let me because I have no admin rights. I can do it with the command line everytime (with cp sudo or something, have to look it up) but that is simply really really annoying.

How can I give myself rights to a certain folder? Or simply to the whole drive including all folders and subfolders? I know that this is not smart for things like /lib etc (don't have a clue what it exactly does, but its something for the system..), but this is just for my data which I always need to be able to change or add to..

How would I do this?

---

### Post by hums07 on 2008-04-11
> **kramer65 said:**
> Hello,

I have a folder on an external hard drive (fat32) which contains my music. I want to add things to it but it won't let me because I have no admin rights. I can do it with the command line everytime (with cp sudo or something, have to look it up) but that is simply really really annoying.

How can I give myself rights to a certain folder? Or simply to the whole drive including all folders and subfolders? I know that this is not smart for things like /lib etc (don't have a clue what it exactly does, but its something for the system..), but this is just for my data which I always need to be able to change or add to..

How would I do this?

I never have that problem and always have the read/write rights.

See the ownership of the media (right click - properties), at Permission tab I think, see the name of the group. In user management, add your self as member of that group.

---

### Post by Souls-hunteR on 2008-04-11
```
sudo chmod a+r,a+w file_name
```

---

### Post by Schendje on 2008-04-11
You can also try Alt+F2 and then type "gksudo nautilus", which opens Nautilus with root permissions. From there, go to the folder, right-click -> properties -> permissions. There you can edit the permissions needed for the folders/files. There's also a button "Apply permissions to enclosed files" if I remember correctly.

This is the way I always do it, I'm not 100% sure if it's the right way, or entirely safe. But it works for me. :)

---

### Post by kramer65 on 2008-04-11
Yea I try that. But then it says that I don't have rights to do that..

What now...?

---

### Post by Schendje on 2008-04-11
Which way did you use? Mine or Souls-hunteR's?

Btw, I just noticed you're Dutch too. Gezellig. :)

---

### Post by erginemr on 2008-04-11
I believe it is a setting that need to be done in the file **/etc/fstab** to give users write permissions. So first, please post the outputs of the following four commands from the terminal:
```
sudo fdisk -l
```
```
blkid
```
```
ls -l /media
```
```
cat /etc/fstab
```

---

### Post by kramer65 on 2008-04-11
> **Souls-hunteR said:**
> ```
sudo chmod a+r,a+w file_name
```

Great! That works!

Now how do I change the right of this folder AND all the underlying folders?

---

### Post by hums07 on 2008-04-11
> **kramer65 said:**
> Great! That works!

Now how do I change the right of this folder AND all the underlying folders?

Yes but you have to do it file by file.
Follow **eginemr**, it will set the access rights for the whole filesystem (external drive) at boot time.

---

### Post by StRiFe10101 on 2008-04-11
I had a similar problem.  I had tons of music that i could get to some and some I could not.

I simply did this and it worked.  I changed the permissions on the folder using the recursive option/switch (changes the permission of all files withing).

```
sudo -r chmod 777 "folder location and name"
```

or it was 

```
sudo chmod -r 777 "folder location and name"
```

I can't remember.  I had to try 3 different variats to get it to work..lol.  Have a go yourself and try it out.

---

### Post by hums07 on 2008-04-12
> **StRiFe10101 said:**
> I had a similar problem.  I had tons of music that i could get to some and some I could not.

I simply did this and it worked.  I changed the permissions on the folder using the recursive option/switch (changes the permission of all files withing).

```
sudo -r chmod 777 "folder location and name"
```

or it was 

```
sudo chmod -r 777 "folder location and name"
```

I can't remember.  I had to try 3 different variats to get it to work..lol.  Have a go yourself and try it out.

FAT32 format does not allow you to set permission. It does not have that feature. It is successful if you have ext3 or ext2 format (and mightbe NTFS). kramer65 external drive is in fat32. My method or enigmr's can give you access rights to the whole drive.

---

### Post by kramer65 on 2008-04-12
> **erginemr said:**
>  "please post the outputs of the following four commands from the terminal:"

```
sudo fdisk -l
```

Schijf /dev/sda: 200.0 GB, 200049647616 bytes
255 koppen, 63 sectoren/spoor, 24321 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0xc8afc8af

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *           1        5216    41897488+   7  HPFS/NTFS
/dev/sda2            5217       19898   117933165    f  W95 Uitgeb. (LBA)
/dev/sda3           19899       20166     2152710   82  Linux wisselgeheugen
/dev/sda4           20167       24321    33375037+  83  Linux
/dev/sda5            5217       19898   117933133+   b  W95 FAT32

Schijf /dev/sdc: 500.1 GB, 500107862016 bytes
255 koppen, 63 sectoren/spoor, 60801 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x44fdfe06

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdc1               1       25063   201318516    c  W95 FAT32 (LBA)
/dev/sdc2           25064       60801   287065485    f  W95 Uitgeb. (LBA)
/dev/sdc5           25064       50126   201318516    b  W95 FAT32
/dev/sdc6           50127       59414    74605828+   7  HPFS/NTFS
/dev/sdc7           59415       60801    11141046   83  Linux


```
blkid
```

/dev/sda1: TYPE="ntfs" UUID="525414E75414CF99" LABEL="Windows" 
/dev/sda3: TYPE="swap" UUID="6ca3c72d-f1cf-44b0-ae3d-6878c5c88dab" 
/dev/sda5: LABEL="COMP" UUID="45CF-5410" TYPE="vfat" 
/dev/sdc1: UUID="22D4-42BC" TYPE="vfat" SEC_TYPE="msdos" LABEL="MULTIMEDIA" 
/dev/sda4: LABEL="Ubuntu" UUID="a1553ffe-8b28-4f5f-bfd9-a945dbdfcc14" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: LABEL="ANDERS" UUID="462B-A083" TYPE="vfat" 
/dev/sdc6: UUID="5E3037003036DEA9" LABEL="Backup" TYPE="ntfs" 
/dev/sdc7: LABEL="Site Shite" SEC_TYPE="ext2" TYPE="ext3" 


```
ls -l /media
```

totaal 144
drwx------ 11 ricam root    32768 1970-01-01 01:00 ANDERS
drwxr-x--- 71 root  admin    4096 2008-04-12 11:08 Backup
drwxrwxrwx  1 root  root    20480 2008-04-10 09:34 Backup_
lrwxrwxrwx  1 root  root        6 2007-03-07 17:56 cdrom -> cdrom0
drwxr-xr-x  2 root  root     4096 2007-03-07 17:56 cdrom0
drwxr-xr-x  2 root  root     4096 2007-03-07 17:56 cdrom1
drwxr-xr-x  2 root  root     4096 2007-03-07 17:56 hda1
drwxrwx---  8 root  plugdev 32768 1970-01-01 01:00 hda5
drwx------ 10 ricam root    32768 1970-01-01 01:00 MULTIMEDIA
drwxr-xr-x  2 root  root     4096 2007-04-19 17:07 My Book
drwxrwxrwx 21 root  ricam    4096 2008-03-20 19:05 Site Shite
drwxr-xr-x  2 root  root     4096 2007-04-17 18:33 usbdisk


```
cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4
UUID=a1553ffe-8b28-4f5f-bfd9-a945dbdfcc14 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=F88C42558C420F16 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=45CF-5410  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=6ca3c72d-f1cf-44b0-ae3d-6878c5c88dab none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0


Does that help?

---

### Post by erginemr on 2008-04-13
I am sorry, but as someone who never used an external hard drive before, I have to retreat from the battle field. I hadn't pay attention to the fact that you were trying to configure an external hard drive. :?

I could as well suggest you to edit your "/etc/fstab" file and add lines for "sdc#" partitions with correct parameters, but this would be wrong and might wreak havoc on your system. The problem with fstab is that; it configures fixed volumes mounted at start up, but you are connecting/disconnecting your external hard drive at will, and want that functionality I guess. So, this issue settles in udev's territory.

AFAIK, external storage devices are handled by a background daemon called **udev** (dynamic device management), which has a predefined set of rules stored under "/etc/udev/rules.d". 

There are several posts regarding udev:
[http://ubuntuforums.org/showthread.php?t=378663&highlight=udev+bind+mount](http://ubuntuforums.org/showthread.php?t=378663&highlight=udev+bind+mount)
[http://ubuntuforums.org/showthread.php?t=665606&highlight=udev+external](http://ubuntuforums.org/showthread.php?t=665606&highlight=udev+external)

and advanced tutorials on how to configure it:
[http://gentoo-wiki.com/HOWTO_Customizing_UDEV](http://gentoo-wiki.com/HOWTO_Customizing_UDEV)
[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

Any ideas from external hard drive owners are welcome...

---


---
title: "Using usb ext HD - is EXT3 better or leave FAT32"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by Tony3286 on 2007-08-17
I installed Ubuntu last week and love it! I've tried to read the forum concerning formatting but am a little confused. I have a dual boot system on my Windows XP machine and formatted it to ext3 for Ubuntu on one partition. Everything works fine. 

I have now purchased a WD external USB HD thats formatted with FAT32. From my reading in the forum,
Ubuntu can read and write to FAT32. I'm using this hard drive for a backup for both Windows and Ubuntu.
Can I leave the entire drive as FAT 32 or should I partition the new drive and have one partition as FAT32 for Windows and EXT3 for Ubuntu? Thank you for your patience.

---

### Post by stchman on 2007-08-17
> **Tony3286 said:**
> I installed Ubuntu last week and love it! I've tried to read the forum concerning formatting but am a little confused. I have a dual boot system on my Windows XP machine and formatted it to ext3 for Ubuntu on one partition. Everything works fine. 

I have now purchased a WD external USB HD thats formatted with FAT32. From my reading in the forum,
Ubuntu can read and write to FAT32. I'm using this hard drive for a backup for both Windows and Ubuntu.
Can I leave the entire drive as FAT 32 or should I partition the new drive and have one partition as FAT32 for Windows and EXT3 for Ubuntu? Thank you for your patience.

Leave it all FAT32, unless you have large files (>4GB).  If that is the case then you can go with an NTFS as you can use the ntfs-3g package.

---

### Post by diatribe on 2007-08-17
yes you are better off leaving it all as fat32

---

### Post by Tony3286 on 2007-08-17
Thank you so much for your quick reply. I have found Sbackup for Ubuntu and wanted to make sure I could designate the USB hard drive with FAT 32 for the backup and not have any problems  with either writing to it or in an emergency being able to use the backup

---

### Post by AndyCooll on 2007-08-17
Depends on whether you're going to want to access the files via Windows. If you are then you're probably best staying with FAT32 or choosing NTFS. If that ain't an issue then ext3 is a good choice.

:cool:

---

### Post by Tony3286 on 2007-08-17
If Fat32 can be used by Windows and Ubuntu, why would you use EXT3? Is  it a better file format?

---

### Post by logos34 on 2007-08-17
> **Tony3286 said:**
> If Fat32 can be used by Windows and Ubuntu, why would you use EXT3? Is  it a better file format?

Yes.  As stated above it has a 4 gb file size limit, and it also fragments much more easily.  Ext3 is much more resilient in addition--it's basically ext2 with journaling added, which means that it hardly misses a beat after a poweroutage, just bounces bounces right back.  Personally I'd consider formatting the entire thing ext3 and getting **fs-driver** for windows to add read+write support. At some point you may want to backup large images of partitions.

---

### Post by Tony3286 on 2007-08-17
Thanks so much to everyone for their input! 
Not only have I found Ubuntu an unexpected pleasure to use, but everyone on the forum has  been so great in helping with any problem!

Thanks again!

---

### Post by hyper_ch on 2007-08-17
you could install ext2/3 drivers in windows so you can read/write the external drive if you format it to ext3

---

### Post by Tony3286 on 2007-08-17
Since the USB is for backing up , if I installed those drivers in Windows that you mentioned, would I be able to save a picture from Windows to the USB drive, thats formatted with EXT3 and then pull that picture back into Windows and use it in Picture it, a Windows program?
Believe me, this Windows thing is going to be temporary! As soon as I find similar programs to work in Ubuntu - I'm saying Bye Bye to Windows!

---

### Post by hyper_ch on 2007-08-17
yes, the ext2/3 drivers will allow you from windows reading/writing to it...

[http://www.fs-driver.org/](http://www.fs-driver.org/)

And that way you can still make use of the linux user/group/world settings.

Oh well, don't rush to get rid of windoze... I still have XP installed because there's a few things I need directx9 ;(

---

### Post by Tony3286 on 2007-08-17
I'm definitely going to check it out! Thanks!

---

### Post by dansen926 on 2007-08-31
Thanks everybody for their input! This was really helpful in deciding how to format my external USB drive.

If only I could get DirectX 9 to work in Linux... :)

---

### Post by dansen926 on 2007-08-31
> **stchman said:**
> Leave it all FAT32, unless you have large files (>4GB).  If that is the case then you can go with an NTFS as you can use the ntfs-3g package.

Does the ntfs-3g package support read+write access very well? I've heard horror stories about NTFS drives getting messed up, especially when the Windows OS I am running is Vista.

---


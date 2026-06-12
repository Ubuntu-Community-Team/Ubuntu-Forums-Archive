---
title: "EXT2 file system for XP help"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by Cornbreadly on 2006-07-21
I am trying to copy some files I put on my linux HD back to my new XP install HD.  I thought I would be able to use [this file system ext]("http://www.fs-driver.org/") but it doesnt seem to work.  It is registering my linux HD as FAT.  I can't see aything on the drive.

Is it not reading it correctly?

Do I have to go in under Ubuntu and change permissions?

---

### Post by moshuptrail on 2006-07-21
I'm not sure I understand what you are trying to do.  If the following doesn't help, post back and re-explain what you're trying to do.

I dont believe Windows XP supports ext2 file systems. So if you are running XP I'm not sure what it will do with an ext2 partition, but I doubt it will be good.  

Does anyone know what XP will do with an ext partition?  Will it recognize it as FAT for example?

Linux supports multiple filesystems, including NTFS (although readonly) so a linux system will be able to mount and navigate an NTFS partition.

---

### Post by Sef on 2006-07-21
> I dont believe Windows XP supports ext2 file systems.

XP does support ext2 and ext3.

> I am trying to copy some files I put on my linux HD back to my new XP install HD. I thought I would be able to use this file system ext but it doesnt seem to work. It is registering my linux HD as FAT. I can't see aything on the drive.

Which os is reading the partition as FAT?

---

### Post by qyot27 on 2006-07-21
> **moshuptrail said:**
> I dont believe Windows XP supports ext2 file systems. So if you are running XP I'm not sure what it will do with an ext2 partition, but I doubt it will be good.

Does anyone know what XP will do with an ext partition?  Will it recognize it as FAT for example?
It supports ext2/3 if you've installed a system driver for it, like the one linked to in the first post.  I dunno if SP1 or SP2 have integrated support for them, but I seriously doubt it.  Again, system driver.

My guess would be either A) Linux was installed to a FAT partition rather than ext2/3, or B) the IFS driver isn't set up correctly to read from the drive yet (if you need to set the drive letter, etc. - just check in Control Panel, there should be a place that says 'IFS Drives', which would be where you can modify those settings).

---

### Post by Cornbreadly on 2006-07-21
Sorry, I could have been more clear in my descriptions.

I love Ubuntu.  I installed it last night, my first linux distro, and I have already learnt so much.

I took to Ubuntu so well in fact that I decided to reinstall my XP onto my other HD.  It was so cluster-%&%^%&! that it took minutes to boot anyways, it was about time.  So I copied pics and other important docs to my Linux HD, and reformated the other HD for a clean install.  I want to keep it for gaming, DVD back-ups, and my wife.  

Now I am trying to use this file extension program, IF2, so that it will be easy to get the files back over to my XP HD.  From my understanding, Ubuntu does not have write capability on my XP HD.  And if it did, it might corrupt the data, which is a risk I dont want to take.

So here I am, in XP, trying to copy important files back over to my new XP install.  The Linux HD is being displayed in XP as a FAT HD, and my XP HD is NTFS. The Any help is appreciated.

---

### Post by Sef on 2006-07-21
Did you set the ext2 up as a separate partition?  If you did then both XP and Ubuntu should be able to read and write to it.


> Ubuntu does not have write capability on my XP HD. And if it did, it might corrupt the data, which is a risk I dont want to take.

NTFS is proprietary file system.  There are some tools now that can write to it, but not something I would trust at the moment.

---

### Post by Cornbreadly on 2006-07-21
> **Sef said:**
> Did you set the ext2 up as a separate partition?  

Im not sure I know what you mean...

In My Computer in XP, I display 3 HDs.  Two FAT's, one just over a gig partitioned on the same as the other FAT with ubuntu installed.

The other is my XP NTFS HD.

I now have another problem.  I just installed GAG, a [URL="http://gag.sourceforge.net/"]graphical boot manager
[/URL].  After i reinstalled XP, my PC wouldnt let me get into Ubuntu so I thought this would work.  I set it up very nice and pretty, but now it is finding a bad or invalid boot sector when I try to load Ubuntu.

Do I have to reinstall Ubuntu?  If I do, I just have to rescue those files.  But is there an easier way to fix this?  Or did my XP re-install overwrite something it shouldnt have?

---

### Post by moshuptrail on 2006-07-21
Sorry - I didn't catch that link.

So you are running XP and trying to get the files back from the ext2 drive..
What does the IFS drives icon in control panel say about your Linux partition?  In the screenshots at the link it shows ext2 drives as simply, "Linux".  What part of XP is showing the partition as FAT?  I'm very suspicious that either the driver is not working, is configured incorrectly, or for some other reason is not working.  That would explain why XP recognizes the drive as FAT and you cant see any files.

---

### Post by catlett on 2006-07-21
Did you install the ext2 driver from the link? You have to install the driver using the installer exec. Then you have to give the partitions a drive letter.
It will walk you through a wizard in the beginning but if you installed without assigning a drive letter you have to enter the ex2fs configurer.
It will be in the control panel in XP. It is easiest to find when you switch to classic view.
The partitions shouldn't have been affected by XP. Only 1 of your 2 Ubuntu partitions will have any data on it anyway. If you let Ubuntu create a default configuration, you will have 2 partitions. One will be formatted as swap. This is a place for virtual ram and will not have any data on it from your ubuntu install. The other will have all of your ubuntu install.
Check that the driver is installed. You will know because in My Computer the ubuntu partitions will have an icon next to your XP icon.

If there is an issue and you think you have to reinstall, you can always use the live cd to recover the data. It is a simple process to mount the partition in the live session and then copy the data out.

---

### Post by Cornbreadly on 2006-07-21
> **Sef said:**
> Did you set the ext2 up as a separate partition?  If you did then both XP and Ubuntu should be able to read and write to it.




NTFS is proprietary file system.  There are some tools now that can write to it, but not something I would trust at the moment.

> **moshuptrail said:**
> Sorry - I didn't catch that link.

So you are running XP and trying to get the files back from the ext2 drive..
What does the IFS drives icon in control panel say about your Linux partition?  In the screenshots at the link it shows ext2 drives as simply, "Linux".  What part of XP is showing the partition as FAT?  I'm very suspicious that either the driver is not working, is configured incorrectly, or for some other reason is not working.  That would explain why XP recognizes the drive as FAT and you cant see any files.

In the IFS driver in the Control Panel in labels the small partition as FAT, and the other as Linux.  The XP HD is NTFS.

In the My Computer, right offf the start button, the partitions are labeled as FAT systems.

As far as installing the IFS driver, I downed the exe from the site, installed it and changed the drive letter.  No wizard popped up or anything.  Should I reinstall the driver?

As far as saving my Ubuntu install, it can be accomplished through the Live CD with no data loss?

---

### Post by Cornbreadly on 2006-07-22
OK, I have been able, with a different driver, to see the first level of files on my Linux HD in XP.

One Victory... a few more to go.

Now onto the broken Linux boot sector.  Since I learned from Catlett that I could just boot up my live cd to browse around the broken Ubuntu install, I have more hope.  

I am trying to save some windows files I backed up onto my Linux HD when I reinstalled XP.  Now I want to put them back on my XP HD.  I backed those files up to my Ubuntu desktop when it was working, thinking that would be the easiest place to work with them because of my Noob status.

Now since that Ubuntu install is down, but I can still navigate my Linux files withthe live cd, what is the best way to get those files to my XP HD, so that I can reinstall Ubuntu?

---

### Post by Cornbreadly on 2006-07-22
I forgot to say that I can't find those files because i don't know where to look.  I have been poking around in usr/share/ ???  I saved them to my desktop.

I think that is correct but I am in XP now.

---

### Post by catlett on 2006-07-22
If you are in xp and can see your ubuntu partition with the drivers, this is where to look for the desktop.
Double click on the icon and it should have a lost and found folder and a folder with your user name on it as well as the trash folder. Open the username folder and look for the Desktop folder that is spelled with a capital D. That is your ubuntu desktop.
To browse it in thge live cd you will have to mount it. To mount it you will have to know which partition it is on. To find out that enter this command ```
sudo fdisk -l
``` The partition you want is the linux partition that is marked with *. Your windows partition will also have a * but it wil be an ntfs partition.
Once you know that you can mount it with these commands (for the sake of example I will use /dev/hda2).
```
sudo mkdir /media/ubuntu
```
```
sudo mount /dev/hda2 -t ext3 /media/ubuntu
``` An icon should appear on your desktop with the partition. If it doesn't, browse to the file by selecting Places<Computer<Filesystem Select the media foldere and the ubuntu folder is inside of that folder.

---


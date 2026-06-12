---
title: "format usb drive"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by holiday on 2006-06-10
I'm running 5.10 and want to use a LaCie d2 usb drive. 

When I plug it in it comes up in Nautilus. Disk information tells me it's NTFS, but even root can't write to it. Read Only volume.

I want to use this for video files.

I suppose I should format it?

Where can I find information on how to use this drive? 

I've googled on it and find a lot of irrelevant stuff. I need really newbie information here.

---

### Post by Jagot on 2006-06-10
Linux cannot write to NTFS.  If you want to use it with Linux then you need to format it as either FAT32 (which can be read and written to by pretty much any operating system), or EXT3 if you plan on just using it for Linux.  Bear in mind that FAT32 has a limit on the size of files which is about 4GB, so this might not work well if your video's are huge.

You can format using Gparted which is in the repos - you will be able to get it in Synaptic, or by typing i nterminal:

```
sudo aptitude install gparted
```

You can find out more about Gparted here:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by FryerFox on 2006-06-10
Actually, Linux can write to NTFS ([http://wiki.linux-ntfs.org/doku.php?id=ntfsmount](http://wiki.linux-ntfs.org/doku.php?id=ntfsmount), but if it's a flash-disk, I strongly recommend you format it to FAT32.

The previous poster pointed to gparted, which is a relatively simple tool to use. Just make sure you are formatting the right drive!

---

### Post by zugu on 2006-06-10
Alternatively, you could plug the drive in a Windows XP computer, wait for it to be discovered, right click it in My Computer, choose Format, specify FAT32 in the Filesystem box and click Start. In no time you'll have a FAT32 drive ready to be used under both Ubuntu and Windows and a variety of other OS, just as Jagot said.

---

### Post by holiday on 2006-06-10
Thanks. I formatted ext3 using System.Administration.Disks. I had to disable the drive to access the format button and then select ext 3. I then created a directory, chowned it to my user, and hey presto I'm writing to the drive. 

Thanks for your help.

---

### Post by holiday on 2006-06-10
Well ok now this is weird.

I have Breezy on my laptop and on my desktop. Initially I formatted the drive from the laptop and copied some files onto it. 

Then I plugged it into my desktop and all I could see was Lost&Found. 

So Ok I reformatted from the desktop, copied some files, plugged it into my laptop and all I see is Lost&Found. 

What's going on?

---


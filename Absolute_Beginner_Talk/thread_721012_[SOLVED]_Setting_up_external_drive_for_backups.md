---
title: "[SOLVED] Setting up external drive for backups"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by mgbridges on 2008-03-10
I've got a 500Gb USB hard drive which I previously used for backups on my Windows machine. It currently contains 2 partitions which I can see if I hook it up to my Ubuntu desktop.

What do I need to do to re-partition and format the drive for use as a backup drive for my Ubuntu system? At the moment I'm only planning to use it to backup the data directories on my Ubuntu system.

Thanks,

Martin

---

### Post by Presto123 on 2008-03-10
It's quite simple. Go into your Add/Remove under the Applications menu, make sure that the top-right drop-down menu is selected for "All Available Programs" and search for "gparted". It will be the program listed as "Gnome Partition Editor"; install that program by selecting the box and hitting the "Apply" button.

Follow up after this is done...

---

### Post by mgbridges on 2008-03-10
OK, that bit is done, but I'm still not clear what I should be doing next. Apologies - although I've had Ubuntu installed for about 4 or 5 months now I haven't really got comfortable with it yet.

Cheers,

Martin

---

### Post by Presto123 on 2008-03-10
From there, go into System/Administration/Gparted (you will have to enter your password). 

A partition-editing GUI will pop up and at the top-right again, you will see your drives listed. MAKE SURE YOU HAVE SELECTED THE RIGHT ONE! (Should be pretty simple with it being 500gb)

Right click on the drive where it shows the filesystem type (IE: FAT32 or NTFS, etc.) and select from there "unmount". You can then right click again after it unmounts the drive and select "Format To" and select the filesystem you want to format it to (I choose FAT32 for my 320gb so that it can be read by BOTH NTFS and Linux partitions).

That should get you there.

---

### Post by mgbridges on 2008-03-10
Thanks - sounds straightforward, I'll give it a go a bit later.

In terms of the filesystem to use, I've seen suggestions on other threads to use ext3 (I believe there's a driver that will let a Windows machine read this) - what are the advantages/disadvantages of using FAT32 opposed to ext3?

Thanks,

Martin

---

### Post by Presto123 on 2008-03-10
> **mgbridges said:**
> Thanks - sounds straightforward, I'll give it a go a bit later.

In terms of the filesystem to use, I've seen suggestions on other threads to use ext3 (I believe there's a driver that will let a Windows machine read this) - what are the advantages/disadvantages of using FAT32 opposed to ext3?

Thanks,

Martin

Someone else will be better of explaining this. I've HEARD that FAT32 isn't as good for some weird reason, like it not being very efficient. But, hey, it works for me.

I'll leave this one open for discussion, lol.

---

### Post by Presto123 on 2008-03-10
One thing I will say...to make sure what the mountpoint is for your external, right click on it and select "Properties" (I would rather you see for yourself what it is, just to reduce the chance of errors). From there look at the "Volume" tab and find the Mount Point. Remember what it lists and then go into your Terminal and type in:

```
gksudo gedit /etc/mtab
```

And find the line that has the same thing listed...it will show you what the drive volume is.

So, for example, in my "Volume" tab, it lists:
**Mount Point**: /media/disk

I find that line in mtab as:
/dev/sda1 /media/disk vfat
(Above, it lists first: drive, second: mountpoint, third: filesystem)

There I have it, my drive is /dev/sda1.

Again...this is just to be on the safe side. You would probably have NO issues without doing this, but...*Shrugs*

---

### Post by mgbridges on 2008-03-11
OK, I've tried using gparted and had some problems. When I opened up the external drive in gparted it showed three existing partitions. I didn't see an option to Format anywhere. However, I was able to unmount the partitions and delete them, or so it seemed. One of them is still showing up in my file browser.

I then used gparted to create 3 new partitions but when I told it to apply the changes it failed. The output file is attached.

I wonder if this is to do with the fact that one of the partitions was previously used by Acronis backup software (when I had the drive connected to my old Windows machine). Perhaps this is making it un-deletable? Any thoughts.

Martin

---

### Post by mgbridges on 2008-03-11
Well, not quite sure how I did it but I've managed to create 3 partitions on the external drive. Having problems with write access but I'm dealing with that in another thread, so I'll close this one off.

---


---
title: "Persistent Live CD Settings to HD"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by quake120 on 2007-02-25
Hi all. First time post here. 
I'm using an Edgy CD as a LiveCD on my g/f's laptop. I tried to install it to her hard drive, but installed the bootloader on the wrong partition :(. Long story short, I ended up having to completely format her hard drive (long story) so now she doesn't want me to try it again. Due to that fact, I am stuck using the LiveCD for the time being.
I don't really like having to install Adobe Flash Player and change my themes each time I start it up so I want a way to save my settings. 
I have read various things around the forums and Google about saving the desktop settings to a USB thumbdrive, but on every one I found, it seems to have required the thumbdrive be formatted with ext2/3 which I couldn't do since I use that thumbdrive for Windows stuff too. 
So... What I need to know is if there is a way to save the settings to a FAT32 partition on either the USB drive or the laptop's hard drive. 

Thanks all in advance!

---

### Post by skyhopper88 on 2007-02-25
You can read/write to ext2/3 on Windows with
[http://www.fs-driver.org/](http://www.fs-driver.org/)

Only downside is since it's external, the drive letter will stay visible even when the device isn't plugged in.

---

### Post by quake120 on 2007-02-25
> **skyhopper88 said:**
> You can read/write to ext2/3 on Windows with
[http://www.fs-driver.org/](http://www.fs-driver.org/)

Only downside is since it's external, the drive letter will stay visible even when the device isn't plugged in.

Ah, the only issue with that is that I use my thumbdrive on 140+ computers (I do IT for a company). 

I do have an external hard-drive. Could I just use the partitioning tool to chop off a small amount of free-space and convert it to ext2/3?

---

### Post by tagra123 on 2007-02-27
See my post.

You can use gparted using the live cd

[http://ubuntuforums.org/showthread.php?t=372193&highlight=persistent](http://ubuntuforums.org/showthread.php?t=372193&highlight=persistent)

---


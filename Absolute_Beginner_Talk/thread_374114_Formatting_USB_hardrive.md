---
title: "Formatting USB hardrive"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by yme on 2007-03-02
Hello:

I have a 160Gb cased harddrive which connects via USB and which came from the shop ready formatted (I'm presuming NTFS). 

The read-only problems with working with NTFS from Ubuntu (sometimes it is read-only sometimes not!) is getting too much of a pain. 

How do I reformat it as something Linux compatible (ext2, ext3)? I need really clear instructions as I don't want to wipe the machine I am working from!

me!

---

### Post by jethro10 on 2007-03-02
Install gparted via synaptic.

plug in usb drive, wait till it recognised/mounted. EDIT - Oops, see post below, unmount disk first. (cant gparted unmount a disk by right clicking it?)

Gparted in system menu, you'll see the drive there.

format away.

J

---

### Post by xyz on 2007-03-02
You need a LiveCD.  And sooner or later, you may need it to accomplish other things,too. One of them is [GParted.]("http://gparted.sourceforge.net/")
It is straightfoward. Come back and ask questions if you run into problems.

---

### Post by StefanoCole on 2007-03-02
To be able to format it the hard disc must be plugged but unmounted.

Stefano

---

### Post by yme on 2007-03-02
Is there no tool that comes as part of the Dapper package that I can use? It takes up 7.5Gb on my harddrive so lord knows what that is if not such stuff. I've had very little success with downloading add on stuff.

---

### Post by ThrobbingBrain66 on 2007-03-02
> **yme said:**
> Is there no tool that comes as part of the Dapper package that I can use? It takes up 7.5Gb on my harddrive so lord knows what that is if not such stuff. I've had very little success with downloading add on stuff.

Do what jethro10 advised.

Go to System > Administration >Synaptic Package Manager

Search for gparted and install it.  Then I believe gparted can be found in system > Administration

Make sure the external drive is plugged in to the usb port but NOT mounted.  You will then be able to format it as fat, fat32, ext3, etc.

---

### Post by yme on 2007-03-02
OK! I just managed to find that if I open System > Adminsitration > Disks. It allows me to format. I tried with a 1Gb USb pendrive that had been a bit messed up (showed only 512Mb free when there was nothing on the disk at all) and it came up fine.

I'll try the bigger drive in a mo. I guess maybe this is GParted although it doesn't say so ...

---

### Post by yme on 2007-03-02
It seems to work OK both on the 1GB USB and on the 160Gb hardrive. Only thing is that although the disk utility shows the USB pen drive as 1GB by the time it is plugged in there is only 857 available. 78Mb goes in a swap partition: is that necessary? In both cases a 'lost and found' folder appears. Why is that?

---


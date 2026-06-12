---
title: "Installation stuck at 5%"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by TSPetersInc on 2007-08-10
Hello everyone. I'm pretty new to the whole Linux thing so far but I already have a question or problem. I have just formatted an additional internal hard drive on Windows XP and am trying to install Ubuntu v7.04 on the formatted disk. It's been about 2 hours, maybe more, that the installation is remaining on 5% "on "Creating ext3 file system for / " My hard drive is active and deffinitely doing something since it will occasionally communicate with the CD drive. (The LED hard drive light is constantly blinking) So I assume it has to be doing something at least. I just can't figure out whats going on here. If anyone could please lend me a hand I would greatly appreciate it! Thank you so much!

---

### Post by Outrunner on 2007-08-10
How large did you make the / partition? Ext3 filesystems usually take a bit to be created but 2 hours is definitely a long time(500GB partition, maybe?)

---

### Post by TSPetersInc on 2007-08-10
Its only a 20gig hard drive, but this is an older system I am running. Its only an Anthlon XP1800 with 256MB of ram. I am wondering if that could be it, or if there is some issue when formatting a harddrive a certain way. I dont really know..

---

### Post by RomeReactor on 2007-08-10
Hi. Some people experience problems during installation in systems that have 256 MB ram or less; if you know your system specifications, please post them. You may need to download an Alternate CD.

---

### Post by forestpixie on 2007-08-10
I would check the cd, did you check the md5sum - and how much ram do you have

edit too slow :)

---

### Post by TSPetersInc on 2007-08-10
I dont know what a md5sum is. So no I diddn't check that.

---

### Post by TSPetersInc on 2007-08-10
The weird thing is, this isnt the first time I installed Ubuntu on this PC. The first few times it installed faster but wound up having errors later on like, ""/dev/hfc1 contains a file system with errors" or "Error reading block count xxxx (Attempt to read block from file system resulted in short read) while doing inode scan. Ignore error? <y>   Force rewrite? <y>"

---

### Post by RomeReactor on 2007-08-10
It probably has to do with the amount of RAM in your system; you might want to download the [Alternate CD]("http://www.ubuntu.com/getubuntu/download") (scroll down to the end of the page, and check the box that reads **Check here if you need the alternate desktop CD**, just below the green **Start Download** button.

---

### Post by forestpixie on 2007-08-10
it's ok, I guess it's ram related though - post your specs though 

here are the hash checks - [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

have a look here as to how to go about checking - [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

Edit - as the man/woman says go with the alternate install - but it wouldn't hurt to check out the links to make sure your download is ok.

---

### Post by TSPetersInc on 2007-08-10
Well would it still eventually complete the installation with the given amount of RAM I am using? The system is still blinking away and I don't usually feel comfortable aborting an active system.

---

### Post by RomeReactor on 2007-08-10
There's no guarantee that the installation process will eventually finish; likely, it won't. You'd be safer installing through the  Alternate CD.

---


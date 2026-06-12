---
title: "Format NTFS Drive into EXT3"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2007-01-09
I have a drive attached to my Ubuntu Edgy which is NTFS. How do I reformat it so it is EXT3. I don't have any data on it. I can't figure out how to format it. Thanks!

---

### Post by taurus on 2007-01-09
What's the output of this command?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by meng on 2007-01-09
If you know the device ID for the partition, e.g. /dev/hda1, then the command should be
mke2fs -j /dev/hda1
(make sure you get the correct device ID, else you're toast!)
You may need to preface the command with 'sudo', I've never done this in Ubuntu before.

---

### Post by amitroy5 on 2007-01-09
Is there a GUI for formatting?

---

### Post by taurus on 2007-01-09
You can try gparted!

---

### Post by jvc26 on 2007-01-09
You can get Gparted on the ubuntu live cd, and also a Gparted live cd- a very useful tool!
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
Il

---

### Post by meng on 2007-01-09
I'm a big fan of GParted and particularly of the GPartedLive CD, but seriously, I can't see the point of downloading that MERELY to do a 'sudo mke2fs -j' command. On the other hand, I heartily recommend downloading GParted Live CD for future contingencies!

---

### Post by taurus on 2007-01-09
You can install gparted with synaptic/apt-get/aptitude.

---

### Post by shareMenaPeace on 2007-01-11
Anyone kind enough to tell me which the command is to install gparted?

Thanks

---

### Post by shareMenaPeace on 2007-01-11
Ok i found it

System / Administration / Synaptic Package Manager
than search for gparted and install it with the additional libs.

---

### Post by amitroy5 on 2007-01-12
Or, if you prefer the terminal, type in:

sudo apt-get install gparted

---

### Post by bobby.hawk on 2007-09-17
Hello,

I purchased a Maxtor One-Touch-III 500 USB drive.  It came formatted with NTFS but I would like to use it under the EXT3 format.  Can a reformat also be done from the graphical interface?

Bob

---

### Post by amitroy5 on 2007-09-20
Yes, it can.

Go to the terminal. Type in:

sudo apt-get install gparted

gparted will tehn appear in one of the menus.

---

### Post by bobby.hawk on 2007-09-22
> **amitroy5 said:**
> I have a drive attached to my Ubuntu Edgy which is NTFS. How do I reformat it so it is EXT3. I don't have any data on it. I can't figure out how to format it. Thanks!

Well after a lot of messing around I figured how how to format my external drive.  I am actually using a cool little linux NAS device from Linkys...NSLU2.  

[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1119460471050&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1119460471050&pagename=Linksys%2FCommon%2FVisitorWrapper)

Deep down inside the Administrative features it actually helps you format a new drive.  

Done!

---


---
title: "Paritioning drives"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by sirisaac87 on 2008-03-31
I am completely partitioning my harddrive I am getting ride of windows, and want a fresh start with ubuntu.  I will have to partitions one for the system and another for music.  Should I partition the drives in fat32 or ext3 or ext2? What is the difference?

---

### Post by tangibleorange on 2008-03-31
Well the default for Ubuntu is ext3. I would recommend this for both your partitions unless you have another specific reason for using another. ext3 is just a newer version of ext2, and fat32 is not a good choice as it requires regular defragmentation in my experience.

go with ext3 :guitar:.

---

### Post by shoot2kill on 2008-03-31
if you are going LINUX ONLY, then i would say ext3, it is much better/faster/secure than FATxx

if you may be using windowze again, then think about using FATxx

---

### Post by abhiroopb on 2008-03-31
You have a few options.

1. Put in an ubuntu liveCD and it will partition everything automatically (basically it will create ONE ext3 partition). Then you can use the built-in partition editor in ubunut (gparted) to resize the partition and add the extra partition for music, etc.

2. When installing with the liveCD you can set up the partition yourself. Ideally you should do a small-ish partition for system (or "/"), a large-ish partition for /home (your documents), and leave some unformatted space for the music.

Don't use fat32, nowadays it is almost solely used to transfer files between different OSes as it can be read/write by almost all. ext3 is stable, fast and reliable, I suggest you use this for all 3 partitions (for point 2 above).

I personally would do point 1, as it is hassle free, and then resize the partition to add space for music.

---

### Post by sirisaac87 on 2008-03-31
What should I use as the mount point for these drives? One is for the system and all its files and the other is for my music?

---

### Post by shoot2kill on 2008-03-31
the mount point for your install would be root or ' / '

---

### Post by sirisaac87 on 2008-03-31
Would root or '/' be the mount point for both drives??

---

### Post by shoot2kill on 2008-03-31
i would use / as the mount point for the install, (and if following abhiroopb's info, use /home as the mount point for your documents) and then install ubuntu and format your music partition afterwards with gparted..

---

### Post by sirisaac87 on 2008-03-31
Im in Gparted, but all the options to change the partition are greyed out..am I supposed to unmount the drives before I do anything? How do I go about changing the size of the drive?  I attached the screenshot of what my screen looks like

---

### Post by sirisaac87 on 2008-03-31
Is there another program that I should be using?? or is gparted the best option?

---

### Post by sirisaac87 on 2008-03-31
I tried to open gparted and got a message that said "Since GParted can be a weapon of mass destruction only root may run it."  What does this mean

---

### Post by Moop on 2008-03-31
Gparted is a good option. Yes you need to unmount the partitions before you can do anything with them. 

To be root means you need to put sudo before gparted, if you were opening it in terminal. ```
sudo gparted
```

You need to boot from a live cd and not use gparted from within Ubuntu if you're going to do something with the partition Ubuntu is on.

---

### Post by Duck2006 on 2008-03-31
You can use the live cd of gparted.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

or parted magic.

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

To partition the drive.

---

### Post by sirisaac87 on 2008-03-31
how much space should I set for the system or the root folder???

---

### Post by Duck2006 on 2008-03-31
For / root 10Gb I have 20Gb (but no home partition)
For swap 1Gb
For home what ever you like (if your going to have one)

---

### Post by abhiroopb on 2008-03-31
According to your HD you have about 110 gb of space. It depends on what you want to use the other space for.

About 10gb is MORE than enough (more than the root will ever need), 5gb is about a good amount. Basically this is where all your installed programs/basic ubuntu stuff/config files, etc will go. So it really depends. But I'd recommend 5gb.

---


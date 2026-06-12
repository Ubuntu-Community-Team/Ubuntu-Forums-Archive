---
title: "Cloning Harde Drive"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by ianb72 on 2007-10-26
Hi,
Is there any way I can clone my SATA hard drive, which presently has Fiesty on it to a IDE drive?

When I used windoze I used Norton Ghost is there a simular bit of software for Ubuntu, I've read about something called Partimage, would that do the job and is there an easy way of using it from the Live CD either Feisty or Gusty.

The reason I want to do this is I want to try out Gusty but the 64 bit version to see if I can still use all the software I am using in the 32 bit version of Feisty and  also see if it is any quicker.

Thanks
Ian

---

### Post by Pumalite on 2007-10-26
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by molly_001 on 2007-10-26
I've been using the dd command recently for a full-on bit-to-bit imaging of a hard drive partition (without compression).  It works very well for both NTFS (Windows) partitions and for ext2 partitions.  It also works for Vista partitions if you are careful to correct the image with linux command ntfs-resize.

---

### Post by Orbital75 on 2007-10-27
I pretty much have the same question here.  I have used Norton Ghost 2003 for
ages and now would like to use Ubuntu as my primary OS. I like the
peice of mind in knowing that I have a nice recent Bit for Bit copy of my OS sitting
right beside me in case something bad happens. All I have to do is put in the
Bootable DVD and we're back up just as we were in 5 minutes give or take 4 days
of recent data.  

So, My question would be is Partimage similar to Ghost? Can it make a Bootable
DVD or CD?  I understand you can back the image up to an external drive, which
is very nice but I'd like a nice quick and easy DVD solution.  I've also heard
of something called clonezilla, is this about the same or is it better?  Not trying
to hijack this thread, I figured this would help out.

Thanks

---

### Post by molly_001 on 2007-10-27
Orbital75,
 
I just wrote a nice long response to your questions but the browser logged me out before I could submit it.  grrrr .. lost the whole thing
 
Sum of it is:
 
Yes, you can copy partitions bit-by-bit to an optical drive without compression.
 
An excellent hard drive to hard drive copy utility is made by Western Digital (in its bootable Digital Lifeguard suite).  It is free and sold with their standalone new hard drives.  You might be able to download a bootable .iso of it from somewhere online.
 
I've asked in several linux forums about copying a hard drive partition to optical drive.  It is possible, and I can hunt down several forum responses (to my initial inquiry) for you, if you want.  I haven't taken the next step of trying out the method yet, although I routinely use the same command structure (dd command) to clone HD-to-HD.

---

### Post by Pumalite on 2007-10-27
[http://www.partimage.org/Partimage-manual_Usage](http://www.partimage.org/Partimage-manual_Usage)

---

### Post by HermanAB on 2007-10-27
You can also use clonezilla: [http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

---


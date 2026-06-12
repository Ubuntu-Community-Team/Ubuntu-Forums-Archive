---
title: "Partitioning question"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Big Tony on 2008-01-27
A friend of mine has convinced me to setup a dual boot on my Dell E1705 laptop running XP.  As I use this computer a lot for multiple important things, I am not ready to wipe it completely, and I would like to keep my current install of windows intact.  I have a 120 gig hard drive with 30 gig free.  I was going to allot 20 gig to Ubuntu.  I have run disk clean-up and defragmented the drive.  During the Ubuntu install when I have to choose how the partition is made I choose to use the largest consecutive free space but it gives me an error that there might not be enough free space on the partition.  My question is can I use the manual partition option to the same effect?  If so, when you select the "edit partition" option it asks you to give the size of the "new" partition, is this the actual new partition or the new size for the existing partition?

---

### Post by ubuntu-freak on 2008-01-27
> **Big Tony said:**
> A friend of mine has convinced me to setup a dual boot on my Dell E1705 laptop running XP.  As I use this computer a lot for multiple important things, I am not ready to wipe it completely, and I would like to keep my current install of windows intact.  I have a 120 gig hard drive with 30 gig free.  I was going to allot 20 gig to Ubuntu.  I have run disk clean-up and defragmented the drive.  During the Ubuntu install when I have to choose how the partition is made I choose to use the largest consecutive free space but it gives me an error that there might not be enough free space on the partition.  My question is can I use the manual partition option to the same effect?  If so, when you select the "edit partition" option it asks you to give the size of the "new" partition, is this the actual new partition or the new size for the existing partition?

 
I'd suggest doing it manually and create a storage partition. Let Windows have about 20-30gb, then let Ubuntu have 10gb for the root partition, 10gb for a seperate /home partition, 1gb for the swap partition and then the rest for a storage partition. 
 
That's how I would do it.
 
Nathan
 
P.S. Best not to mount the Windows partition. It really slowed down my boot into Ubuntu. That's another benifit of having a storage partition that both Ubuntu and Windows can use.

---

### Post by JoshuaRL on 2008-01-27
When the error comes up, does it let you continue or does it stop the process?

BTW, good job filling up 90gb of space.  Wow.

---

### Post by ubuntu-freak on 2008-01-27
Ouch! Just noticed you only have 30gb free. That's a lot of porn.
 
Could you transfer your files to an external drive so you can edit/add/resize your partitions?
 
Nathan

---

### Post by JoshuaRL on 2008-01-27
> **reassuringlyoffensive said:**
> That's a lot of porn.

... not that we think that's what's filling your HD.  It may be a super-massive collection of music.  Or a ton of ripped DVDs.  Or whatever.  But still, yeah.  

Are you sure you need all of that?  Because if you're a digital packrat then you have found heaven.  About 20,000 packages available through Synaptic.  And almost everything you find will be free.  You'd benefit with more space to Ubuntu.

BTW reassuringlyoffensive, you are aptly named.  :lolflag:

---

### Post by Paqman on 2008-01-27
> **JoshuaRL said:**
> 
BTW, good job filling up 90gb of space.  Wow.

Easily done. I have over 200gb on my NAS (it's downloading TV shows that does the damage). 

Thought I was being silly when I bought 320gb drives for it, now i'm beginning to wonder.

---

### Post by JoshuaRL on 2008-01-28
Yeah, I guess I'm just more frugal since I don't have that size HD.  But now that you mention it, the teradrives are looking pretty nice.

---

### Post by Big Tony on 2008-01-28
> **JoshuaRL said:**
> When the error comes up, does it let you continue or does it stop the process?

BTW, good job filling up 90gb of space.  Wow.

The error says "Either not enough space or the selected partition is not big enough"  and will not continue with that process.  It will only allow "Guided" with complete wipe, or manual.  I need to know if using manual will still wipe the drive and if the size allocation I give in the "edit partition" is the size of the new blank partition or the new size of the old partition.

BTW I record audio and work with high-res graphics for print for my band, and I probably do hold on to stuff a little long, but, I can't bear to part with it, and I am not completely ready to give up windows and Photoshop, as I am not used to GIMP yet.  You guys are going to get me in trouble w// my wife...:lolflag:

---

### Post by louieb on 2008-01-28
The thing about NTFS (the windows file system) is that performance start to drop after it gets about 70% full. At 80% full you will notice the drop. 

Really think its time for that external drive you've been cravening.  For  the safety of your data I don't think I would try to shrink your windows partition until you able  to store it someplace else during the install.

What I normally do  is use a partition editor like GParted (available or the [SystemRescueCd]("http://www.sysresccd.org/Main_Page")) and use it to shrink the XP partition. Then create the install and swap partitions for the Linux install. 

Then when installing Linux use the manual partition option and point it to you new partitions for / (root) and swap.
:guitar:Join the club. I'm always in trouble with the wife.

---


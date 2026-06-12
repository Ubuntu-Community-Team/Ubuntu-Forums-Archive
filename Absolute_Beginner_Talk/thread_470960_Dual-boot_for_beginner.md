---
title: "Dual-boot for beginner"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-06-11
Let me start of by saying i am a self admitted "noob" when it comes to linux in general.  I have been doing research and learning as i go.  I am trying to run a dual boot xp/ubuntu on a dell optiplex GX60: Celeron 2.00 Ghz, 1Gb ram, 40gb HD.  I am currently running xp and realize that dual-boot is a viable option.  I am wondering if there is a way i can install ubuntu on top of my current windows install so i dont have to format and re-install windows?

---

### Post by p_quarles on 2007-06-11
Yep, and it's very easy. 

You can install Ubuntu from the CD. When you get to the "partition the drive" menu, you should select "guided partitioning -- use partial disk." The gparted partition manager included on the live CD is very good, and makes it easy.

Before doing this, you should defrag the hard drive and backup any data. Most likely nothing will go wrong, but it's better to be safe.

---

### Post by LaRoza on 2007-06-11
By the time you read this, several others will have posted probably, but it was blank when I got here.

Dual-booting is very very very easy.

During the install, you will be given an option to resize a partition and install on the freed space, you select what size you want to free, and install. XP and Ubuntu will be in a menu when you turn on the computer, and you can choose what OS you want.

Defrag xp first to make it easier.

---

### Post by Inxsible on 2007-06-11
> **ITdrummer said:**
> Let me start of by saying i am a self admitted "noob" when it comes to linux in general. I have been doing research and learning as i go. I am trying to run a dual boot xp/ubuntu on a dell optiplex GX60: Celeron 2.00 Ghz, 1Gb ram, 40gb HD. I am currently running xp and realize that dual-boot is a viable option. I am wondering if there is a way i can install ubuntu on top of my current windows install so i dont have to format and re-install windows?
Yes you can. Use the LiveCD for Ubuntu. A program called GParted on it, will help you partition or resize your drive the way you want. Remember to defrag your Windows XP a couple million times :rolleyes: ;) --- before you start your Ubuntu installation.
 
For more info on partitioning and installing, check these links out:
[Partitioning]("http://ubuntuforums.org/www.psychocats.net/ubuntu/partitioning")
 
[Installing]("http://ubuntuforums.org/www.psychocats.net/ubuntu/installing")

---

### Post by Inxsible on 2007-06-11
> **LaRoza said:**
> By the time you read this, several others will have posted probably, but it was blank when I got here.
 
Dual-booting is very very very easy.
 
During the install, you will be given an option to resize a partition and install on the freed space, you select what size you want to free, and install. XP and Ubuntu will be in a menu when you turn on the computer, and you can choose what OS you want.
 
Defrag xp first to make it easier.
 
LaRoza, It was blank when I got to it too ;) :D. But you and p_quarles beat me to it :)

---

### Post by ITdrummer on 2007-06-19
> **LaRoza said:**
> 

During the install, you will be given an option to resize a partition and install on the freed space, you select what size you want to free, and install. 



How do i know how much size i will need to free? i have heard my swap partition should be double the size of my physical memory.?

---

### Post by ITdrummer on 2007-06-19
also, how many partitions should i create. Could someone please describe it to me as if i was computer illiterate. Because everywhere i go people are always like "oh just click here and do this and that"....well....i dont know what "this and that" is!

---

### Post by nutz on 2007-06-19
> **LaRoza said:**
> By the time you read this, several others will have posted probably, but it was blank when I got here.

So true...

Ubuntu has the best community support of any OS...

You will see when you boot up to the CD ITdrummer. There is an option there to resize your drive. Choose whatever size you want for the Ubuntu partition just make sure it is enough. 10-12gb should be enough for most users provided you don't have a lot of media to store on there. Once the partition is setup you can have Ubuntu automatically setup the file system based on it's size...

---

### Post by ITdrummer on 2007-06-20
Ok, i will be installing a dual boot on a dell laptop. P4 - 2.2Ghz, 512Mb RAM,  30 Gb HD.  I have about 24Gb of music i have stored on an external 30Gb HD, so the only thing i will be storing on my local drive(30 Gb) will be software and minor documents. How should i set up my partitions? How much swap memory should i allocate?

---

### Post by nutz on 2007-06-20
> **ITdrummer said:**
> Ok, i will be installing a dual boot on a dell laptop. P4 - 2.2Ghz, 512Mb RAM,  30 Gb HD.  I have about 24Gb of music i have stored on an external 30Gb HD, so the only thing i will be storing on my local drive(30 Gb) will be software and minor documents. How should i set up my partitions? How much swap memory should i allocate?

Just go for the automatic option and let it use the whole partition that you created for Ubuntu.

---

### Post by BruisedQuasar07 on 2008-01-15
I have been running Ubuntu 7.04 on my Dell GX 60. Unless you want to invest considerable 
time learning to use Grub, I would forget about dual booting a GX60. Dual booting is easy 
with the live CD. You can select from a menu and have it auto set it up fine.. First, defrag 
your hard drive SEVERAL times. I found 15 gigs for Ubuntu is plenty. If you want to use less,
 I would install Xubuntu instead. That is what I have on my dual boot IBM T23 Thinkpad.

Dual boot held up for a month on the T23 30gb drive and then Grub crashed.
I installed a 40gb drive and reinstalled. Its been working dual boot since Spring 2007.

Dual boot on the GX60 crashed within two weeks. I reinstalled and it crashed in 
three weeks. By that time, I decided to just run Ubuntu, everything Linux works
fine in the GX60. Dual Boot on a single hard drive is unstable. You want two drives
for that.The GX60 slim form cannot fit a second drive and it can not boot from an 
external device. Otherwise, I'd install Ubuntu on my 16gb micro drive, a 4gig pen 
drive or an external  hard drive. 

I have four much newer and more powerful PCs but I love the GX60, small form 
factor, low power use. I am using Ubuntu to extend its useable life span. Under Linux,
it is a zippy 1.8 GHz PC.

Bruised

---


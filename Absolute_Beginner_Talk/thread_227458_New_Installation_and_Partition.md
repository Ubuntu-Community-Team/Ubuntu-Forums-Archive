---
title: "New Installation and Partition"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by thornomad on 2006-08-01
Hi,

I am entirely new to Linux/Ubuntu (though would consider myself fairly well versed in computers, both Mac and PC).  My situation is this:

I am a new Mac convert; I have an older laptop (IBM ThinkPad R32 Win XP Pro); I have been waiting for it to die so I could try out Linux on it; my laptop died on me today; I would like to try Linux.

I found it very difficult to decide on a distrubution package, but I like Ubuntu because it is a clever name, a pretty website, and seems friendly to me.  I was tempted, actually, to try Xubuntu because I like streamlined, fast software.  SuSe also tempts me but only because it sounds sexy.  Anyway, here is my question:

My laptop does not have a Win XP Boot CD; instead, there is a secret partition on the computer that holds all the files for me to do a clean reboot and install of Win XP.  What I would like to do, however, is partition the drive and do clean installs of both Linux and Win XP.

I read an article ([read it here]("http://home.nc.rr.com/systemfiles/linux-r32.htm")) that gave suggestions for starting a boot procedure from the linux disks, then using the disk to partition the drive cleverly, then going back to install windows, then going forward with the install of Linux.

Do you have any suggestions?  The only limitation I have is that I cannot boot into Windows for any reason -- it is completely dead.

How should I go about getting both back up and running ?

Thanks,
Damon

---

### Post by deadgobby on 2006-08-01
Well the basic thing to do is save any data you want to save. Becuase you are going to hose the HD. Yep fresh install from the start. If you are hip to video help
[http://video.google.com/videoplay?docid=-6104490811311898236](http://video.google.com/videoplay?docid=-6104490811311898236)
 There is more help too. I would give you more book mark, but my wife is using my other puter with Ubie on it. Now as Suse goes. That is what I am using right now on this puter. It is very slick too. There is reason why why Ubie is #1 and Suse #2. Both have a freaking great o/s. Welcome to the the linux world. At least you know mac o/s and now you can sling  Linux under your belt.
GObby

---

### Post by aam-aadmi on 2006-08-01
Take a look at the following links; they are very helpful.
[www.psychocats.net/ubuntu/installing.html](www.psychocats.net/ubuntu/installing.html)
users.bigpond.net.au/hermanzone/

---

### Post by thornomad on 2006-08-01
Gobby & aam,

thanks for the strong praise; I will try ubuntu for starters for sure; and thank you for the video link ... will watch that now and see if it answers my dual boot questions ... also, took a quick look at those two links ... that helps me understand it a bit better.  i will just have to be sure that i don't format the "secret partition"

D

---

### Post by Ric95 on 2006-08-01
I did a dual boot without hurting the WinXP partition.
It sounds like you have an HP/Compaq like me, with the recovery partition. I had a few problems;
I had to use checkdisk with fix before the install would even get going. (  command; chkdsk C:/f or somesuch.)
I used partition magic to create the 2 linux partitions and start the linux OS install, unfortunatly it left the widows partition with the 'hidden' property on, so I had to have an fdisk program on a cd to unhide the Windows partition.( super fdisk worked)
I have also done a dual boot using only the included Ubuntu installer, it works better!
 Other tweaks like changing the boot order can easily be learned after :)

---

### Post by thornomad on 2006-08-01
> **Ric95 said:**
> 
I have also done a dual boot using only the included Ubuntu installer, it works better!

Did you use the "normal" installer or the "alternate" ?  

Thanks so much everyone !

---

### Post by Ric95 on 2006-08-01
Just the normal. It did require carfull reading to make sure it got the correct partition.
I don't know anything about the alternate. Mabey its simpler? Anyhow the normal installer is very cautious.

---


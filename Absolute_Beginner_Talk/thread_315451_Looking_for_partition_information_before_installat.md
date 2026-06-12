---
title: "Looking for partition information before installation"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by Hughesy on 2006-12-09
Hi all, 

1stly beware, total noobie:KS 

I am looking at installing ubuntu on my laptop but before i do i just have a few questions as i dont want to mess it up and ruin all the info a have, as unfortunetly i do not have the option of backing up my hdd. 

i have tried to get the information i am looking for by searching through the beginner threads, but as i'm sure you will all understand, everyones installations requirements are different. I am installing ubuntu on to my hp dv6000 dual amd 64 laptop. There are currently 2 drives available a 8gb recovery drive and a 85gb c:. 

I am aware that i need to create at least 2 more drives, a 1gb swap drive and i intend on creating a 10gb drive to install ubuntu on and keep linux files on. It also looks like that people create another large drive that can be accessed by both xp and ubuntu, is this true? Can ubuntu not access files say in "my documents" on my c: ? Also in relation to creating the drives i believe that i dont have to do this before installation as it is possible to do during ubuntu installation, is this correct?

I am aware that before partitioning i have to defragment my drive and i am doing this as i type.

---

### Post by tchoklat on 2006-12-09
If you plan to install from the live CD  it will create the partitions for you. You can then install gparted (a partitioning program) to resize the partitions after.  Not sure about a shared drive with XP as Ubuntu will not read NTFS without a third party interface I understand
 
 
Tchoklat

---

### Post by Hughesy on 2006-12-09
Thanks for the reply, 

Used daemon tools to show what was on the cd and it is a live cd. It states that if i reboot it will run a demo. Is this the right cd that will also install ubuntu? Or do i need an alternate cd?

---

### Post by zhangqing6 on 2006-12-09
I am pretty new to ubuntu/linux also.

I think this link is useful.just  for your reference

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by outofnicks on 2006-12-09
If you have the Dapper 6.06 or newer CD, the live CD includes the install. With previous versions (Breezy, etc) there were seperate live and install CDs.
Why don't you just try booting into it? Won't do any harm, and if it works you'll know you can do the install.

---

### Post by louieb on 2006-12-09
I have 4 PC's two dual boot XP, two run only Linux. Only had minor  problems  installing Linux until last week. And I did not have a backup.
The problem it was XP refused to boot. I tried all the things I've see here : boot to XP's recovery console and run fixmbr, and then fixboot, tried a recover install also. 
Fortunately for me I was able using Knoppix to copy  most of my data to DVD. But even at that Reinstalling XP and all the programs and putting the data back was a pain. 
Someone said [COLOR=Red]Experience is what you get after you need it.[/COLOR]         
Someone else also said **it happens.

Oh BTW the installer on both the live and alternate CD  can repartition your hard drive and it may be safer than what I did which was to use the GParted live CD to create the Linux partitions on the computer. That is when it broke.

---

### Post by mikewhatever on 2006-12-09
There is a good site explaining how to dual boot. Check it out.
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

In your case, you can either install Ununtu on the second HD or resize the ntfs C:\. It is recommended there to use FAT32 partition for storage for both Windows and Ubuntu.

Good luck

---


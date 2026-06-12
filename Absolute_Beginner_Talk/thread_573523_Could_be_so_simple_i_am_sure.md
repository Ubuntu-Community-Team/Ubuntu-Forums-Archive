---
title: "Could be so simple i am sure?"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by Jezprice on 2007-10-11
Okay, this is my initial thread:

[http://ubuntuforums.org/showthread.php?t=572695&highlight=jezprice](http://ubuntuforums.org/showthread.php?t=572695&highlight=jezprice)

below is the best reply i have read from posts on my threads

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

yet still its not clear. I have had 3 freinds round, all are very capable of installing windows - MANY TIMES - setting up networks, multiple email accounts etc etc (the NORM) and still we all feel that the answers i am getting from ubuntu users are not as "easily explained as they should be for potentisl new users like ourselves".

Its simple for me, i have 3 partitions on my hard drive:

1: Win XP - NTFS
2: Data disk (storage of items retrievable from both XP & Ubuntu - music movies etc) - NTFS
3: I want to instal Ubuntu HERE?!

Partition 3 is for UBUNTU and beryl which i want to instal later plus the other relevant software dedicated to UBUNTU i will install (i have saved 40GB for this partition). This shows up as FREE SPACE during install - see previous thread.

How do i install Ubuntu on this partition (format it as ext3 for UBUNTU leaving the rest of my hard drive to function as NORMAL). I do not believe that it is as complicated as people are making it out to be. There has to be someone out there who has a well explained 1.2.3 how to do this. 

I have played with the live CD and love usind ubuntu but do not want to mess up my WIN xp partition and datd storage partition so please some one explain this to me in "for dummies" speak as the stuff i have read makes a mess of the sense it should make.

You are all to clever................................

---

### Post by Jezprice on 2007-10-11
--------------------------------------------------------------------------------

Okay, this is my initial thread:

[http://ubuntuforums.org/showthread.p...light=jezprice](http://ubuntuforums.org/showthread.p...light=jezprice)

below is the best reply i have read from posts on my threads

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

yet still its not clear. I have had 3 freinds round, all are very capable of installing windows - MANY TIMES - setting up networks, multiple email accounts etc etc (the NORM) and still we all feel that the answers i am getting from ubuntu users are not as "easily explained as they should be for potentisl new users like ourselves".

Its simple for me, i have 3 partitions on my hard drive:

1: Win XP - NTFS
2: Data disk (storage of items retrievable from both XP & Ubuntu - music movies etc) - NTFS
3: I want to instal Ubuntu HERE?!

Partition 3 is for UBUNTU and beryl which i want to instal later plus the other relevant software dedicated to UBUNTU i will install (i have saved 40GB for this partition). This shows up as FREE SPACE during install - see previous thread.

How do i install Ubuntu on this partition (format it as ext3 for UBUNTU leaving the rest of my hard drive to function as NORMAL). I do not believe that it is as complicated as people are making it out to be. There has to be someone out there who has a well explained 1.2.3 how to do this. 

I have played with the live CD and love usind ubuntu but do not want to mess up my WIN xp partition and datd storage partition so please some one explain this to me in "for dummies" speak as the stuff i have read makes a mess of the sense it should make.

You are all to clever................................

---

### Post by Pumalite on 2007-10-11
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

### Post by LowSky on 2007-10-11
the psychocats seems very clear to me.

all you need is to make the free space, a root (/) for linux

do a manual partition of ubuntu and set up the 3rd partition as ```
/
``` with whatever amount of space you want.

---

### Post by rsambuca on 2007-10-11
Please don't make multiple threads with the same question (actually this makes three now).

---

### Post by mister_lister on 2007-10-11
I am new to ubuntu to, but I have installed other distributions. Each distribution is different on how they handle the gui version of partitioning and setting up the boot. 

My suggestion is what I have done, and it is this: Buy a hard drive caddy and hard drive that will be a dedicated linux hard drive. If you do not know what a hard drive caddy is, they are sleeves that fit in a CD ROM drive bay, in which you can swap out hard drives easily. They range in price from just about 20$ and up,  making life real simple. They come in two flavors SATA and PATA, PATAs are getting harder to get a hold of, the flavor you buy depends on the hard drives you have.  You don't need a huge hard drive for ubuntu, maybe a 20GB so that wont cost you much either, especially if the drives you are going to using are PATA.

This has made it real simple for me, I just select the new hard drive, put it in the caddy, start my machine with the live cd in, do a full install after ubuntu boots (selecting erase drive and use whole drive). After that when ever I want to use ubuntu or Windows (which rare now) I just slap in the hard drive for the os of choice and boot normally.

This eliminates making mistakes partitioning with the install when you are new to the whole partitioning thing in linux and you can there after practice setting up partions with out worrying about wiping your XP partition.

Give it a try.

---

### Post by ChaosParser on 2007-10-11
Select Manual partitioning.  Leave 1 and 2 alone.  Put a checkmark in FORMAT for the space you want you ubuntu to use.  Make its mountpoint /

That's it.

---

### Post by mramsey on 2007-10-11
> **Jezprice said:**
> 

How do i install Ubuntu on this partition (format it as ext3 for UBUNTU leaving the rest of my hard drive to function as NORMAL). I do not believe that it is as complicated as people are making it out to be. There has to be someone out there who has a well explained 1.2.3 how to do this. 


Just allow ubuntu to install to the largest free space as ext3..it will automatically create the swap partition and install the grub boot loader. It really is that simple, I am dual booting now with XP and ubuntu.

---

### Post by nick_h on 2007-10-11
I think it was all covered in the previous thread.  Do the following:

1. Create a small swap partition approx. twice the size of your physical memory.
2. Follow the instructions in the psychocats link selecting the manual partition option.
3. Make the partition you want to install Ubuntu on type ext3 and mount point /
4. Make your swap partition type swap (no mount point).
5. Keep your other 2 partitions mounted as /media/sdax.
6. Select the boxes to format your ext3 and swap partitions.
7. Make sure that you have not selected to format your windows or data partitions.

To be safe always make a backup of your data first.

---

### Post by bigken on 2007-10-11
I would make your free space an extented partition and and manually make 
three partitions within the extended partiton

/ 10gig 
swap twice your ram ie 512mb=1gig
whats left home 

one good reason for a seperate home partition is if you need to reinstall ubuntu all you personal files and email ect stay in tact no need to back em up  :)

---

### Post by cmnorton on 2007-10-11
I went and read the psychocats link, and I would not say it is compliated as much as it is very detailed. The Ubuntu -- for that matter a lot of Linux-based installations -- allow you to get to a point in the installation and bail out before you have "commited" to the installation (altered information on the disk(s), data, partitions, and so on). 

So, to answer your basic question, you should be able to identify the 3rd partition into which you want to install during the early stages of the Ubuntu installation. From that partition, you would have to carve out / and swap.

IMHO given you still want to use Windows, I would find a cheap "box" that meets a little more than the current Ubuntu requirements (to grow on), and install Ubuntu on that. You have clearly invested a lot in your Windows system, and while a lot of people have tackled dual-boot, I believe it is at least a medium-level system administration job.

Otherwise, with patience and boiling down your problem into more discrete questions,  you will probably get an answer. As an alternative, that "cheap box" I mentioned earlier might be a very good staging device on which to install Windows, the second partition, and Ubuntu. Then you might feel more adventurous and learn more about dual-boot.

Good luck.

---

### Post by steve.horsley on 2007-10-11
OK, so partitions 1 and 2 are NTFS. 

If partition 3 exists, i.e. you have already created a partition you want Ubuntu to be installed on, then delete it so the disk has unpartitioned space. Then you can tell the installer to use the free space (it means unpartitioned space) on the disk. Doing this removes the need for manually editing partitons at all. Let the partitioner do the work automatically. 

Your problem in the last thread was that after manually creating partitions, you have to go back to the editor and say where you want them mounted. You must select one partition to mount as "/". That's not the easiest way, but it's what you have to do if you're installing onto existing partitions - you have to tell it which ones to use and how. Clearing some space and telling it "just use the free space" is the easy way.

---

### Post by Jezprice on 2007-10-12
Thank you all for your help, as a new user it is great to see there are people out there with excellent and easily understandable advice for a total newbie.

I want to thank LowSky and Chaos Parser in particular for the straightforward uncomplicated answers, simply giving me the little bit of info i was missing.

The other info is great to especially the first link from Pumalite.

Cheers all, Ubuntu is great and i have only played with the live CD so far!!!

---

### Post by jvc26 on 2007-10-12
One other brief thing to note, beryl is finished now as it has re-merged with compiz in the form of compiz fusion, so I would recommend looking into Compiz-fusion for beryl-like effects now,
Il

---


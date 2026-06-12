---
title: "I partitioned wrong... need help"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by wandaa on 2007-05-27
Hi all, just got ubuntu installed, was happy about it, until I noticed that I had partitioned 80gigs for XP and 180 for ubuntu, I meant it to go the other way? is there ANY way to get this back? or reinstall ubuntu or what ever... thanks already... i'm a beginner, please gimme links to the programs I might need, if I need any...

---

### Post by overdrank on 2007-05-27
> **wandaa said:**
> Hi all, just got ubuntu installed, was happy about it, until I noticed that I had partitioned 80gigs for XP and 180 for ubuntu, I meant it to go the other way? is there ANY way to get this back? or reinstall ubuntu or what ever... thanks already... i'm a beginner, please gimme links to the programs I might need, if I need any...

Hi and welcome, you should be able to use the live cd again and resize the partition but back all you data first. Hope this helps good luck!:popcorn:

---

### Post by mikewhatever on 2007-05-27
Yes, you can redo it. Check the [Uninstall Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm") to remove Ubuntu. Delete all partitions you created for Ubuntu, enlarge the Windows partitions, reinstall Ubuntu.

---

### Post by wataboutbob on 2007-05-27
surely... he can just resize the partition using gparted that comes with the LiveCD?

---

### Post by wandaa on 2007-05-27
what would be the simplest way, so far the simplest way I have seen replied, would be the livecd gparted proggy (most likely, if its simple ;)) and THANK YOU for so fast replies, would have had no chance of getting ANY replies if I would have had the same problem with windows/micro$oft... guess I will be staying with ubuntu for a while! :)

---

### Post by wandaa on 2007-05-27
sorry that I'm replying to my own topic so many times... but now I have taken about 150gigs OFF of my linux partition, and it made that 150gigs into some "un(something)", something like unpartitioned part... so I was wondering how do I ADD that 150gb into my 80gb windows partition, I THINK it might be that I just do a "new partition" with the same type as my windows partition (NTFS, and my linux partition type is ext3 (or something like that)).. someone PLEASE help me, would really like to get this working :)

---

### Post by Nikron on 2007-05-27
> **wandaa said:**
> sorry that I'm replying to my own topic so many times... but now I have taken about 150gigs OFF of my linux partition, and it made that 150gigs into some "un(something)", something like unpartitioned part... so I was wondering how do I ADD that 150gb into my 80gb windows partition, I THINK it might be that I just do a "new partition" with the same type as my windows partition (NTFS, and my linux partition type is ext3 (or something like that)).. someone PLEASE help me, would really like to get this working :)

This is easily done in gparted, just use what is basically self-explanatory interface, and wait for a couple of hours for it to do it.

---

### Post by wandaa on 2007-05-27
> **Nikron said:**
> This is easily done in gparted, just use what is basically self-explanatory interface, and wait for a couple of hours for it to do it.

So I should do as I thought I should do? Add that partition as a new partition of type NTFS? Never had anything to do with partitioning before :D (TOTAL BEGINNER!)

---

### Post by wataboutbob on 2007-05-27
> **wandaa said:**
> sorry that I'm replying to my own topic so many times... but now I have taken about 150gigs OFF of my linux partition, and it made that 150gigs into some "un(something)", something like unpartitioned part... so I was wondering how do I ADD that 150gb into my 80gb windows partition, I THINK it might be that I just do a "new partition" with the same type as my windows partition (NTFS, and my linux partition type is ext3 (or something like that)).. someone PLEASE help me, would really like to get this working :)

Here's what I understand.

You have, lets say, a 200 GB HDD on which you have one NTFS partition with XP. You used the LiveCD and ended up with an XP NTFS partition of 80 GB and a linux partition of 120 GB, whereas you wanted the larger partition to go to the XP. Now, you've used gparted to resize the ext3 and wondering how to add the balance to the original NTFS.

If you'll take my advice, here's what I've done

Its good practice to keep your data seperate from your OS. So I'd advice you to start from scratch (keeping your existing XP installation) for what is ideal below.

C:\ 20 GB NTFS (XP System partition) - overkill if you ask me, 15 GB is more than adequate for XP, Office 2007, various video/media editing tools. I tend to install games in a seperate partition so I get away with even less space for my main XP_SYSTEM partition. Also considering the 1st thing I do when I install XP is to go to My Documents, right-click and give new target inD:\, most of the data is saved seperate.

D:\ 130 GB NTFS (Data partition - for media, games, documents) since I've never had a problem using ntfs-3g to read/write the NTFS drive using Ubuntu, that's where most of the data is. Mind you, I take weekly backups of that drive to my external My Book 1TB.

The remaining space of 8 GB was made into ext3 partition using gparted when installing Ubuntu. I'd recommend that you download the SystemRescueCD from [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) as they have the better GUI version of gparted that we used to get with 6.10 Edgy Eft.

Using that, you can resize your existing windows partition to something like 20 GB. Assign the rest to NTFS_Data and then use the LiveCD to cut a small portion from the end of NTFS_Data for Ubuntu.

---

### Post by overdrank on 2007-05-27
> **wandaa said:**
> So I should do as I thought I should do? Add that partition as a new partition of type NTFS? Never had anything to do with partitioning before :D (TOTAL BEGINNER!)

Hi maybe this will help 
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Good luck and I hope you remembered to back up your data!;)

---

### Post by wandaa on 2007-05-27
I have gotten it working... solution:

took that 150gb partition and made it into a 120(ish)gb  partition, and a 30gig partition...
made the 120gigs a ntfs type for windows, and the 30gigs I just left untouched... 
Now I have a dual boot with Ubuntu and Windows XP, didn't have to uninstall ubuntu, and now my only problem is getting my wlan to work... which I have the drivers already downloaded, just gotta see how do I install them... at the moment, i'm happy!!!! go ubuntu! :popcorn:

---


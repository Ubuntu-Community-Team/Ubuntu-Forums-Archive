---
title: "Backing up data before Fiesty install"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by TekMuzik on 2007-04-18
I've got so many things messed around with now in my Edgy install, I'm planning to just completely format the partition and do a fresh install of Fiesty tomorrow. But I have a lot of movies/music/pictures on my Ubuntu partition I don't want to lose, so my plan was too...

1. Create a FAT32 partition on my hard drive
2. Mount the FAT32 partition
3. Copy all the stuff I want to keep over
4. Delete my Ubuntu partition
5. Do a fresh install of Fiesty
6. Remount FAT32 partition
7. Copy all the stuff I kept back over

Any one got any ideas for a simpler way? I thought about just backing to DVDs, but it's about 30GB of data, and I don't want to waste that many DVDs. But it's also going to take a really long time to copy that 30GB from one partition to another, and then back again. Any help is appreciated.

---

### Post by freebird54 on 2007-04-18
If you have room for another partition - make it ext3.  Copy your stuff over.  When Feisty is installed, just mount the ext3 partition as /home/data  or whatever you like.  Much less work!

---

### Post by earobinson on 2007-04-18
that way seems like your best bet. I would use ext3 over fat32, but then I dont run windows. Also if you keep your data on a diff partition you will be able to reinstall whenever you like.

Good luck, let us know how it goes. And rember if the data is really important to burn it also.

---

### Post by TekMuzik on 2007-04-18
> **freebird54 said:**
> If you have room for another partition - make it ext3.  Copy your stuff over.  When Feisty is installed, just mount the ext3 partition as /home/data  or whatever you like.  Much less work!

Can Windows read ext3? I was planning on using the extra partition, after I'm done with the upgrade, as a sharing point between Linux and Windows. I have some DVD Menu Designers and Burners in Windows that I just haven't found a match for in Linux yet. I was going to try them on Wine, but I lost my install CDs for the programs. :(

Sorry for asking a question I could probably easily search for and find an answer, but I'm feeling lazy right now, lol.

---

### Post by RobsterUK on 2007-04-18
> **TekMuzik said:**
> Can Windows read ext3? I was planning on using the extra partition, after I'm done with the upgrade, as a sharing point between Linux and Windows. I have some DVD Menu Designers and Burners in Windows that I just haven't found a match for in Linux yet. I was going to try them on Wine, but I lost my install CDs for the programs. :(

Sorry for asking a question I could probably easily search for and find an answer, but I'm feeling lazy right now, lol.

Windows can't read ext3. If you have dual boot WIndows/Ubuntu then using a FAT32 partition like you said in your first post is the best way to go as both Ubuntu and Windows can read and write to it.

If you only had Ubuntu on your machine then you could use an ext3 partition

As mentioned above if you want both windows and Ubuntu to have access to your files then you could leave them on the FAT32 partiion after you've installed Fiesty

hope this helps

---

### Post by freebird54 on 2007-04-18
Actually there is a driver so that recent Windows (like XP) can read and write ext3 without a problem.  The other way around works too, as the ntfs-3g driver now works reliably for r/w  from Linux in NTFS (at least XP style NTFS )

I personally would use the ext3 because not even Windows finds FAT32 particularly reliable :)

EDIT: here's the link for Windows to read ext3:  [http://www.fs-driver.org/](http://www.fs-driver.org/)

and here is the link for ntfs-3g for the other way around  [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by TekMuzik on 2007-04-18
> **freebird54 said:**
> Actually there is a driver so that recent Windows (like XP) can read and write ext3 without a problem.  The other way around works too, as the ntfs-3g driver now works reliably for r/w  from Linux in NTFS (at least XP style NTFS )

I personally would use the ext3 because not even Windows finds FAT32 particularly reliable :)

EDIT: here's the link for Windows to read ext3:  [http://www.fs-driver.org/](http://www.fs-driver.org/)

and here is the link for ntfs-3g for the other way around  [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

I tryed using the NTFS-3G method a few months ago. I got it working but it was such a pain I don't want to deal with it again. I will try the Windows driver to read ext3 though. 

Thanks for your help everyone!

---

### Post by FuriousLettuce on 2007-04-18
The ext3 driver works fine for me, I used to use it for at least half a year before I got rid of Windows.

---


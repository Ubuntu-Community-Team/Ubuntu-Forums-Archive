---
title: "[SOLVED] Partition Question"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by RenegadeZero on 2008-02-04
Hi, 
I am a completely new user to Ubuntu, so I apologise if this question has been asked numerous times (Searching didn't fully answer me). I have 2 320GB NTFS formatted drives for Windows and Backups, and an 80 for Ubuntu.

1. I am not sure what to partition the 80 one for Ubuntu with, I have read that FAT32 has a limit of 4GB for files, and I think I will have some files that go over that. What do I do here?

2. I have read that you can mount an NTFS drive(s) in Ubuntu so that it can read and write to NTFS Drives. However, I have some rather important documents on them. I have heard that this is dangerous and may harm the files on the NTFS drive. Is this true?

3. What can I do to make Windows see the Linux drive and write/access it's files, without harming either?

4. And lastly, I have been told before installing Ubuntu that I should go into BIOS and change the 1st Boot Device from my 320gb Windows HDD to the 80gb drive, so that when I install Ubuntu, the Master Boot Record will be on the 80GB, and does not mess up the Windows one and incase I ever need to remove Ubuntu, it would not mess up everything. Should I change the order, or just leave it as it is... 

Thank you in advance, hopefully I can enjoy Ubuntu as much my colleagues! :)

---

### Post by Rocket2DMn on 2008-02-04
> **RenegadeZero said:**
> Hi, 
I am a completely new user to Ubuntu, so I apologise if this question has been asked numerous times (Searching didn't fully answer me). I have 2 320GB NTFS formatted drives for Windows and Backups, and an 80 for Ubuntu.

1. I am not sure what to partition the 80 one for Ubuntu with, I have read that FAT32 has a limit of 4GB for files, and I think I will have some files that go over that. What do I do here?
Your filesystem will be "ext3", there is no size limit on it.  This is the default filesystem for linux.

> 2. I have read that you can mount an NTFS drive(s) in Ubuntu so that it can read and write to NTFS Drives. However, I have some rather important documents on them. I have heard that this is dangerous and may harm the files on the NTFS drive. Is this true?
You can access and read/write using the ntfs-3g driver (it comes with Gutsy).  It is stable, so you don't really have any need to worry.  However, you should ALWAYS keep good backups regardless of what filesystem or operating system you use.

> 3. What can I do to make Windows see the Linux drive and write/access it's files, without harming either?
You can get a driver from [http://fs-driver.org/](http://fs-driver.org/) which is designed for ext2 filesystems.  You can mount ext3 filesystems with it, because the only difference between ext2 and ext3 is that ext3 has journaling which means if something happens and the computer has to be rebooted unsafely, you won't have to run a disk check.  It's essentially just ext2.  HOWEVER, although this driver is useful, I would not put full faith in it.  You don't need to store anything on your linux drive to access from windows, just store the data on an NTFS partition and access it from Ubuntu.

> 4. And lastly, I have been told before installing Ubuntu that I should go into BIOS and change the 1st Boot Device from my 320gb Windows HDD to the 80gb drive, so that when I install Ubuntu, the Master Boot Record will be on the 80GB, and does not mess up the Windows one and incase I ever need to remove Ubuntu, it would not mess up everything. Should I change the order, or just leave it as it is... 

Thank you in advance, hopefully I can enjoy Ubuntu as much my colleagues! :)

I'm not sure this is necessary.  You can overwrite your windows MBR and repair it later if you get rid of Ubuntu by booting to the windows cd and entering the recovery console.  Then you would just type
```
fixmbr
```
However, it's your call on that one.

Welcome to Ubuntu!

---

### Post by mike1821 on 2008-02-04
Hello friend,

1. In order to use Ubuntu or any other Linux distribution, you will need to have an ext3 or reiserfs filesytem. The Ubuntu installer will automatically format the drive which you will specify to it, into ext3 filesystem format.

2. You are right. Ubuntu will automatically mount your NTFS file system with read/write access. If I were you I would use only its read ability though. Writing in an NTFS partition is a bit risky (at least in my opinion). The most secure way to transfer data between a Linux and Windows installation is to use a common FAT32 partition.

3. Windows does not recognise any Linux filesystem without external help. By saying external help I mean an external application which will be able to mount the Linux FS. I would recommend to use Total Commander. It's environment is similar to Midnight Commander and it allows you to transfer any kind of files.

4. I do not think this is necessery. You can allow Ubuntu to write its MBR (Grub) into your primary hard drive with no problem. GRUB will replace the windows MBR and will create a multi-boot environement for you automatically. In case you do something wrong you can always create a new MBR for windows using the "fixmbr" command through the Windows XP rescue console.

I hope these help clear out some things,
Mike

---

### Post by RenegadeZero on 2008-02-04
Wow, thank you all for the immediate response (I guess my friend was right afterall about Ubuntu having a great community)!

> The most secure way to transfer data between a Linux and Windows installation is to use a common FAT32 partition.

Hmm, that is a rather good idea... I could create a small 10GB or so drive just for exchanging the 2... wow, talk about simplicity!

Thank you all!

---

### Post by Rocket2DMn on 2008-02-04
> **RenegadeZero said:**
> Wow, thank you all for the immediate response (I guess my friend was right afterall about Ubuntu having a great community)!



Hmm, that is a rather good idea... I could create a small 10GB or so drive just for exchanging the 2... wow, talk about simplicity!

Thank you all!

I would still say it's safe to use ntfs-3g.  It is a stable version, also see here - [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)
I was a little worried at first when I switched to Ubuntu , but I think this is mostly due to how long it took them to release a stable driver to ntfs (12 years!).  I actually waited to switch to linux until the driver became stable because I knew I would need it.
I have never heard anybody complain about it or heard reports of it breaking anything, so I think you're pretty safe (I use it myself as well).
However, you can do FAT32 if it makes you feel better, I just don't think it's necessary.

---

### Post by RenegadeZero on 2008-02-04
> I have never heard anybody complain about it or heard reports of it breaking anything

Really huh.... hmm. I might actually try that route, as the FAT32 option is rather bothersome copying it over, switching OS and then copying it again. Thanks.

Also, just to make it clear, since I didn't ask it before, but does "copying" a file constitute as just "read'? If it is, and reading is safe, Ubuntu can easily (and safely) copy files from mounted NTFS drives?

---

### Post by hyper_ch on 2008-02-04
ntfs drives will not be auto-mounted as read/write... just as read-only.

---

### Post by Rocket2DMn on 2008-02-04
> **RenegadeZero said:**
> Really huh.... hmm. I might actually try that route, as the FAT32 option is rather bothersome copying it over, switching OS and then copying it again. Thanks.

Also, just to make it clear, since I didn't ask it before, but does "copying" a file constitute as just "read'? If it is, and reading is safe, Ubuntu can easily (and safely) copy files from mounted NTFS drives?

Yes, but ntfs-3g also allows for write capability.  It is the write capability that would be the most difficult to get to be stable, but it is :)
In a nutshell, ntfs-3g allows you to safely read and write partitions that are formatted with NTFS
:guitar:
I'm gonna catch some Z's now, post back if you have more questions and I'll get to them in the morning.  Peace!

---


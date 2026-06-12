---
title: "Keep Dapper and install Vista"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by Bethrine on 2007-08-31
Hello everyone.

I installed Dapper Drake, using it to partition my hard drive with the live CD, after defragging Vista once. Vista's files are all still there and I copied my pictures to Dapper yesterday (there is plenty of room on both partitions, I think). I would like to re-install Vista today (it boots to a black screen after the loading bars which freeze and unfreeze every few seconds) instead of the desktop only so I can run AutoCADLT 2005. I would appreciate any and all suggestions on how to do this, without upsetting my system, very much. 

Some specs:

120 GB SATA II HD 7200rpm with 8 MB cache / 7200rpm on 8 MB cache

*when starting gparted I get in terminal:*
cathy@Bethrine:~$ sudo gparted
Error reading inode 2917.
Error reading inode 4380.
Error reading inode 7955.
Error reading inode 10099.
Error reading inode 10980.
Error reading inode 12693.
Error reading inode 14741.
Error reading inode 15368.
Error reading inode 22917.
Error reading inode 22918.
Error reading inode 159.
Error reading inode 842.
Error reading inode 6442.
Error reading inode 6446.
Error reading inode 6450.
Error reading inode 6454.
Error reading inode 6458.
Error reading inode 6465.
Error reading inode 6469.
Error reading inode 6483.
Error reading inode 6487.
Error reading inode 6491.
Error reading inode 6495.
Error reading inode 6499.
Error reading inode 6503.
Error reading inode 6507.
Error reading inode 6511.
Error reading inode 6515.
Error reading inode 6519.
Error reading inode 6523.
Error reading inode 6527.
Error reading inode 6531.
Error reading inode 6535.
Error reading inode 6539.
Error reading inode 6543.
Error reading inode 7629.
Error reading inode 8160.
Error reading inode 24399.
Error reading inode 27943.
Error reading inode 28990.
Error reading inode 29941.
Error reading inode 31681.
Error reading inode 33502.
Error reading inode 34110.
Error reading inode 34142.
Error reading inode 34165.
Error reading inode 34177.
Error reading inode 34211.
Error reading inode 34212.
Error reading inode 34228.
Error reading inode 34390.
Error reading inode 34743.
Error reading inode 34948.
Error reading inode 35835.
Error reading inode 36897.
Error reading inode 46243.
Error reading inode 46248.
Error reading inode 46257.
Error reading inode 46522.
Error reading inode 46539.
Error reading inode 47035.
Error reading inode 47343.
Error reading inode 49127.
Error reading inode 50584.
Error reading inode 55800.
Error reading inode 56006.
Error reading inode 56219.
Error reading inode 61184.
Error reading inode 61770.
Error reading inode 61785.
Error reading inode 62006.
Error reading inode 62075.
Error reading inode 63054.
Error reading inode 63456.
Error reading inode 63457.
Error reading inode 63458.
Error reading inode 63459.
Error reading inode 63460.
Error reading inode 63461.
Error reading inode 63462.
Error reading inode 63463.
Error reading inode 63464.
Error reading inode 65466.
Error reading inode 68579.
Error reading inode 81894.

*then gparted tells me:*
/dev/sda1 ntfs   8.37 GB   4.69 GB used     3.67 GB unused
/dev/sda2 ntfs 50.61 GB  24.11 GB used 26.50 GB unused boot flag
/dev/sda3 ext3 51.39GB    3.75 GB used 47.65 GB unused
/dev/sda4 extended 1.42 GB  ---  ---
    /dev/sda5 linex-swap  1.42 GB ---  ---


:~$ sudo fdisk /dev/sda

The number of cylinders for this disk is set to 14593.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help):


Any help at all, I wasn't expecting what I got. Now I'm *totally* lost! Is my system okay??? (I can take a screenshot but I don't know how to do anything but save it to my desktop.)

---

### Post by klytu on 2007-08-31
> **Bethrine said:**
> Hello everyone.

I installed Dapper Drake, using it to partition my hard drive with the live CD, after defragging Vista once. Vista's files are all still there and I copied my pictures to Dapper yesterday (there is plenty of room on both partitions, I think). I would like to re-install Vista today (it boots to a black screen after the loading bars which freeze and unfreeze every few seconds) instead of the desktop only so I can run AutoCADLT 2005. I would appreciate any and all suggestions on how to do this, without upsetting my system, very much. 

Some specs:

120 GB SATA II HD 7200rpm with 8 MB cache / 7200rpm on 8 MB cache

*when starting gparted I get in terminal:*
cathy@Bethrine:~$ sudo gparted
Error reading inode 2917.
Error reading inode 4380.
Error reading inode 7955.
Error reading inode 10099.
Error reading inode 10980.
Error reading inode 12693.
Error reading inode 14741.
Error reading inode 15368.
Error reading inode 22917.
Error reading inode 22918.
Error reading inode 159.
Error reading inode 842.
Error reading inode 6442.
Error reading inode 6446.
Error reading inode 6450.
Error reading inode 6454.
Error reading inode 6458.
Error reading inode 6465.
Error reading inode 6469.
Error reading inode 6483.
Error reading inode 6487.
Error reading inode 6491.
Error reading inode 6495.
Error reading inode 6499.
Error reading inode 6503.
Error reading inode 6507.
Error reading inode 6511.
Error reading inode 6515.
Error reading inode 6519.
Error reading inode 6523.
Error reading inode 6527.
Error reading inode 6531.
Error reading inode 6535.
Error reading inode 6539.
Error reading inode 6543.
Error reading inode 7629.
Error reading inode 8160.
Error reading inode 24399.
Error reading inode 27943.
Error reading inode 28990.
Error reading inode 29941.
Error reading inode 31681.
Error reading inode 33502.
Error reading inode 34110.
Error reading inode 34142.
Error reading inode 34165.
Error reading inode 34177.
Error reading inode 34211.
Error reading inode 34212.
Error reading inode 34228.
Error reading inode 34390.
Error reading inode 34743.
Error reading inode 34948.
Error reading inode 35835.
Error reading inode 36897.
Error reading inode 46243.
Error reading inode 46248.
Error reading inode 46257.
Error reading inode 46522.
Error reading inode 46539.
Error reading inode 47035.
Error reading inode 47343.
Error reading inode 49127.
Error reading inode 50584.
Error reading inode 55800.
Error reading inode 56006.
Error reading inode 56219.
Error reading inode 61184.
Error reading inode 61770.
Error reading inode 61785.
Error reading inode 62006.
Error reading inode 62075.
Error reading inode 63054.
Error reading inode 63456.
Error reading inode 63457.
Error reading inode 63458.
Error reading inode 63459.
Error reading inode 63460.
Error reading inode 63461.
Error reading inode 63462.
Error reading inode 63463.
Error reading inode 63464.
Error reading inode 65466.
Error reading inode 68579.
Error reading inode 81894.

*then gparted tells me:*
/dev/sda1 ntfs   8.37 GB   4.69 GB used     3.67 GB unused
/dev/sda2 ntfs 50.61 GB  24.11 GB used 26.50 GB unused boot flag
/dev/sda3 ext3 51.39GB    3.75 GB used 47.65 GB unused
/dev/sda4 extended 1.42 GB  ---  ---
    /dev/sda5 linex-swap  1.42 GB ---  ---


:~$ sudo fdisk /dev/sda

The number of cylinders for this disk is set to 14593.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help):


Any help at all, I wasn't expecting what I got. Now I'm *totally* lost! Is my system okay??? (I can take a screenshot but I don't know how to do anything but save it to my desktop.)

I'm guessing part of the issue is that you used gparted to re-size Vista's primary boot partition. As far as I know, gparted cannot reliably resize Vista's primary boot partition; it is a special, different type of NTFS structure- I don't know the details. I discovered this when I tried to expand Vista 's primary boot partition; I found I could only shrink it and then only with Vista's built-in partitioning manager! 

I would suggest the following. If you have all of your Vista data backed-up, try deleting the old Vista partitions altogether with gparted, leaving only the partitions Dapper is using plus free, unpartitioned  space. Then install Vista, letting Vista set up it's partition on the free space you cleared. Once this is completed, you should be able to boot into Vista (and only Vista!). The last step would be to re-install GRUB to be able to boot from your choice of either Vista or Dapper.

---

### Post by Bethrine on 2007-08-31
I only partitioned once and I let the live CD do it. I installed gparted afterward and have only used it to "look". Can I back up my Vista from Ubuntu?

---

### Post by Bethrine on 2007-08-31
*bump*

---

### Post by klytu on 2007-09-01
> **Bethrine said:**
> I only partitioned once and I let the live CD do it. I installed gparted afterward and have only used it to "look". Can I back up my Vista from Ubuntu?

> I only partitioned once and I let the live CD do it.  I think this would be a problem as well, if you started out with a Windows Vista primary boot partition. As I understand it, you would have needed to  resize that partition with either Windows Vista's built-in partition manager or one of a (small) number of other non-free commercial partitioning utilities. 
> Can I back up my Vista from Ubuntu? You can probably access and save most of your data with Ubuntu, yes. But if you have nothing important on your Vista partitions, I think it would be easier for you to delete the old Vista partitions and re-install Vista on the free space as I suggested earlier. If you are hesitant to go this route, you could also try reinstalling Vista on the drive in the state it's currently in. What you would need to be careful of in this case would be Vista wiping out your Dapper partitions when it installs.

---

### Post by Ptero-4 on 2007-09-01
Or dump Vista and install XP (yes AutoCAD runs in XP, my sister have AutoCAD 2006 running on XP).

---

### Post by Bethrine on 2007-09-01
I I have XP also. 

"What you would need to be careful of in this case would be Vista wiping out your Dapper partitions when it installs."

Will I have the same problem with XP trying to wipe out Dapper? I could use some explicit advice here or a link pretty please The video I found installs XP first, I don't want to have to re-install Dapper too.

Don't know if this is pertinent:I installed a linux kernal in "updates" yesterday and it said something like 6.14 or 6.41...(shoulda' paid more attention), do I still have the Dapper version? Will this effect the new install?

Bethrine ~she who's newbieness is shining through :)      Oh, and thanks for the replies! Gotta' LOVE this forum!

---

### Post by Bethrine on 2007-09-01
*bump*

---


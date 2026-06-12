---
title: "MB 5,1 Partitioning"
date: 2010-09-16
forum: Apple Hardware Users
---

### Post by Engine_number_9 on 2010-09-16
Hi,

I'm trying to install Ubuntu on a MB 5,1 in a dual boot environment. I've followed the installation instruktions at [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation")

I've deleted the partition created by boot camp. When I get to step 4 of the installation I choose to "install to the largest continuous free space". When I reach the last step of the installation (sted 7) I press advanced in order to install grub to /dev/sda3. However /dev/sda3 is not an option in the drop down menu. The only options are /dev/sda /dev/sda-1 /dev/sda1 /dev/sda2 (OS X). 

What to do?

---

### Post by linuxopjemac on 2010-09-16
You can do it from the liveCD:
```
sudo grub-install /dev/sda3
```

---

### Post by Engine_number_9 on 2010-09-17
I've found a solution that worked fine for my mb 5,1. The solution was suggested by Jamesixgun and Jacques4x4 in this thread: [http://ubuntuforums.org/showthread.php?t=1297229&page=6]("http://ubuntuforums.org/showthread.php?t=1297229&page=6"). I've edited the solution a bit since it is meant to solve another problem.
I followed the installation instructions given in the wiki to the point where I had installed refit and created a partition with boot camp manager.


After that: 
1. Boot from Lucid install disc, open gparted, delete the Bootcamp partition.
2. You should see three partitions: EFI, OSX, and Free Space.
3. At the beginning of Free Space, create a small partition for GRUB (I used 512mb) and format it as NTFS.
4. Save changes.
5. Click the install icon on LiveCD desktop.
6. Go through the first couple of screens until you get to step 4 in the installation. When it asks you where you want to install Ubuntu, choose 'Specify partitions manually'.
7. Select the partition you just created (should be /dev/sda3). Choose Change --> use as NTFS. For Check Format, choose 'mount point = /windows.'
8. Select the free space. Within the free space, create a large partition for Ubuntu at the beginning of the free space (for the Ubuntu portion, choose 'Use as Ext4,' mount point = / ), and build a smaller partition (equivalent to twice the amount of RAM in your machine) for the swap (choose Add --> use as Swap).

If everything worked properly, you should now have 5 partitions (sda1: EFI; sda2:OSX; sda3:NTFS; sda4:Ubuntu; sda5:Swap).

9. Go through the rest of the installation. On the last screen, click the Advanced button and choose to install GRUB at /dev/sda3.
10. Let Ubuntu install itself.
11. After installation of Ubuntu, restart. At rEFIt, choose the partition tool and resync. It should now work flawlessly.
12. Power off.

---


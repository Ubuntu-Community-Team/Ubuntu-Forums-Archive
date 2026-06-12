---
title: "inaccesible_boot_device"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by zainka on 2007-09-15
Hi all

This is my second time i install Ubuntu.  This time I install version 7.04 on a new computer which had one partition WORKING with windows 2000. The HDD is 250GB and I used app 130GB for the w2k, the rest was saved for Linux. 

Whilest installing was easy, starting windows afterwards was simply not possible. The menu item for windows was available and accessible. However, Windows boot app. halfway through giving me the dreadful bluescreen and message INACCESIBLE_BOOT_DEVICE.

Please give advice for how to deal with this problem...

sda1 is used for windows

---

### Post by louieb on 2007-09-15
That happen to me once. I got in a hurry and did not defrag my XP install before I shrank its partition. Afraid I'm not much help here never did get Xp to boot Wound up using Ubuntu to copy my data off the XP partition and reinstalling.  Two things to try 1st. : [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/") [SystemRescueCd]("http://www.sysresccd.org/Main_Page") and heres some ideas on other fixes. [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")



---

### Post by zainka on 2007-09-17
- thanx for your reply, I will try this later. However, I did not shrink my HDD to gain place for Ubuntu but used free unused space. (When I assembled my computer i used a 250GB disk, but since I installed w2k I could only utilize half of it because of the earli versions of ntfs or something, But this  was youst fine because rest of the space should be used for Ubuntu)

I therefor used manual install of Ubuntu and selected remaining space minus room for swap for the Ubuntu root partition. 

ntfs partition is however accessible from Ubuntu.

Any ringing bells out there?

---

### Post by louieb on 2007-09-17
Thats strange. The way you described what you did should have worked without any problems. Its good you can see you NTFS data from Ubuntu. The only suggestion I have is on the Illustrated Boot Site there is a section on the files that XP need in order to boot. Win2000 should be pretty much the same. [IDBS MBR Page]("http://users.bigpond.net.au/hermanzone/p6.htm")

---

### Post by zainka on 2007-09-24
Problem solved, or more correct, reason for failure detected. 
 ...In short terms this means simply Microsoft. 

In long term, please sit down and listen, popcorn is served :popcorn:
well, I did not know that before but windows 2000 does not support large HDDs,  atleast not larger than .. hmm 80GB or something (please correct me if wrong). Mine is 250GB. 

Since I installed w2k first, this thingy was the one os that partitioned my space. Now, It never said that myHDD was 250G, but only 130G, thus I did actually get a warning, but thought that if I  preserved a smaller partition for w2k than the sice it detected I should be safe. But safe I was not!

I defined a partition for app 80G and said GO. w2k formated my partition with the dreadful NTFS and installed the OS into this partition and everything was OK.. until I installed Linux. Since Ubuntu DO know there exists larger HDDs than 80G, it found that the disk had some free space available and I said, go for that. Linux installed perfectly, but now my w2k installation was transformed into asparaguses and failed on boot.

After much investigation with Microsoft held as the most suspicious part in this case, I finally understood the problem and found that the only correct thing to do was to install everything from scratch. Since Linux partition was working I could take backup of all critical data from the NTFS disk, which Ubuntu still could read. 

Then I used acronis disk editor and deleted all partition from my HDD. Then I installed windows and let it do the same operation as first time i installed w2k. Then, I used Acronis again to investigate what things w2k had done to my HDD. There was not only one partition created, but 5 partitions where one contained most windata, one was amrked as some netware formatted thing, a couple of partition was marked by acronis as BAD, and one which format I could not remember. The MBR was a topic for itself, but still It could load and run w2k  as if there was no problems to it. So my teory is that windows installation CD mocked everything up because of some addressing problems when counting and formatting the drive. It wrapped its LBA adderss space or something 

Solution was to, by using disk editor, create a small (10GB - 20GB) FAT partition for windows system  and programs and another one for data. Then I erserved app, 60% of the drive for Ubuntu. Now by locking into disk editor, everything looks fine, and I can use the data partition (FAT32) for sharing data between w2k and Ubuntu. System has never been so stabel. Lucky me surviving so long as I did with a mocked up w2k installation

berg
Vidar (Z)

---


---
title: "Yet another partition problem with excited new linux user."
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by nothingeleven on 2008-04-10
Hello everyone, I am in school for computer science first year.

I think that xbuntu is cool, loaded the disk upon cd boot. Went through the install, it is asking for a partition, I tried to make unallocated space by resizing my 80 GB hard disk with Windows xp on it sp1 NTFS. It gave me some error saying it could not resize. I can only guess how to get this xbuntu up and running/ do I get a foreign partition program set it up in windows, FDISK mabey? Please help. 

I have alot of great things on my computer like games and music. And I really dont want to delete all the windows os and its files.

I have 30 gb;s free space.

Ive heard defraging might help. 

GOOD JOB CODERS LOOKS NICE.

---

### Post by SaddleTramp on 2008-04-10
> **nothingeleven said:**
> Hello everyone, I am in school for computer science first year.

I think that xbuntu is cool, loaded the disk upon cd boot. Went through the install, it is asking for a partition, I tried to make unallocated space by resizing my 80 GB hard disk with Windows xp on it sp1 NTFS. It gave me some error saying it could not resize. I can only guess how to get this xbuntu up and running/ do I get a foreign partition program set it up in windows, FDISK mabey? Please help. 

I have alot of great things on my computer like games and music. And I really dont want to delete all the windows os and its files.

I have 30 gb;s free space.

Ive heard defraging might help. 

GOOD JOB CODERS LOOKS NICE.
Howdy, I had the same problem with Vista and at first slicked Vista off and turned to Ubuntu.  Bad idea .. I forgot to backup some important files under something besides Onecare Live.  Anyway, I reinstalled Vista to get my files backed up to DVD and for whatever reason Vista let me resize it this time.  However, I also came across this site, [http://www.raxco.com/home_office/home_perfectdisk_professional.cfm](http://www.raxco.com/home_office/home_perfectdisk_professional.cfm). I think one of the problems of resizing XP/Vista is dependent on where the MFT (Master File Table), which XP/Vista and some other partitioning programs won't move, resides in the partition. Seems, Vista in particular on my system, put the MFT at the end of the partition.  PerfectDisk will move the MFT and most any other "non-movable" files in the partition.  You might won't to give this a try.  PerfectDisk is fairly easy to use and easy to understand Help.  Worked for me and I was able to get Vista resized down to 60Gb.  Hope this helps if you decide to try it.

PerfectDisk 2008 Pro has a 30 day free trial and that's what I used.
S'Tramp

---

### Post by Rocket2DMn on 2008-04-10
Defragging is often necessary before you can resize.  Also, I think it suggested that you resize your Vista partition from within Vista if possible (not true for XP).  After you resize, you can go install Xubuntu on the empty space (needs a root partition and a swap partition, a separate /home partition is optional).
Don't forget to back up your important data before fiddling with partitions.

---

### Post by BaffledMollusc on 2008-04-10
Yes, I agree with the defragging solution. I've had this problem and defragging solved it.

---


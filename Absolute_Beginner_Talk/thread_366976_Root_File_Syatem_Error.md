---
title: "Root File Syatem Error"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by tomco on 2007-02-21
Thought that I had prepared well - partitioned my 1st Disk to include a ext3 Primary and a Fat 32 'Share' partition (all alongside my ntfs Windows). On the second disk I added a 1g 'swap' partition. Worked through the 6.10 live CD install and given my pre-determined partitioning selected the manual option. Got to the mount step (5) selected '/' for my ext3 partition and 'swap' for my 'swap'. No deal! Got a No Root File System error. Wound back a stage to look at what the table said and it had the following:

Part 1   Fat 32  lba (this is a pre-installation restore partition)
Part 2   ntfs     boot (my windows)
Part 3   ext3         
Part 4   fat 32  lba

As I said my second disk has a small 'sawp' partition

What have I done wrong? Help much appreciated

---

### Post by Sqwishy on 2007-02-21
ok so make sure your swap partition is linux-swap type formatted, and i think it needs to be mounted at /swap ... also i think you want a boot loader! So make a 100mb ext2 partition mounted at /boot

---

### Post by tomco on 2007-02-21
Sqwishy, thanks for the response

The 'Swap' was formatted as a 'linux swap'. Sorry, pretty new to this - not sure I completely follow your second point about 'boot loader'. Are you suggesting I create another partition (100mb) and at 'stage 5' mount it as /boot. If thats what you mean, why is this necessary and what would it do?

---

### Post by annda on 2007-02-21
a separate boot partition is not necessary and so that is not your problem.

how did you partition your disk? not with ubuntu liveCD as i understand.

if the ext3 partition cannot be mounted as / (root file system), maybe try deleting and creating it again using the ubuntu live/install CD (it will not do anything to your other partitions if you are careful, so don't worry).

---

### Post by tomco on 2007-02-21
annda

I used Partition Magic 8 - thought that would give me more control - but apparently not. If I rewind the whole thing (restore my HD's to where they originally were) and trust the Live CD partitioning tool, should I select the auto install and if so am I taking less risk with my Windows partition by putting all of my Ubuntu partitions on the second disk (I need Windows still - current access to internet etc and family not quite as enthused by a non-XP future as I am)

Thanks

---

### Post by bodhi.zazen on 2007-02-21
First, if you partitioned with partition magic, as suggested by tomco, users occasionally have problems.

If you like you can re-partition with gparted, the partitioner on the Ubuntu CD.


======================


BUT ....

Second, the "no root" is a bug in the installer. Here is a work around :

Ubuquity fails to find /

[http://ubuntuforums.org/showpost.php?p=1700787&postcount=29](http://ubuntuforums.org/showpost.php?p=1700787&postcount=29)

---

### Post by annda on 2007-02-21
you can put ubuntu on a second disk, but i haven't tried it so i can't tell you how easy it is. plenty of people do it so search around.

i would recommend ubuntu cd or even gparted live cd before install if you want to (it's great, easy to use and can be downloaded - of course - for free from sourceforge.net). i've read about problems with partition magic and linux.

if you are careful **(manual** partitioning is always good, especially since you are not a stranger to partitioning), just make sure you do not delete or format your windows partitions. nothing bad is going to happen. but burn the most important data first, or save it to your second disk - just in case (i mean a total blackout or a thunderstroke during repartitioning).

b

---


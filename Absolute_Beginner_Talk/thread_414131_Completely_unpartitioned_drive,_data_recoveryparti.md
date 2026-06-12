---
title: "Completely unpartitioned drive, data recovery/partition repair?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Wayren on 2007-04-19
So apparently I win at computers. In preperation for Fiesty I booted into the Live CD and was using gparted to resize my Windows and /home partitions. They share the same drive and are the only partitions on the drive. Well the trouble is that either Fiesty or gparted (not sure which) kept mounting the drive whenever it went to access it for resizing. I thought I had it figured out, but after the process completed it just showed the drive as one big lump of unpartitioned space. I didn't have it reformat so I know the data is still there and it's just lost all partition tables and stuffage. So...anyone have any suggestions on how I can get my data back or rebuild the partition(s)?

---

### Post by tbg58 on 2007-04-19
I'm assuming you want to be able to dual boot.  I'm not sure what state your drive is in, so let's start by trying to get your windows boot back.  We'll assume your NTFS partition is still there.

You may want to use another windows pc, make a bootable disk or CD and put fdisk on it from the system32 directory of your win system.
Boot using the floppy or CD then run fdisk -mbr 
This will repair the master boot record that windows looks for when it boots using its own boot manager (if you delete Grub or your Ubuntu partition did not complete, your mbr may be messed up.
This will restore your ability to boot to windows if the NTFS partition is intact.
If this doesn't work, download an image of Ultimate Boot CD (Google to find it) to use its utilities to mount the NTFS partition and try to recover your data.

If the NTFS partition is okay, then the mbr should get your Windows boot working again.

Before you try to install Ubuntu, clean up your windows by deleting obsolete or redundant files, then defrag. This will make the partitioner's job easier and speed up the process.

Then you can try running the LiveCD of Ubuntu again.
Hope this helps!  Good luck!
Rob

---

### Post by Cappy on 2007-04-20
I recently did something VERY similar to this on accident last week (I accidently repartitioned my NTFS drive as EXT3). I was able to recover all my data by using a Windows partition and using recovery utilities .. most don't work on deleted partitions even though they claim they do (I tried about 6 different programs that I selected and only 2 actually worked). Of all the ones I tried, I would recommend Restorer2000 (Windows only) and RecoverSoft (Boot disk, OS independant). I ended up using Recoverer2000 because it recovered all of my filenames while Recoversoft didn't. Both of those have trials.
If I were you, I would either hook up your hard drive to windows on another computer and use Restorer2000 or just use RecoverSoft. On a side note, if you decide to use the trial RecoverSoft you can extract the trial exe and you will get an iso you can burn in linux =)

[http://www.recoversoft.com/data_rescue_pc_info.htm](http://www.recoversoft.com/data_rescue_pc_info.htm)
[http://www.restorer2000.com/](http://www.restorer2000.com/)

I might as well warn you, I don't know of any partition recovery programs that are free.

---

### Post by CoMRaDe_X on 2007-06-17
if you accidentally dropped one of your partitions and did not write over the now blank drive, try Test Disk [http://www.cgsecurity.org/wiki/TestDisk_Download]("http://www.cgsecurity.org/wiki/TestDisk_Download")
it works like a charm:D
and it's for linux
score another one for OPEN SOURCE!!

---


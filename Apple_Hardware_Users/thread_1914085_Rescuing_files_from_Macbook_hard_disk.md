---
title: "Rescuing files from Macbook hard disk"
date: 2012-01-23
forum: Apple Hardware Users
---

### Post by mörgæs on 2012-01-23
I am trying to rescue some files from a misbehaving MacBook with hfs+. MacOS does not boot.

While booting a live Xubuntu 11.10 I can run Gparted. It shows a 74 GiB hfs+ - partition, but it also gives a warning that the package **hfsprogs** is needed in order to read from it. 

After installing hfsprogs (and **hfsutils**, just to be sure) in the live boot, I can still not access the partition, and the same warning keeps appearing in Gparted.



Mounting with the command
```
sudo mount -t hfsplus /dev/sda2 /mnt/mac_harddisk 
```
does not work (gives a generic error).


Since I can't boot MacOS I can't disable the journaling (I believe), and I am afraid to run fsck on the disk while journaling is active.


Does anyone have an idea to what can be done?

---

### Post by allebone on 2012-01-24
> **mörgæs said:**
> I am trying to rescue some files from a misbehaving MacBook with hfs+. MacOS does not boot.

While booting a live Xubuntu 11.10 I can run Gparted. It shows a 74 GiB hfs+ - partition, but it also gives a warning that the package **hfsprogs** is needed in order to read from it. 

After installing hfsprogs (and **hfsutils**, just to be sure) in the live boot, I can still not access the partition, and the same warning keeps appearing in Gparted.



Mounting with the command
```
sudo mount -t hfsplus /dev/sda2 /mnt/mac_harddisk 
```
does not work (gives a generic error).


Since I can't boot MacOS I can't disable the journaling (I believe), and I am afraid to run fsck on the disk while journaling is active.


Does anyone have an idea to what can be done?

Yes if you want the files, dont make any edits to the drive in case of drive failure, obviously.

If the disk wont mount in a unix environment then the best would be to try in a native osx environment. 

If that still doesnt work then you would need to use paid for recovery tools that allow you to recover from a seperate computer and are designed to specifically deal with corruption.

If none of these options are viable then more dangerous approaches can be tried under unix.

Pete

---

### Post by allebone on 2012-01-24
Something like:

mount -o force /dev/sdx /mnt/MountAtYourOwnRisk

Might have to incorporate some of your own command in the above:
sudo mount -t hfsplus /dev/sda2 /mnt/mac_harddisk
To get it to work.

I wouldnt do it myself though :P

Pete

---

### Post by Lars Noodén on 2012-01-24
What about the package 'hfsplus' itself?  Is that installed?

---

### Post by daehenoc on 2012-01-24
Could try [FONT="Courier New"]-o ro[/FONT] or [FONT="Courier New"]-r[/FONT] in the mount options for read-only in conjunction with force, make sure you don't accidentally change anything on the HDD.

---

### Post by mörgæs on 2012-01-24
Thanks for the ideas. Didn't work though, so now I am just installing a fresh Xubuntu.

The process is incredibly slow, but seems to make progress. Letting it run overnight.

---

### Post by allebone on 2012-01-25
> **mörgæs said:**
> Thanks for the ideas. Didn't work though, so now I am just installing a fresh Xubuntu.

The process is incredibly slow, but seems to make progress. Letting it run overnight.

Probably suffering from a bad sector crash then.

---

### Post by mörgæs on 2012-01-25
Yes, I was thinking the same. Trying again where I don't use the first 10 GB.

---

### Post by Khayyam on 2012-01-25
> **mörgæs said:**
> [...] Mounting with the command
```
sudo mount -t hfsplus /dev/sda2 /mnt/mac_harddisk
```does not work (gives a generic error).
mörgæs ..

This is unrelated to hfsprogs/hfsutils. You need to have hfsplus support enabled in the kernel for mounting hfsplus volumes. I'm not sure Ubuntu kernels have this by default, but I'm guessing, from the above, this isn't the case. You can check with the following:
```
grep hfs /proc/filesystems
```> **mörgæs said:**
> Since I can't boot MacOS I can't disable the journaling (I believe), and I am afraid to run fsck on the disk while journaling is active.
You can't disable the journal outside of MacOS X, however, here is no need to disable the journal, as long as you mount the disk readonly the journal will be undisturbed. You can run 'fsck.hsplus -n' on readonly and get some idea of what issue there might be before commiting yourself to altering the disk.   

If hfsplus is enabled in your kernel, and your unable to mount readonly, then its either filesystem corruption of some sort or a hardware failure. If this is the case then I'd suggest installing [ddrescue]("http://www.gnu.org/software/ddrescue/ddrescue.html") with which you can make a (complete!) image of the disk, you could then run [fsck.hfsplus]("http://manpages.ubuntu.com/manpages/natty/man8/fsck.hfsplus.8.html") on the image.

It depends somewhat on how important the information you wish to recover is, there are steps you could take should fsck.hfsplus fail to deliver. [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec"), for instance, supports recovering files from HFS+.

HTH ..

INFO: Rescue Disks:
[SystemRescueCD]("http://www.sysresccd.org/Main_Page") or  (probably more to your liking as its Ubuntu based)  [Ubuntu Rescue Remix]("http://ubuntu-rescue-remix.org/").

---

### Post by mörgæs on 2012-01-26
Erasing the drive with [Darik's Boot And Nuke]("http://www.dban.org") and skipping the first 10 GB did the trick. Now Xubuntu is running happily.

---

### Post by AztecGeek on 2013-02-04
I had a FUJITSU 120GB drive failing on a MacBookPro and not allowing to boot or transfer files when the disk was put on "target mode" but finally I was able to recover data.
 
1.-Removed the 2.5 SATA drive and plugged it into a PC and run Steve Gibson's "SpinRite v.6" using level2 (Data Recovery). The process hung at 54.2% after 14 hours. Then I powered down the machines and disconnected the drive.
 
2.- Placed the drive back onto a Mac laptop and run "DataRescue3" from Prosoft Engineering and run data recovery but it was slowing down and hanging due to data read errors/damaged sectors. 
 
3.-On the same Mac; plugged an external Mac formatted drive (FireWire) and booted "DataRescue3" from CD then run a cloning task on the failing drive and used the external drive as the target. The process gave errors and hung at 98% so I had to cancel the operation and shutdown the laptop.
 
4.-Installed "MacDrive6" to a PC running Windows7 and connected the external drive with the cloned image to a PC using the USB interface and the Mac partition was now visible in the "Computer" Explorer. Next. I proceeded to copy the files to another USB drive. Almost 80% of data was recovered saving $500 Dlls. of a LAB disk recovery service! Not bad for a 120GB MHV2120AT hard disk drive that was released in 2005.

---


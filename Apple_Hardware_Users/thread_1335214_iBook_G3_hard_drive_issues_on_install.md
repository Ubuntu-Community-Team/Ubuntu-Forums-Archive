---
title: "iBook G3 hard drive issues on install"
date: 2009-11-23
forum: Apple Hardware Users
---

### Post by Sable683 on 2009-11-23
I have an iBook G3 that is slow as all get out with osX. I really don't like os9, so I figured that I would give Ubuntu a try on this machine. I have been running the live CD for a few hours and man does it fly now. 

So I started install, however, when it got to actually partitioning the hard disk drive, it just stopped saying that I had a bad or corrupt hard disk.

I don't think that this is the case, so how do I mount & re-format or partition the hard disk from inside the Live CD? I tried following this post: [http://ubuntuforums.org/showthread.php?t=24218](http://ubuntuforums.org/showthread.php?t=24218) but it did not work for me. Any help is appreciated!

~John

---

### Post by linuxopjemac on 2009-11-23
```
mkfs.ext4 /dev/sda
```

for sda it could be another one, depending on your system

to check the integrity

```
fsck -pf /dev/device
```

---

### Post by Sable683 on 2009-11-23
I tried the mkfs.ext3 /dev/hda, (along with ext2 & ext4) however, it shows the following:

ubuntu@ubuntu:~$ sudo mkfs.ext3 /dev/hda
mke2fs 1.41.4 (27-Jan-2009)
/dev/hda is entire device, not just one partition!
Proceed anyway? (y,n) y
/dev/hda is apparently in use by the system; will not make a filesystem here!

I tried the partition editor and right now it is showing the following:

Partition    File System     Size           Used     Unused     Flags
/dev/hda1    unknown         31.50 KiB
unallocated  unallocated     8.92 GiB
/dev/hda4    linux-swap      456.90 MiB                         swap

There is a orange triangle with an exclamation point next to "/dev/hda1" and I cannot delete this partition. Also, there is a set of keys next to "/dev/hda4", and I cannot do anything with this partition.

Thanks for the tips and the quick reply!

~John

---

### Post by linuxopjemac on 2009-11-23
cannot you erase and check the disk from a MacOSX cd ? (Utilities in the MacOS installer)

---

### Post by Sable683 on 2009-11-23
I am not sure, I have not tried that yet... I figured I should be able to use the powerpc install cd and just wipe everything out and start from scratch. Also, I am not sure I have the os X disks, the system came with os X installed, but the MacOS 9 disks in the case.

Got to 26% complete on the ubuntu install, then I get an error that says i/o error, either bad hard disk or the optical drive needs to be cleaned (which I did). Also, been running the Live CD for quite a few hours now, with no issues. Could just be a bad hard disk drive... might just upgrade it from the 10GB to something that would have more space.

~John

---

### Post by Sable683 on 2009-11-23
Ok... I tried the Mac OSx disk utility.. now more problems.. it will not boot from the Ubuntu 9.04 PPC Live CD that I had been using. I now get a grey screen with a blue folder with the MacOS logo flashing on it. I did hold the "c" button when I turned it on, but no longer likes this live cd..

~John

---

### Post by linuxopjemac on 2009-11-23
what happens if you hold the Option (or alt) key during boot ? Can you then boot the liveCD ? Cannot you boot the OSX CD and just format your HD in one partition and then try the Ubuntu LiveCD with holding the Option key during boot.

---

### Post by Sable683 on 2009-11-23
I thought I may have figured it out, I did not erase all of the Volumes on the disk, such as the UNIX File System, Mac OS Standard, Mac OS Extended and the MS-Dos File System. I did this and then created 1 whole partition as free space, but I still cannot boot from the LiveCD that I was using earlier. This is getting frustrating! I am downloading the 9.10 powerpc live cd.. maybe that will work!

---

### Post by linuxopjemac on 2009-11-23
burn the iso at low speed, sometimes if you burn at higher speeds, the CD is not workign properly.

---

### Post by Sable683 on 2009-11-23
What I don't get is that the CD was working flawlessly earlier today... go figure...

---

### Post by linuxopjemac on 2009-11-23
really weird indeed, I think there is something wrong with your hardware

---

### Post by Sable683 on 2009-11-23
Just re-install Os X.. the iBook is working fine, downloading the updates. It still will not boot from the LiveCD... and there are no scratches on the disk. Still have like 3 hours before the ubuntu 9.10 iso downloads..

---


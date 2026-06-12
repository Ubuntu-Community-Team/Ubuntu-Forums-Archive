---
title: "I have no OS, and want to install Vista and Ubuntu 7.04"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by steiny on 2007-08-07
Hi all!

I previously had Vista installed, I followed a dual boot "how to" and ended up with GRUB error 21 and no bootable OS. It seemed no one here was able to help me with GRUB error 21 [http://ubuntuforums.org/showthread.php?t=513026]("http://ubuntuforums.org/showthread.php?t=513026")

I took my machine to a LINUX installfest and they couldn't solve the GRUB error, so I have tried to start all over again.

The reason I am posting a new thread, is the installation "how to's" seem to either be for an older version of windows/ubuntu or assume an OS is already installed. Also I get the impression that RAID can make a big difference, but any thread involving RAID has way too much jargon for me (I'm a bit of a noob).

I have 2 80GB SATA HD's, and RAID 0. I'm not sure if it is actual or fake RAID (my mate set it up for me, and I no longer have contact with him) but I can find out if someone tells me how.

Could someone please advise me on which OS to install first, and/or point me to the right thread.

---

### Post by joe.turion64x2 on 2007-08-07
If you have not formatted the hard drive yet then perhaps it is not all lost. Do you have a Ubuntu LiveCD? If you do boot with it and in a terminal (Applications -> System tools) type sudo gparted
 if that program shows your hard disk layout (with Windows partitions and so forth) then I would suggest you to install another Linux. Perhaps PCLinuxOS.2007, if you succeed installing it then it will automatically create another grub and most likely will solve the problem for you.

If you don't mind loosing all your previous data then install Vista first.

Joe.

---

### Post by steiny on 2007-08-07
> **joe.turion64x2 said:**
> If you have not formatted the hard drive yet then perhaps it is not all lost. Do you have a Ubuntu LiveCD? If you do boot with it and in a terminal (Applications -> System tools) type sudo gparted
 if that program shows your hard disk layout (with Windows partitions and so forth) then I would suggest you to install another Linux. Perhaps PCLinuxOS.2007, if you succeed installing it then it will automatically create another grub and most likely will solve the problem for you.

If you don't mind loosing all your previous data then install Vista first.

Joe.

No I have not formatted either of the HD's.

Yup I do have the Live CD (I'm booting off it now)

GParted shows /dev/sda and /dev/sdb. sda is/was where Vista was installed, which had 2 partitions, but now it just shows 74.35GiB unallocated.

At the installfest we tried using several different LINUX distro's to try installing a different GRUB version but it didn't seem to work.

---

### Post by p_quarles on 2007-08-07
I can help you with the basics, at least.

Install Vista first. I've never used dual HDDs, so I don't know if it will install itself on both of them automatically.

In any case, any partitioning you need to do, do that with Vista's system manager. For whatever reason, Gparted has trouble with Vista-created NTFS partitions.

Then, install Ubuntu in the free space. 

If this doesn't work, then, yes, something is funky with your hardware or its setup.

I don't know anything about RAID, but I can point in the direction of a couple of other common problems:
1) Bad install disks. Make sure you check the MD5 number after you download (instructions for this are on the page that pop-ups after you begin the download), and then burn the CD at a slow rate (e.g., 4x). Finally, before you install, select the "Check Disk Integrity" option from the install disk menu. 

2) Graphics drivers. Some cards make for serious installation problems with the live disk. You can almost always get it to work -- with some trouble -- but it's best to use the "alternate" disk (non-live) for the installation. You'll then need to set up the graphics driver with the command line.

---

### Post by skwishybug on 2007-08-07
It is generally accepted practice to install Windows first and Ubuntu second since Windows doesn't play well with others.

---

### Post by joe.turion64x2 on 2007-08-07
> **steiny said:**
> No I have not formatted either of the HD's.

Yup I do have the Live CD (I'm booting off it now)

GParted shows /dev/sda and /dev/sdb. sda is/was where Vista was installed, which had 2 partitions, but now it just shows 74.35GiB unallocated.

At the installfest we tried using several different LINUX distro's to try installing a different GRUB version but it didn't seem to work.
Well, if the hard drive which originally had Windows installed only shows unallocated space then you have nothing else to worry about it, data is lost. The next will be to install Vista first, use its tools to free space for Ubuntu, and install Ubuntu last.

Joe.

---

### Post by steiny on 2007-08-14
Review: I'm getting really odd behavior now and it's starting to f*** me off. I deleted my raid 0 setup and ubuntu installed properly. I tried installing Vista to another partition and it almost finished then froze while testing my pc's performance. I tried again, and no luck (weird seeing as I had Vista working before). I thought maybe it was because I disabled the raid or something, so I re-setup the raid (it is hardware SATA raid btw) and Ubuntu seemed to work, but Vista screwed up again. I managed to restart and it booted straight into Vista but I get an error code while installing updates, and this error is yet to be recorded so no help what so ever. Then Ubuntu stopped working and now I'm back to square one. Anyone know anything about RAID?

---


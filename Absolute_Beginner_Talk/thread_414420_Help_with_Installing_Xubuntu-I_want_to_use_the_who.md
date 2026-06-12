---
title: "Help with Installing Xubuntu-I want to use the whole HD, not partition"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by zazen666 on 2007-04-19
Hi-
I am trying to do a fresh install with Xubuntu.
I want to use the entire disk (I have a small 40gig laptop) and dont want to partition, dual boot, etc.
However,I ran into a problem:
 at step 4 of the installation process, I have two options:
1-resize SCS11 (o,o,o) partition #1 (sda) and use free space
2-guided-use entire disk
I selected 2 and got this error:

"The ext3 file system created in partition #1 of SCSI1 (o,o,o) (sda) failed.

I dont really know what that means. Should I try again, with option 1 and just move it up to 100%. Or what can I do to free my whole HD for Xubuntu?
Thanks very much

---

### Post by siciliancasanova on 2007-04-19
Download the [gparted live disk]("http://gparted.sourceforge.net/livecd.php") and reformat that way.

---

### Post by zazen666 on 2007-04-19
> **siciliancasanova said:**
> Download the [gparted live disk]("http://gparted.sourceforge.net/livecd.php") and reformat that way.


Hey thank you.
Is that the only soultion? I'll need a seperate livecd to combined the partiations? Its not possible via Xubuntu's installation?
thanks again

---

### Post by n3tfury on 2007-04-19
> **zazen666 said:**
> Hey thank you.
Is that the only soultion? I'll need a seperate livecd to combined the partiations? Its not possible via Xubuntu's installation?
thanks again

sometimes the live cd's partioner works fine, other times not.  i've had much better luck with the newest versions of gparted also.

---

### Post by zazen666 on 2007-04-19
Hi guys-thanks for the help.
So, I downloaded the gparted live cd, and booted it up.
I get this:

Patition:          
dev/hda1            ext3                               35.82gigs
dev.hda2            extended                         1.44
dev/hda5            linux-swap                       1.44

I am totally unsure what to do next. do I just move hda1 over to 100%? do I need to leave the linux swap alone? I am new at this, so can you walk me thru it?
thanks

---

### Post by kittyhawk63 on 2007-04-20
> **zazen666 said:**
> Hi guys-thanks for the help.
So, I downloaded the gparted live cd, and booted it up.
I get this:
I am totally unsure what to do next. do I just move hda1 over to 100%? do I need to leave the linux swap alone? I am new at this, so can you walk me thru it?
thanks

This may help.
[http://lifehacker.com/software/partition/how-to-modify-your-partitions-for-free-using-gparted-230420.php](http://lifehacker.com/software/partition/how-to-modify-your-partitions-for-free-using-gparted-230420.php)

---

### Post by lamalex on 2007-04-20
the easiest way is just pick manual partitioning, delete all the current partitions, then make a new one as ext3  and /(root) mount point and finish your install

---

### Post by kittyhawk63 on 2007-04-20
> **Iamalex said:**
> the easiest way is just pick manual partitioning, delete all the current partitions, then make a new one as ext3  and /(root) mount point and finish your install

I need to partition my Windows hard drive, not my Linux hard drive.
Can I **partition** the Windows hard drive **using **Linux?
kh
Edit: I've gone to a new thread and left this to sasen666. It is his thread.

---

### Post by zazen666 on 2007-04-20
> **Iamalex said:**
> the easiest way is just pick manual partitioning, delete all the current partitions, then make a new one as ext3  and /(root) mount point and finish your install

Hi-I tired this but when I click "next" I just get an error message "no root file system is defined"

What can I do? Also, I am not sure that this is the right thing to do? Everything I have read above seems to say I need a dedicated swat file of about 1.5 gigs.
Thanks

---

### Post by Brendantb on 2007-04-20
Hi, 

for what it's worth, I have a 40gb hard drive and am running Xubuntu. I have about 8gb for /, 500mb for a swap partition, roughly three times RAM, and the rest is /home. The utility of this type of layout is that I can upgrade the os in / without affecting data in /home. 

I have never had any problems using the partitioning tool on the Xubuntu distro, although due to my poor RAM overhead, I have to use the alternative CD. If you have nothing of value on the hard drive, you can select manual partition option and delete any existing partitions, then create the new ones that you need.

---

### Post by zazen666 on 2007-04-20
I got it working, thanks a lot

---

### Post by Slackpacker on 2007-04-21
How did you get it to work?  Once you make new partitions in gparted, how do you convince the Xubuntu installer to install there?  I'm in zazen's situation... I wonder if the problem is that Xubuntu seems to want sda, but the drive is hda?  I actually deleted the partitions in gparted and tried to just use the whole disk in Xubuntu, but it gives me the same error again.

---


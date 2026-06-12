---
title: "HELP!!!! I killed my OS! (OS X)"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by WillJeffery on 2008-01-17
Ok. First my computer is a MacBook 2.2Ghz.

I installed Ubuntu succesfuly (I'm using it right now), and rebooted. The screen stayed gray, so I rebooted again holding Alt/Option. This time one drive came up called "Windows". I boot off that, and Ubuntu boots. Ubuntu is running great (minus the fact that I can't figure out the ******* wireless), but I can't boot into OS X.

I fear the in the partitioning process Ubunutu wrote zeroes over my OS X install. I PRAY that my data is still that and that it wasn't written over by Ubuntu, but who knows.

If anyone can help me that would be GREATLY apprieciated. 

Should I go to a data recovery center? All my work, my music, my entire life is on this computer, and if I loose it I will be very.......... sad.

:confused:

Hopeful,

Will Jeffery



NOTE: You can contact me via MSN, AIM, or email. Just send me a PM. Cheers.

---

### Post by Dynaflow on 2008-01-17
I'm not terribly familiar with Macs, but this sounds more like a problem with a boot loader than with overwritten partitions.  How exactly did you go about installing Ubuntu on your Mac?

---

### Post by WillJeffery on 2008-01-17
I followed the steps from here: [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

During the parition process a window poped up saing something about a swap partition or something. I don't know if that means anything but, there you go.

---

### Post by Dynaflow on 2008-01-17
A swap partition is an "extra" partition that you can sort of think of as the RAM's overflow basin.  It's standard to have one in Linux, and the installer will create one alongside your Ubuntu installation if you don't already have one.

When you did the install, did you say to the installer, "Use the whole hard drive" [which would be a bad thing in your case], or did you choose the option that says something like, "Resize existing partition and use the resulting free space" [you're probably in the clear]?

If you did the latter, we just have to figure out why OS X is reluctant to boot and how to persuade it to do so.  I'm wondering, can you find your OS X partition through Nautilus (type "sudo nautilus" sans the quotation marks in the terminal, go to Filesystem, and then go to -- I think for Macs too -- Media)?  If you can, now's as good a time as ever to go out and buy a USB hard drive and back up your data, which you should be able to grab from the other partition through Ubuntu.  Never entrust everything to just one hard drive on one computer, even if you aren't redoing partition tables and the like.  That advice comes from experience.  :?

[Oh, you may want to edit your first post to take your personal info off the open, public forum, since you never know who or what may stumble upon it.]

---

### Post by Dynaflow on 2008-01-17
Hmmm...  I've been looking through the tutorial you linked to.  Did you decide to install rEFIt?

Also, did you have any other OSes, like Windows, installed onto that machine?

---

### Post by WillJeffery on 2008-01-17
The latter, I'm pretty sure. I assume this becuase when I set up the partion it asked me how much space I wanted (something like that) and I input: 10420 MB (or 10GB). So is that good or bad or dunno?

The only thing in File System/Media are two 'cdrom' thingers which I 'got info' on and was around 690MB so that tells me is just the Gusty install disk.

I have a firewire drive that has most of my data backed up, but not recent enough to have some really important stuff.

So yeah, I think I did that latter.

---

### Post by shadowh511 on 2008-01-17
Dude, that kills ALL of your data

---

### Post by Dynaflow on 2008-01-18
What do you get in the terminal from ```
cat /etc/fstab
```?

---

### Post by WillJeffery on 2008-01-18
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=aa69adac-87dd-4310-ba40-36ec764220cc /               ext3    defaults,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by Dynaflow on 2008-01-18
> **shadowh511 said:**
> Dude, that kills ALL of your data

Could you please explain what "that" is?

---

### Post by Dynaflow on 2008-01-18
> **WillJeffery said:**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=aa69adac-87dd-4310-ba40-36ec764220cc /               ext3    defaults,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

One hard drive partition...

From the installation, do you remember if or how you did this bit from the instructions?:

> 
Install Ubuntu as usual, except:

    *      In the partitioner, select Manually edit partition table
    *      Delete /dev/sda3 and /dev/sda4 if they exist
    *      Create a new ext3 partition for your root
    *      Mount the newly created ext3 partition on '/'
    *      Note that Boot Camp will cause problems if you make more than two partitions in total.



Take me through what you did, step by step, as you remember it.

---

### Post by Dynaflow on 2008-01-18
Also, what do you get from ```
sudo fdisk -l
```?

---

### Post by WillJeffery on 2008-01-18
Boot from CD.
D-Click Install from Ubuntu Desktop.
Go through the Language, time, keyboard, etc.
When the very first mention of partioning came up, i said "Manually"
Deleted partions /dev/sda3 and 4
New partition table
"you have selected en entire devie to partition if you proceed......." -> continue
new partition
-Primary
-10420 MB
-begining
-ext3
"OK"
then i think it asks me where i wanted this partition so i said "/" (as per the tutorial)
then the swap thingy came up.

-----------------------------------------------------------------------
willjeffery@willjeffery-ubuntubook:~$ sudo fdisk -1
[sudo] password for willjeffery:
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by Dynaflow on 2008-01-18
----------------------------------------------------------------------
willjeffery@willjeffery-ubuntubook:~$ sudo fdisk -1
[sudo] password for willjeffery:
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors[/QUOTE]

That's actually a lower-case "L" (for "list") at the end of ```
sudo fdisk -l
```

---

### Post by nikoPSK on 2008-01-18
you could of accidentally overwriten the disk... try testdisk please. :)

---

### Post by Dynaflow on 2008-01-18
Contingent on what that command returns, I think it's fairly clear what happened.

I'm sorry to say it, but nikoPSK is probably right.  > "you have selected en entire devie to partition if you proceed......." -> continue...  would have essentially given the installer orders to delete you entire OS X partition.  

It wouldn't have paved over it entirely, since you only asked it to format a 10 gig Ubuntu partition, plus a few more gigs as swap.  The problem is that whatever data was stored on the area of the disk formatted for Ubuntu (the first 10GB and the last 2-4GB, probably) would be lost, and the filesystem that told your computer where to find and how to piece together your files stored elsewhere on the disk would be totally FUBAR.  

This actually happened to me the first time I tried to install a dual-boot Linux system (Mandrake 8.2 vs. Windows Me).  I lost three in-progress term papers, a truckload of saved PDFs of journal articles, about half a gig of music I'd accumulated since my last, CDR-based backup, scads of e-mails, and God knows what else.  It was pretty heartbreaking at the time, but it proved to be a learning experience worth its metaphorical weight in gold, and I ended up a great fan of Linux.  It makes me sad to see someone going through the same thing, but I hope you find a silver lining somewhere in this.

Here are your options:

*If there is absolutely irreplaceable stuff on that drive that *must* be recovered, and you feel it is worth the expense, someone with computer forensics knowledge or a good data-recovery person might be able to pull out whatever data wasn't directly in the path of the disk formatting.  Maybe.  If you're going this route, do *nothing* more with the partitions until someone with the right tools and knowledge can have a crack at the drive.  I don't know what your odds will be, but they will probably be unfavorable.

*If you are resigned to losing the data, you can either expand the Ubuntu partition to fill the rest of the drive and fully join us in the ranks of the Happy Penguin Hordes, reinstall OS X from scratch with whatever recovery media you got with the Macbook and just stick with one operating system for the time being, or you could reinstall OS X, give the installation instructions for Ubuntu another try (making sure you're not asking the installer to use the whole disk), and have yourself a bona-fide, dual-boot system.  

Give this thread another day or two before you do anything, though, because someone better versed in the intricacies of Macs or of the finer points of hard-drive partitioning might have a better idea on how your data (what of it is still extant) might be rescued.

I wish you the best of luck.

---

### Post by WillJeffery on 2008-01-18
Thanks for all the help from everyone. It is greatly apprieciated. What I think I'm going to do is get as much of my data back as possible then move to a dual OS X/Ubuntu boot. Being a full time student I don't really have time to learn a whole new OS all over again.

Thanks again.

---


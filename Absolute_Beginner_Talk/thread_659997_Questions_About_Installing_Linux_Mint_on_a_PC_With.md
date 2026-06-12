---
title: "Questions About Installing Linux Mint on a PC With 2 Hard Drives"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Crumpets and Jam on 2008-01-06
Alright. I am going to install Linux Mint on my younger brothers computer.

Pentium 4 2.00 GHz
512 MB

It has 2 hard drives around 30 GB each. One of them has Windows XP on and the other has Windows's page file and some multimedia files.

I am going to install Linux Mint on the Windows drive by booting in to the Linux Mint Live CD and selecting this drive as I progress though the installation steps. This will format that drive and leave me with a fresh Linux Mint install.

I want to format the second drive with the random files on too so that it is just blank. How can I do this? Thanks guys.

P.S. Linux Mint looks really promising. I've only used it from the Live CD so far but it picked up all my hardware.

---

### Post by laidback on 2008-01-06
During installation you get asked questions re hdd locations etc. Assuming Linux Mint is the same as Ubuntu you can opt for a manual  rather than auto type of hdd selection and partitioning. If you go for the manual you should be able to select and set up as you wish. Remember that you'll need a /root and /swap partition as minimum. The installation will also install Grub which handles the dual boot up.
Linux Mint have their own web site/forum which may help. Make sure you have backups of valuable windows areas first. Searching on this site will also give you more info on dual booting.

---

### Post by Crumpets and Jam on 2008-01-06
> **laidback said:**
> During installation you get asked questions re hdd locations etc. Assuming Linux Mint is the same as Ubuntu you can opt for a manual  rather than auto type of hdd selection and partitioning. If you go for the manual you should be able to select and set up as you wish. Remember that you'll need a /root and /swap partition as minimum. The installation will also install Grub which handles the dual boot up.
Linux Mint have their own web site/forum which may help. Make sure you have backups of valuable windows areas first. Searching on this site will also give you more info on dual booting.

I don't want to dual boot. I just want to formatted drives but one with Linux Mint on.

---

### Post by Crumpets and Jam on 2008-01-06
Sorry for rudely bumbing this up but I have plans to install tonight. Any help is welcome.

---

### Post by ajgreeny on 2008-01-06
If you are getting rid of XP, then no problem, just chose the appropriate disk at partitioning point in the install and use the whole disk.  The XP will be reformatted and all should go smoothly.  You won't even need to manually set up a swap as the installer will do this automatically for you.  The installer is almost exactly the same as Ubuntu, not surprising as the distro is also very similar, it just looks different and installs all codecs and plugins that you would probably need to do yourself in Ubuntu later.

The only thing that might make things easier in future upgrades of the version of Mint, is to have a separate /home partition.  To do this chose manual at partitioning and you can then do that if you want.  Probably easiest to stick with the default until you understand linux better, then next time perhaps use /home separately.

---

### Post by Crumpets and Jam on 2008-01-06
> **ajgreeny said:**
> If you are getting rid of XP, then no problem, just chose the appropriate disk at partitioning point in the install and use the whole disk.  The XP will be reformatted and all should go smoothly.  You won't even need to manually set up a swap as the installer will do this automatically for you.  The installer is almost exactly the same as Ubuntu, not surprising as the distro is also very similar, it just looks different and installs all codecs and plugins that you would probably need to do yourself in Ubuntu later.

The only thing that might make things easier in future upgrades of the version of Mint, is to have a separate /home partition.  To do this chose manual at partitioning and you can then do that if you want.  Probably easiest to stick with the default until you understand linux better, then next time perhaps use /home separately.

Thanks for your response.

I understand all this. I want to erase everything on the **second** hard drive disk. The one that won't have Linux Mint installed.

Thanks again.

---

### Post by maybeway36 on 2008-01-06
If you don't need to put files on it, just use the manual partitioning to take off the partition on the 2nd drive, and make your Mint partitions on the 1st drive.
If you do want to use it for storage, make the 2nd drive have an ext3 or reiserfs partition.

---

### Post by Crumpets and Jam on 2008-01-06
> **maybeway36 said:**
> If you don't need to put files on it, just use the manual partitioning to take off the partition on the 2nd drive, and make your Mint partitions on the 1st drive.
If you do want to use it for storage, make the 2nd drive have an ext3 or reiserfs partition.

How would I do this?

Thanks.

---

### Post by Crumpets and Jam on 2008-01-06
I'm sorry for being so pushy on the matter. I'm a noob and I need to learn about this. Everyhting I have found on the web is very complex for someone who is just starting.

---

### Post by rubicon on 2008-01-06
I understand your haste, so I'll try to clear situation a bit.

Assuming linux mint is somewhat ubuntu-like, I guess it uses the same LiveCD installer, e.g. Ubiquity. Ok, you run "Install" from desktop of live-session and it -- after some tweaking -- brings you to disk partition page.

There, you can select "Manual partitioning" (or something like that, I'm not sure about exact phrase -- I used localized version of CD and that was pretty long ago, but let's go back to partitioning). It should show your both HDDs. Select "New partition table" from context menu for the first drive, then for the second. 

Then you should make two or three partitions on the first drive to install Linux on it (I suppose you know how to do it since you run openSUSE), and one partition on the second drive. Select ext3fs or reiserfs as suggested above and pick "mount point" as something like '/media/stuff'.

**This will format both drives (YOU WILL LOSE ALL DATA ON THEM!), install Linux Mint on the first, and will give you some free space for "stuff" on the second ;)**

Is this what you want to do? Did this help?

---

### Post by Crumpets and Jam on 2008-01-06
> **rubicon said:**
> I understand your haste, so I'll try to clear situation a bit.

Assuming linux mint is somewhat ubuntu-like, I guess it uses the same LiveCD installer, e.g. Ubiquity. Ok, you run "Install" from desktop of live-session and it -- after some tweaking -- brings you to disk partition page.

There, you can select "Manual partitioning" (or something like that, I'm not sure about exact phrase -- I used localized version of CD and that was pretty long ago, but let's go back to partitioning). It should show your both HDDs. Select "New partition table" from context menu for the first drive, then for the second. 

Then you should make two or three partitions on the first drive to install Linux on it (I suppose you know how to do it since you run openSUSE), and one partition on the second drive. Select ext3fs or reiserfs as suggested above and pick "mount point" as something like '/media/stuff'.

**This will format both drives (YOU WILL LOSE ALL DATA ON THEM!), install Linux Mint on the first, and will give you some free space for "stuff" on the second ;)**

Is this what you want to do? Did this help?

The installation is pretty much exactly the same for Linix Mint and Ubuntu. Thanks for the response.

You said to 'make two or three partitions on the first drive to install Linux on it'. Why do I need two or three partitions?

Thanks for helping.

---

### Post by rubicon on 2008-01-06
I'm assuming you want to create partitions all-by-yourself.

*All: feel free to fix me here, as I'm not such a pro in this question.*

My advice is to: 
1. make / partition (5-10GiB, ext3 or reiser),
2. make swap partition (1GiB, swap),
3. make /home partition (all unused space, _ext3_ or reiser). 

The order is slightly have some meaning. Swap partition is overall faster when created near to disk's inner cylinder, e.g. near from the beginning.

---

### Post by laidback on 2008-01-07
Linux Mint is derived from Ubuntu, is very much like it but has a different desktop and provides restricted codecs at install. I believe that some (all) Ubuntu repositories are used.

I deduced that you intended to keep your XP system on disc 1 and install Linux Mint on disc 2, that would be a dual boot. However, the above is implying a new install with all existing data and XP deleted. Are you sure?

---

### Post by Crumpets and Jam on 2008-01-08
> **laidback said:**
> Linux Mint is derived from Ubuntu, is very much like it but has a different desktop and provides restricted codecs at install. I believe that some (all) Ubuntu repositories are used.

I deduced that you intended to keep your XP system on disc 1 and install Linux Mint on disc 2, that would be a dual boot. However, the above is implying a new install with all existing data and XP deleted. Are you sure?

Yeah. The above thing is what I wanted to do.

---


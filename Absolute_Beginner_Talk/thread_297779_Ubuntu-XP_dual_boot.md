---
title: "Ubuntu-XP dual boot"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by nonpareilpearl on 2006-11-11
I am working on installing Ubuntu and having my first go at Linux, after watching some of the guys I work with do so many cool things with it :)

I already posted about what file format I should be using for the boot sector, and apparently that is ext3.

I was talking to one of the guys I work with and I am now a little confused, since although I do understand most of what he was saying, I'm not entirely sure how to implement it. Here's the basics:

- I want to dual boot WinXP with Ubuntu
- I was told I have to use Linux as the default boot sector do to this, that Windows doesn't support dual boot with non-Windows (no surprise there... :P)

Now here is where I get a little confused (for the record I have 1 Gig of RAM and a 250 Gig hard drive):
- I need to create at least three Linux partitions: boot, root, and swap (?)
- The swap needs to be 2x the amount of memory I have or not much more than 2 Gigs and of a specific file format (forgot what that was)
- The boot should be ext3 (check)
- The root should be reiserfs

Also for whatever reason my hard drive's two partitions (a 30 Gig boot sector and 220 remaining) show up as three when viewed through a command he used in the terminal. There's sda1, or the Windows boot, and sda2 and sda5, with sda5 being embedded within sda2 and they are both of equal size (i.e. both approx. 220 Gigs). He said I might want to try using GParted on my Ubuntu Live CD to make six partitions... and I'm just a little lost. I want to partition it such that I have the three necessary boot partitions, but he recommended destroying sda2 and sda5 and creating sda2, sda3, and sda4 partitions with sda5 and sda6 embedded in sda4. But I don't want to loose all the data (files etc.) that are on the sda2/sda5 unit. Is there any way to create the 6 partitions (and they do sound like a good idea) without reformatting the whole 220 Gig portion?

Sorry so long... thanks to whomever can respond :)

---

### Post by ner0tic on 2006-11-11
with ubuntu all you really need are 2 partitions, and GRUB the linux bootloader will auto detect your pre-existing XP isntall and add it to the boot list.

---

### Post by nonpareilpearl on 2006-11-11
Well the three partitions sounded like a good idea because I think keeping the boot and data separate, although I'm not 100% sure what the swap partition is for.

---

### Post by Sef on 2006-11-11
Read the [Illustrated Daul Boot]("http://users.bigpond.net.au/hermanzone/").

> Now here is where I get a little confused (for the record I have 1 Gig of RAM and a 250 Gig hard drive):
- I need to create at least three Linux partitions: boot, root, and swap (?)
- The swap needs to be 2x the amount of memory I have or not much more than 2 Gigs and of a specific file format (forgot what that was)
- The boot should be ext3 (check)
- The root should be reiserfs

Not necessary to have separate boot partition. Just set root to be bootable.

Root should be either ext3 or reiferfs.

With a gig of ram, swap is not necessarily needed.  It is if you do a lot of video instensive games or movie making.  Just for internet, wordprocessing, it is not needed.  Swap has its own file format.

Basically with a XP dual boot, you would like these partitions:

XP - NTFS
Ubuntu - Ext3 or reifers
swap - swap
Share - FAT32, ext2, or ext3
home - ext3 or reiferfs

---

### Post by nonpareilpearl on 2006-11-11
> **Sef said:**
> 
Basically with a XP dual boot, you would like these partitions:

XP - NTFS
Ubuntu - Ext3 or reifers
swap - swap
Share - FAT32, ext2, or ext3
home - ext3 or reiferfs

I am assuming the share is for both Windows and Ubuntu to access if necessary, is this correct? I didn't think Windows would support ext2 or ext3. Also would any of these partitions require destroying the sda2/sda5 combo?

---

### Post by Sef on 2006-11-11
> I am assuming the share is for both Windows and Ubuntu to access if necessary, is this correct? I didn't think Windows would support ext2 or ext3. Also would any of these partitions require destroying the sda2/sda5 combo?


Yes, the FAT32, ext2, or ext3 is for sharing files.  Nothing should be destroyed, but **back up** your data.  Nothing is 100% guaranteed.

---

### Post by nonpareilpearl on 2006-11-11
Thanks a bunch! I've actually been backing up my data while reading and posting :) When I'm done with all that I'm going to move to starting to put Ubuntu on.

---

### Post by Bartender on 2006-11-11
Take a look at [aysiu's]("http://www.psychocats.net/ubuntu/installing") page, where he maps out installing Ubuntu and dual-booting with Windows.
I don't know what your friends meant by "have to use Linux as the default boot sector".  If anything, you want Windows already on the HDD.  It's simpler to create a new partition for Linux "after" the Windows partition then it is to install Linux first, then Windows.
When done right, you basically leave the Windows install alone, except for the GRUB bootloader tweaks the Windows master boot record (the small amount of data at the very beginning of the HDD) so that instead of booting straight to Windows you get a menu asking which OS you wish to start.  It's simple once you've seen it, but of course a little bit scary if you've never done it before.
You only need to create one partition for Linux.  However, you'll end up with 2 partitions when finished because Ubuntu will create a swap partition from the space you give it, and it will choose a size that works for you.  If you've got a gig or more of RAM, there's a good chance Ubuntu will rarely if ever use the swap.  So it's not a big deal.  Some folks recommend making a separate partition for /home, but it's not critical and you could do that later if you decided you really wanted it.
Have you got broadband?  Download [GParted]("http://gparted.sourceforge.net/livecd.php")and make a CD out of it.  You can do the download and make the CD on a Windows PC.  Then toss the CD in your optical drive and boot from it.  GParted is a neat partitioning tool that will show you in a graphical interface what, where, and how many partitions you have.  That way you won't be wondering if you have 2 or 3 partitions.
Oh, OK, sounds like you've already installed Ubuntu?  The sda2 and sda5 you refer to make perfect sense.  Ubuntu's partitioning tool will only make four primary partitions.  It saw Windows as the first partition (sda1), made Ubuntu the second partition (sda2) and made the swap as a logical partition inside of Ubuntu's primary partition.  Swap was labeled sda5 because the partitioning tool leaves sda3 and sda4 unreserved in case you want to make 2 more primary partitions.  Was that clear as mud?
Take a look at the rest of aysiu's website - he's got lots of neat guides on there.  You'll have to do some tweaking to get Ubuntu to see your Windows partition, and aysiu has the directions for that too.

---

### Post by nonpareilpearl on 2006-11-11
Actually I haven't installed yet, I've been using an Ubuntu Live CD, which has GParted on it. I was looking at it, but since I hadn't finished backing stuff up yet I didn't mess around with it.

---

### Post by Sef on 2006-11-11
You might want to get [GParted]("http://gparted.sourceforge.net") itself.  It is a graphical installer and then you can simply put the partitions where you want them.
.
Read the illustrated dual boot (link above) or [Installing Windows]("http://www.psychocats.net/ubuntu/installing").

---

### Post by Bartender on 2006-11-11
If you didn't install Ubuntu, where did the sda2 and sda5 you refer to come from?

---

### Post by Velotix on 2006-11-11
> I didn't think Windows would support ext2 or ext3.

It doesn't, but Windows doesn't support most things until you add third-party software, which is the case here as well.

[Ext2/3 IFS for Windows](http://www.fs-driver.org/)

There are a number of reasons for using ext3 over FAT32, the best reason being that FAT32 is somewhat unreliable (it was the file system for Win9x - 'nuff said) whilst ext3 is about as reliable as NTFS, i.e. very.

I hear that the driver in the link has a few issues but nothing that should bother you. If you want something that will definitely work properly in both Linux and Windows go with FAT32 but be prepared to experience data loss for no good reason every once in a while.

*is reminded of the three-hour ScanDisk sessions with my old Athlon Thunderbird machine and Win98SE*

---

### Post by Timokl on 2006-11-12
> **nonpareilpearl said:**
> 
Now here is where I get a little confused (for the record I have 1 Gig of RAM and a 250 Gig hard drive):
- I need to create at least three Linux partitions: boot, root, and swap (?)
- The swap needs to be 2x the amount of memory I have or not much more than 2 Gigs and of a specific file format (forgot what that was)
- The boot should be ext3 (check)
- The root should be reiserfs


As said already, you can choose either ext3 or ReiserFS. I use ext3, and it works perfect for me.

One advice, that saved myself from a lot of trouble. Set up another partition for /home - this is where the personal files of all users of your computer go.

This way, you can easily re-install Ubuntu easily, and still use your old preferences for applications automatically. That's so cool, try that with Windows! Upgrading to Edgy with a clean install was piece of cake. All I had to do was install the applications that don't get installed by default. But that was merely some line of apt-get, and time for a coffee during the download time. :-)

Good luck with your installation!

Bye from Bangkok,
Timo

---

### Post by gtdaqua on 2007-09-03
I wanted to install Ubuntu on my XP machine (XP became painfully slow everytime I update)

But just wanted keep XP as backup. I was reading all these topics and how to get the dual boot done - boy! most of the steps were so complex and I thought 'why take all this pain, add an entry in grub to keep xp and all'. 

So I just installed ubuntu 7.04 on a fresh partition in my IDE HDD. Guess wat? I didnt change a single configruation nor tell Ubuntu that XP was there - but the boot loader after installation showed all options available for booting!!! Ubuntu, Ubuntu Recovery, memtest and Windows XP Professional! I was amazed - because everything was automatic! 

I can see this an old thread but things have improved since then I guess! Yet another Congrats to the Ubuntu 7.04 team!!

---

### Post by gtdaqua on 2007-09-03
I wanted to install Ubuntu on my XP machine (XP became painfully slow everytime I update)

But just wanted keep XP as backup. I was reading all these topics and how to get the dual boot done - boy! most of the steps were so complex and I thought 'why take all this pain, add an entry in grub to keep xp and all'. 

So I just installed ubuntu 7.04 on a fresh partition in my IDE HDD. Guess wat? I didnt change a single configruation nor tell Ubuntu that XP was there - but the boot loader after installation showed all options available for booting!!! Ubuntu, Ubuntu Recovery, memtest and Windows XP Professional! I was amazed - because everything was automatic! 

I can see this an old thread but things have improved since then I guess! Yet another Congrats to the Ubuntu 7.04 team!!

---


---
title: "ERROR 18, help!!"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by bobby_b on 2007-03-14
ok here is the deal, i bought a new hard drive for an old (but still very capable) computer, i installed unbuntu 6.06, it worked fine off the disk, after I installed it the full version from the desktop icon, i was asked to either continue using the cd, or restart.  If i was going to restart i needed to take out the disk, so... I did that and when my computer booted up while reading the hard drive, it stopped and said ERROR 18.  i tried reinstalling the OS again, but with the same result. Please help! thanks

bobby

---

### Post by alienexplorers on 2007-03-14
Boot from the liveCD and when you get your main screen enter the Terminal and type:

sudo grub
you will then enter the grub editing program
enter : find /boot/grub/stage1
you will get a set of numbers like so (hd0,0)
enter : root (hd0,0) using the string you got from the first command
enter : setup (hd0)
quit

reboot

---

### Post by rsambuca on 2007-03-14
I am not sure that is the problem here (although it could be).  Grub often gives an error 18 if the hard drive being accessed is larger than the Bios can handle.

If the previous instructions don't work, you will probably have to update the Bios for your motherboard.

---

### Post by bobby_b on 2007-03-14
ok i was able to do all that which you suggested, it didn't solve my problem though, i got an output of something to this effect:

checking if "/boot/grub/stage1 exsists.....yes
checking if "/boot/grub/stage2 exsists.....yes

--omitted some lines--

running "embeded /boot/grub/e2fs_stage1_5 (hd0,0) .....failed (but not fatal)

then the last line said successful, so i trued rebooting but got the same result, any other suggestions.

---

### Post by rsambuca on 2007-03-14
Go to your motherboard manufacturer's website and download the newest bios.  Should do the trick.  Just make sure you follow the instructions very carefully when you upgrade the bios.

---

### Post by jook on 2007-03-15
I also get an error 18. Ubuntu is the second OS installation in an anttempt to make a dual-boot. I was only able to get past the error by booting with a super grub CD that my dad had.  I'm typing in XP right now.  I havent tried going back into ubuntu yet, but when the computer is booting it at least tries to go from CD before hard drive, so i assume that i could get back to the live cd.
I installed ubuntu on a 60-gig new partition on my secondary hard drive (400gig)
aida32 tells me that the BIOS i have installed is from 2003, the one i see on the motherboard manufacturer's website is version 1.0 from 2002.
Shall I try the suggestion from the second post, or what?
This is my first time doing anything with linux.

---

### Post by bobby_b on 2007-03-15
THANKS FOR ALL THE HELP GUYS!!! i tried some more internet searching, and playing around with the harddrive and i figured it out.  I reinstalled it and just made a 50MB partition for the /boot, figuring that it wouldn't need to search the entire 320gig harddrive to find it, and presto! she worked, now she's runnin great!, todays adventure will be networking it with a windows machine!  THANKS AGAIN!

bobby b

---

### Post by jook on 2007-03-17
ubuntu@ubuntu:~$ find /boot/grub/stage1
find: /boot/grub: No such file or directory

What should I do?

---

### Post by rsambuca on 2007-03-17
You have to enter grub first by entering ```
sudo grub
```and then yuor find command.

---

### Post by jook on 2007-03-18
grub> find /boot/grub/stage1
 (hd1,6)

grub> root (hd1,6)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+15 p (hd1,6)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.



*reboot*


Verifying DMI Pool Data......
Boot from CD: Failure...
Boot from CD: Failure...
GRUB Loading Stage 1.5.


GRUB Loading, Please Wait...
Error 18



I don't know if it makes a difference to help my problem, but I see now that I never posted that I'm using Ubunto 6.10, rather than 6.06, as was the person who started the topic.

---

### Post by confused57 on 2007-03-18
> **jook said:**
> I also get an error 18. Ubuntu is the second OS installation in an anttempt to make a dual-boot. I was only able to get past the error by booting with a super grub CD that my dad had.  I'm typing in XP right now.  I havent tried going back into ubuntu yet, but when the computer is booting it at least tries to go from CD before hard drive, so i assume that i could get back to the live cd.
I installed ubuntu on a 60-gig new partition on my secondary hard drive (400gig)
aida32 tells me that the BIOS i have installed is from 2003, the one i see on the motherboard manufacturer's website is version 1.0 from 2002.
Shall I try the suggestion from the second post, or what?
This is my first time doing anything with linux.
Here's some possible solutions for grub error 18:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)

Boot up your live cd, open a terminal, & post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

Does Windows boot from grub?

---

### Post by rsambuca on 2007-03-18
Try setup (hd0) instead of (hd1).

---

### Post by jook on 2007-03-19
@confused57:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 163.9 GB, 163928604672 bytes
240 heads, 63 sectors/track, 21175 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       10565    79871368+   7  HPFS/NTFS
/dev/hda2           10566       21175    80211600    7  HPFS/NTFS

Disk /dev/hdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       16575   133138656    7  HPFS/NTFS
/dev/hdb2           16576       48641   257570145    f  W95 Ext'd (LBA)
/dev/hdb5           24225       48641   196129521    7  HPFS/NTFS
/dev/hdb6           16576       16706     1052194+  82  Linux swap / Solaris
/dev/hdb7           16707       24224    60388303+  83  Linux

Partition table entries are not in disk order




Grub doesnt even boot from grub. I can boot windows from the super grub CD, or I can boot ubuntu from the live CD. I've never been able to boot the installed version of ubuntu.







@rsambuca:

grub> find /boot/grub/stage1
(hd1,6)

grub> root (hd1,6)

grub> setup (hd0) 
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd1,6)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.



*reboot*


Verifying DMI Pool Data......
Boot from CD: Failure...
Boot from CD: Failure...
GRUB Loading Stage 1.5.


GRUB Loading, Please Wait...
Error 18



...I really appreciate your patience and suggestions

---

### Post by jook on 2007-03-19
deleted, appended to previous post.

---

### Post by confused57 on 2007-03-19
Do you get a grub menu, if you boot first to your Ubuntu hdb drive?

IF you do, highlight the Ubuntu entry, press "e" to edit, then change the root from (hd1,6) to (hd0,6), then press "b" to boot.

The Super Grub Disk is capable of restoring your Windows code IPL to your hda mbr...you might want to do this, then try reinstalling Ubuntu to your hdb, setting hdb to boot before hda in bios.

Then you could add an entry to your menu.lst to boot Windows.

I'm not sure if you can have 2 extended partitions on one hard drive, but you "might be able to set up another extended partition with ext3 filesystem(would be designated hdb3), then set up logical partitions within this extended partition for your root & swap...like I said, I'm not sure about 2 extended partitions on 1 hd.  This is pure speculation on my part, hopefully booting first to your hdb drive will help.  Depends on how flexible you are in being able to repartition your hdb drive...e.g. have an extended partition near the front of hdb with root & swap & possibly make the NTFS partition a primary partition?  Possibly making the root partition a primary partition, in other words, I'm not sure what it'll take partition-wise...usually the closer to the beginning of your partition table Ubuntu is installed, the better chance of getting it to work.

I do think your best bet to get Ubuntu working  would be to boot first to your Ubuntu hdb drive...if you can repair your Windows drive to boot independently, then you'd always be able to boot into Windows by changing the boot order in bios.

The GAG boot manager is also another possibility, it can be used as a boot floppy or cd or can be installed to your hd mbr...to be able to boot Linux, grub needs to be installed to the root partition(hd1,6):
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
see the index GAG section

In fact, I'd try GAG if booting first to hdb doesn't work & you're considering reinstalling Ubuntu...install grub to the root partition(first set hda to boot before hdb in bios), using the live cd:
root (hd1,6)
setup (hd1,6)
quit

then see if a GAG floppy or cd  will boot Windows & Ubuntu...if it does you can install GAG to your Window's mbr & use it to boot both OS.

I'd definitely consider repartitioning(if it is even feasible for you) as a last resort...

The gparted live cd is a great  partitioning tool for Linux:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)
you'd have to use a Windows partitioning tool to create a NTFS partition.

---

### Post by jook on 2007-03-20
I'm afraid I understood very little of that... :(

---

### Post by confused57 on 2007-03-20
> **jook said:**
> I'm afraid I understood very little of that... :(

It's a lot of information to hit you with all at one time & I probably wouldn't have understood a word of it when I was just beginning Ubuntu.

Are you able to go into your bios setup and change the boot order of your hard drives?  If so, you might try setting your slave drive to boot before your master drive, you've installed grub to the slave drive mbr by setup (hd1) & it might be worth a try to see if you get a grub menu by booting to your slave drive first.  If you do get a grub menu, see my last reply for editing & trying to boot Ubuntu.

As I mentioned, the Super Grub Disk has an option to restore the Windows mbr on your master drive, so that you'll be able to boot Windows normally.  If you have a Windows install cd(not a recovery cd), you boot up your pc with it, press "r" for recovery, then enter FIXMBR, similar to what's described here:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by mcduck on 2007-03-20
Error 18 is telling you that the partition you are trying to boot from is bigger than what your BIOS supports, so it's not a problem that can be solved by reinstalling Grub. Either you need to find BIOS update that supports larger disks, ot then you need to make a separate smaller /boot partition.

---

### Post by jook on 2007-03-20
> **mcduck said:**
> Error 18 is telling you that the partition you are trying to boot from is bigger than what your BIOS supports, so it's not a problem that can be solved by reinstalling Grub. Either you need to find BIOS update that supports larger disks, ot then you need to make a separate smaller /boot partition.


When I started, I set aside 60gigs for Ubuntu. Then from the live CD i used the partition editor to divide that into 1gig for the boot and 59 for everything else. (root?) They're in the middle of the drive though - there's a 126GB windows partition before, and another after, of somewhere around 180gigs.

---

### Post by jook on 2007-03-28
went into the BIOS and set it to boot from the second hard drive instead of the first, and I got the same messages... loading stage 1.5, error 18. It was slower about doing it, though.
Then I booted back to the live CD and entered the terminal commands again jsut for kicks, and tried again, it worked out the same way.
Anything else to do? I don't really want to go back to the windows MBR because that definitely wouldnt bot linux, right? I'd rather have a purpse for the missing 60gigs from my hard drive.

---

### Post by jook on 2007-04-12
bump?

---

### Post by dstew on 2007-04-12
In order to get around an error 18, the whole boot partition with the kernel in it has to be within the first 1024 cylinders of the disk. You have to create a boot partition at the beginning of the disk, and mount it to /boot before installing. See last post of bobby_b and post by mcduck.

---

### Post by jook on 2007-04-13
So, somehow I need to get the partitions moved around then?
[IMG]http://i12.tinypic.com/3zi4sqd.png[/IMG]

The two NTFS partitions at the front and back are used by windows.
The other two (1-gig swap and 60-gig ish ext3) I used to install ubuntu.

So, assuming I can find a way to move these things around (suggestions? Is this possible?), in what order do I want them?

---

### Post by dstew on 2007-04-14
Yes, you have to move things around to make a boot partition. I would probably be easiest to do it this way.

1. Shrink /dev/hdb1 by 100 Mb. I can't recall if you can shrink if from the right only, or if you can shrink if from the left also. If you can, shrink it from the left. If not, then shrink it from the right, and then move it toward the right so that you have the 100 Mb of unallocated space at the start of the drive.

2. Create a new partition out of the 100 Mb and format it as ext3. I am not sure if the /boot partition has to be a primary partition or not, but make it a primary partition just to be safe. It should end up being /dev/hdb3.

3. Reinstall Ununtu. (You might have to format /dev/hdb7 to remove your old install). When it gets to the part about mount points, make the mount point of /dev/hdb3 to be /boot. /dev/hdb7 will be /. When you re-install, put grub in the MBR of your first disk (hd0), and grub's root should be (hd1,2).

Of course, back up everthing you want to save. With such a complicated partitioning exercise, you want to be safe.

---

### Post by jook on 2007-04-28
I thought I might be able to take care of it in GParted, but when I've ried booting the live ubuntu CD recently, nothing happens. Nothing has changed on my system that ought to affect it, it's very strange. I get to the CD's menu. "Start/Install Ubuntu, Memory Test, Boot Hard Drive" etc. When I choose to start the live disk, I get a couple lines of text, and a whole bunch of dots showing some progress or other (as I always did), and I even get as far as the Ubuntu boot screen, with the circles logo and a little progress bar that keeps scrolling to the right (very like the windows boot screen) only, it either freezes on this screen, or goes blank and sits forever with a white text cursor at the top left of an all-black screen.
What's going on here? It's hard to fiddle with the partitions as I can't get into linux. If I look at it with Partition Magic from in windows, it just tells me the whole drive is bad. Silly thing. I guess it doesn't like linux partitions.

Where can I go from here, folks?

---


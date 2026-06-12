---
title: "Partition help to undo Dual Boot Win98"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by lkraemer on 2008-03-01
My current computer has Win98SE, and WinXP set up for Dual Boot.
I want to prepare the drive for installing Ubuntu ver 7.10.  I have used GOOGLE to search and also searched the forum and haven't found my answer yet.

I have copied my current drive to a 320G Maxtor STM32206020A IDE drive to allow me to test the results.
 
My Drive has the following:
 
1.  First Partition - 14.3Gig FAT32 Win98 (Dual Boot with WinXP in an EXTENDED Partition))
2.  Second Partition - EXTENDED 63.8Gig NTFS (WinXP Partition)
3.  Lots of unallocated space.
 
I would like to do the following:  (without having to totally rebuild my XP machine)
 
1.  COMPLETELY REMOVE the Win98SE Partition, and stay with the Four Partition Limit.
2.  MOVE/SLIDE the WinXP Partition to the beginning of the Drive, then EXPAND it to 80Gig, and still have it BOOT UP on XP (and also Ubuntu ver 7.10)!
     Note: I would really like to have this partition not be EXTENDED, and would rather it be just a normal Partition.........if possible.

3.  Create 3 more Partitions (/, /HOME, /Linux-Swap) to install Ubuntu.
   
That would give me Four Total Partitions.
1.  WinXP - Bootable 80Gig NTFS Partition
2.  Ubuntu 7.10 using /, /HOME, /Linux-Swap - Bootable  
 
I have tried several times without any luck in getting Win XP to boot.
 
Do one of you fine gentlemen have a solution that will allow me to
get XP booting and be the first Partition without a total rebuild?  I can't be the first to try this.

Thanks.

Larry

---

### Post by pytheas22 on 2008-03-01
I don't know that you could move the Windows XP partition, and even if you could, it seems like it would be pretty dangerous to me (e.g. there's a high risk of corrupting the XP system).  What you could do, however, is leave the XP partition where it is but expand it to the size you want (you will only be able to expand it towards the end of the drive, not the beginning, as far as I know), and build the Ubuntu partitions around that.  I know that this will limit your flexibility in setting up the Ubuntu partitions to some extent, but I'm not sure that there is a better solution (although I hope that there is and someone smarter will tell us).  You could probably use the space of the 14.3 gigabyte partition for / ; it would be enough for most normal systems.

As for booting, when you install Ubuntu it should rewrite the MBR and make grub entries for both Ubuntu and Windows, solving the problem with XP not booting.

---

### Post by Duck2006 on 2008-03-01
> 2. Second Partition - EXTENDED 63.8Gig NTFS (WinXP Partition)

If you take win98se off the drive you will not get win xp to boot because it is on a extended partition, it has to be on a primary partition.

This will help with installing ubuntu with win to dual boot.

[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

---

### Post by lkraemer on 2008-03-02
Thanks for the reply Duck2006 & pytheas22.................

I did manage to find a way to get it done and here it is...........................



How to Clone a WinXP EXTENDED Partition to a New Drive's Primary Partition

 

My 320G Maxtor STM32206020A IDE Drive has the following:

 

1.  First Partition - 14.3Gig FAT32 Win98 (Dual Boot with WinXP in

    an EXTENDED Partition))

2.  Second Partition - EXTENDED 63.8Gig NTFS (WinXP Partition)

3.  Lots of unallocated space.

 

I would like to do the following:  (without having to totally rebuild XP)

 

1.  COMPLETELY REMOVE the Win98SE Partition, and stay with the Four Partition Limit.

2.  MOVE/SLIDE the WinXP Partition to the beginning of the Drive, then EXPAND it

    to 74Gig, and still have it BOOT UP on XP (and also Ubuntu ver 7.10)!

     Note: I would really like to have this partition not be EXTENDED, and would

           rather it be just a normal Partition.........if possible.

3.  Create 3 more Partitions (/ /HOME /Swap) to install Ubuntu.

     (Ubuntu will install GRUB when it is installed)

 

That would give me Four Total Partitions.

1.  WinXP - Bootable 74Gig NTFS Primary Partition

2.  Ubuntu 7.10 using /, /HOME, /Linux-Swap - Bootable

 



	Solution Follows:





 How to Clone WinXP EXTENDED Partition to a NEW Drive's Primary Partition



1.  Download Gparted/Clonezilla Ver 2.3 ISO and burn a LiveCD.  NICE Software & it works GREAT!

    [http://clonezilla.sourceforge.net/gparted-clonezilla/](http://clonezilla.sourceforge.net/gparted-clonezilla/)

    [http://clonezilla.sourceforge.net/gparted-clonezilla/download/](http://clonezilla.sourceforge.net/gparted-clonezilla/download/)



2.  Download and Install XXCLONE to Drive E: (WinXP).

    [http://www.xxclone.com/](http://www.xxclone.com/)



    Make sure the following exist on E:, if not copy them to E: from another XP machine.



    Autoexec.bat	0KB	MS-DOS Batch File

    boot.ini		1KB	Configuration Settings	Hidden

    Config.sys		0KB	System File

    IO.SYS		0KB	System File		Hidden & Read-Only

    MSDOS.SYS		0KB	System File		Hidden & Read-Only

    NTDETECT.COM	47KB	MS-DOS Application	Hidden & Read-Only

    ntldr		245KB	System File		Hidden & Read-Only

    

3.  Install the NEW Drive to the Primary IDE cable as Master ie. C:\



4.  Boot from Gparted/Clonezilla LiveCD, and remove all partitions from

    the new drive left over from previous testing.

    (Skip this step if the drive has never been used)



5.  Boot from the WinXP CDR, and CREATE a 74003 NTFS Partition, and Format.

    Power off the computer when it starts to copy the files.  Do not worry. 



6.  Install the drive you are going to CLONE on the Secondary IDE Cable as Master. (ie. E:\)



7.  Boot Gparted/Clonezilla LiveCD.  Select Boot Second Drive MBR.  This will allow you to

    boot into WinXP on the Extended Partition.  (E:\ in my system)



8.  Go to START, CONTROL PANEL, DISPLAY, and disable the screen saver.



9.  Run XXClone and click on the Drive Manager Tab.  Verify that the drives are

    as you had planned.



10. Copy the drive -- E:\ to C:\ with XXClone -- first default option.



11. When the copy is complete, Restart XXClone, SET TARGET Drive, select the tab

    COOL OPTIONS to write the following:

    MBR

    Boot Sector

    Boot.ini



12. Shut Down the Computer.  REMOVE the Original drive from the Secondary IDE Cable,

    and store it in a safe place until the copy has been proven to work.



13. Boot and test the XXCloned Drive which is now E:\.



14. Zit Zot......Slicker than snot!



15. Install Ubuntu 7.10 ........the easy part.

---

### Post by lkraemer on 2008-03-09
The following sites have good information on Dual Boot systems.

[http://www.goodells.net/multiboot/principles.htm](http://www.goodells.net/multiboot/principles.htm)
[http://www.goodells.net/multiboot/index.htm#principles](http://www.goodells.net/multiboot/index.htm#principles)

[http://www.nick.rozanski.org.uk/index.php?page=multboot#stdboot](http://www.nick.rozanski.org.uk/index.php?page=multboot#stdboot)

[http://www.thpc.info/dual/removedualboot.html](http://www.thpc.info/dual/removedualboot.html)

LK

---


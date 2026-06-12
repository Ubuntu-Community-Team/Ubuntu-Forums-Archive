---
title: "Hard drive problems, Dual booted Ubuntu/Windows7."
date: 2013-06-19
forum: Any Other OS
---

### Post by c4nati on 2013-06-19
Ok, first off I'm fairly new to computers and Linux in general.  I built my own PC a few months ago and I installed Ubuntu on the HDD first because I didn't have windows.  I finally bought windows 7 and found the task quite difficult of installing it since I was told it's easier and recommended installing Windows first.  I ended up installing Windows and it broke GRUB which I had to repair.  All went well and everything was fine, I could boot into Ubuntu or Windows at ease from GRUB when my computer boots.  Fast forward a week ago I buy a SSD and install Windows 8 on it.  I had my HDD unplugged, power cable and sata cable during the process because I read up boot loader info could possibly be corrupted due to different OS's.  I completely forgot I had a HDD until yesterday (haha I know -.-) So I opened my computer up and hooked it back up. I went into BIOS and chose to boot from the HDD and up comes GRUB and I choose to boot into Windows 7 and it wouldn't let me, it went to the repair screen and it wouldn't let me repair or restore any point and failed every time.  I end up going into Ubuntu because it booted fine (and still does) and getting into the Windows partition and transfer all my files and back them up.  Now since I'm not quite knowledgeable yet I tried to wing it to learn and put in my Windows 7 ISO disk again since Windows was broke for some reason and I tried to install it and when I get to the screen of choosing which partition it gave me the error from picture 2 no matter which partition I highlighted.  So then I formatted the partition Windows 7 was originally on from within the installation screen and then tried again to no avail.  I booted back into Ubuntu, which has had no problems this entire time and deleted that partition and created a new one of the same size with Gparted and tried again, still getting the same error from picture 2.  I guess my question after this long type up is how do I fix the partition so Windows lets me re-install?  Or is there a way to delete everything on the HDD even partitions so it goes back to like new out the box?  I burned a program called Dban to a disc which apparently is suppose to delete everything but even after choosing the CD in BIOS to boot from it does nothing and goes into GRUB after failing to boot the CD.  Once again my apologies for the long type up and any help is appreciated. (I've included two more images in case that can help)

1. Unallocated space is the partition Windows was originally on.  Ubuntu is partition 1.
[IMG]http://imgur.com/hPRq6cT.jpg[/IMG]

2. The error I get while trying to install it on any partition
[IMG]http://imgur.com/ikRVG0O.jpg[/IMG]

3. From within Ubuntu 
[IMG]http://imgur.com/JqlZViz.jpg[/IMG]

---

### Post by c4nati on 2013-06-19
Lots of views but no replies, uh oh I hope I didn't mess up big time.  Any ideas?

---

### Post by oldfred on 2013-06-19
Please only bump once per 24 hours. We are all volunteers and in many time zones. Also please do not use large pictures. Attach screenshots with advanced editor, using paperclip icon. Those with older systems or slow Internet may never load your post.

Since you have a new computer you are into UEFI and/or BIOS booting. Your system has both. Ubuntu will install either with gpt partitioning and boot with either UEFI or BIOS. 
Windows will only boot from gpt partitioned drives with UEFI or with UEFI only from gpt partitioned drive.

Since you now have two drives are both gpt partitioned or MBR(msdos) partitioned.
How you boot installer UEFI or BIOS - for both Windows & Ubuntu is how it installs. If first install is UEFI with gpt partitioning then the second install must be also.
and with two drives both should be the same partitioning and same boot UEFI or BIOS.

Post this:
       sudo parted /dev/sda unit s print

See also link in my signature for more info on UEFI and many useful links.

Also Windows does not see LInux partitions and may damage them. Use Windows partitioning tools to shrink Windows NTFS partitions and immediately reboot to let Windows run its repairs & chkdsk. But use gparted for all Linux or new partitions.

---

### Post by c4nati on 2013-06-19
> **oldfred said:**
> Please only bump once per 24 hours. We are all volunteers and in many time zones. Also please do not use large pictures. Attach screenshots with advanced editor, using paperclip icon. Those with older systems or slow Internet may never load your post.

Since you have a new computer you are into UEFI and/or BIOS booting. Your system has both. Ubuntu will install either with gpt partitioning and boot with either UEFI or BIOS. 
Windows will only boot from gpt partitioned drives with UEFI or with UEFI only from gpt partitioned drive.

Since you now have two drives are both gpt partitioned or MBR(msdos) partitioned.
How you boot installer UEFI or BIOS - for both Windows & Ubuntu is how it installs. If first install is UEFI with gpt partitioning then the second install must be also.
and with two drives both should be the same partitioning and same boot UEFI or BIOS.

Post this:
       sudo parted /dev/sda unit s print

See also link in my signature for more info on UEFI and many useful links.

Also Windows does not see LInux partitions and may damage them. Use Windows partitioning tools to shrink Windows NTFS partitions and immediately reboot to let Windows run its repairs & chkdsk. But use gparted for all Linux or new partitions.

Well my SSD shouldn't have anything to do with this should it?  I have that unplugged, I'm only using my HDD right now.

---

### Post by oldfred on 2013-06-20
SSD may only be a concern that it should also be booting with UEFI if hard drive is UEFI or both should be BIOS boot.
Otherwise to dual boot you have to go into UEFI/BIOS change boot mode and change drive to boot from every time you want to change. Not an easy way to dual boot.

If both boot in the same mode you can easily dual boot from grub menu or chain load from one drive to another.

One advantage of gpt partitioning with Ubuntu is that it will boot with UEFI or BIOS with gpt partitioning. Windows only boots from a gpt partitioned drive with UEFI. 
Both only boot from MBR(msdos) partitioning with BIOS.

---

### Post by c4nati on 2013-06-20
> **oldfred said:**
> SSD may only be a concern that it should also be booting with UEFI if hard drive is UEFI or both should be BIOS boot.
Otherwise to dual boot you have to go into UEFI/BIOS change boot mode and change drive to boot from every time you want to change. Not an easy way to dual boot.

If both boot in the same mode you can easily dual boot from grub menu or chain load from one drive to another.

One advantage of gpt partitioning with Ubuntu is that it will boot with UEFI or BIOS with gpt partitioning. Windows only boots from a gpt partitioned drive with UEFI. 
Both only boot from MBR(msdos) partitioning with BIOS.

I don't think I explained what I was looking to do properly, as I am still new to this and trying to learn so I apologize.  With my SSD out of the picture, I'm just wondering how I can either delete all the partitions on my HDD so I can start fresh with installing windows again first then Ubuntu or to fix it so it lets me install Windows 7 again on the unallocated partition that had windows on it before.  In order to do the second option of re-installing windows I need to do what you said to make the disk GPT correct? Since that's what windows is telling me and is why I cannot install it?

---

### Post by oldfred on 2013-06-20
Do you want UEFI boot or BIOS boot. You have to boot installer media, flash drive or DVD in that mode for both. 
I think with Windows 7 you only get BIOS install with DVD and have to convert to flash to be able to install with UEFI.

If you want BIOS boot and drive was gpt you may have to remove left over gpt data. One of gpt advantages is that it has a backup partition table. But when Windows installs on a gpt drive it converts to MBR but does not overwrite backup table. Then Linux sees both MBR and gpt backup and gets confused.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

If you want UEFI, Windows has to create several partitions.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

You can modify partitions with gparted. But use Windows Disk tools to shrink a Windows NTFS partition and reboot immediately to let it repair it and run chkdsk.

 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---


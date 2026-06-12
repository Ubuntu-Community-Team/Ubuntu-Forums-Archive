---
title: "Windows Vista x64 will not reinstall!"
date: 2012-09-14
forum: Any Other OS
---

### Post by Terrapin2190 on 2012-09-14
Hi,

I recently downloaded and successfully installed the latest version of Linux Ubuntu on my HP Pavilion dv4 laptop. I created a new partition (of ~26Gb) and all was well, except for the fact that under Windows Management the two partitions it created had no drive letters. Somewhere along the line I decided that Ubuntu was not the OS for me, so I thought "Okay, Ill just do what I've done about 5 times this month and install a fresh copy of Windows Vista x64 complete with horrendous amount of HP bloatware via system restore and all will be normal once more." Well... obviously, since I wound up here all was and is not well and I'm stuck thinking "I knew installing Ubuntu (myself) was a bad idea!" Nothing against Ubuntu, I think its more the fault of Windows or myself if anything. SO... here"s what I did...

After installing Ubuntu, I opened Windows Disk Management and manually deleted both "sub-partitions?" Erased the space within the partition they were in and expanded the space of my C:\ drive to allocate the space that Ubuntu was using. 

Then I went ahead and utilized a few features to try and rid myself of some pesky metadata and MFT files so I could shrink more space through Disk Management (as I wanted to install Windows 7 next to my existing Vista)

Disabled Windows System Restore
Disabled Kernel Memory Dump
Disabled pagefile
Deleted Pagefile.sys
Disabled Hibernation
Ran Cleanup Wizard to remove restore and hibernation junk

Then I defragged multiple times with Auslogics, PuranDefrag, and Microsoft's defrag utility with the command lines "defrag c:\ -v -w -f"

At THIS point, I downloaded a few things, something noteable might be EasyTether from the GooglePlay Marketplace (which was how I was d/ling things).

Then came the Microsoft (/HP) System Restore.

Head spinning yet? Mine too.


Now, mind you, after installing Ubuntu, I had been having Boot trouble, F11 at startup would not take me to recovery options. While Windows was still operable I would open HP Recovery Manager and magically wind up in System Recovery options. Or later on, I mounted my recovery partition (drive D:\) as the active partition, taking me to System Recovery upon rebooting.

So I mounted D:\, ran System Recovery and began installing Windows Vista x64 Setup.

Reformatting and installing Windows components all worked well. Its when I got to HP Software Installation that I began having trouble.

(Here's the juicy part!! XD)

The HP Software Installation was almost to 100% when the screen flickered and showed the desktop for just over a second and showed an "uiadll32.exe" error, and toward the end of HP Soft Inst (it shows at the beginning after it restarts itself and tries to complete installation again) a window pops up stating "Windows can't certify this driver installation" and asks "Don't install this driver software" or "Install anyways."

From there, my laptop just restarts in a constant loop and tries to complete the end part of HP Software Installation.


I've done a bit of research on this and some people are saying that the "Windows can't verify this driver installation" error stems from an IDT Audio Driver error. I can't see why this would be a problem. I'm just completely frustrated trying to reinstall Windows Vista x64 Factory Setting.

I DO have a copy of Windows 7 x64 that I could use to troubleshoot with and have some experience using the command prompt to fix boot settings and MBR. (Something else I have also done trying to restore my boot settings so I can easily get into System Recovery Settings, which didn't solve much.) ex: recboot.exe /fixboot, recboot.exe /fixmbr, AND the /nt60 force fix command (which is for Vista's MBR, I believe).


Sorry for such a long and drawn out walkthrough for what I have done to edit and attempt to recover my computer's original settings, but I figured the more you know, the more you can troubleshoot just what the heck is going on here. I'm in dire need of help and would rather restore my Vista than install a fresh copy of Windows 7 (even though I have most of the drivers in backup). There's something else I found on the internet that lists quite a few command prompt commands that will rebuild Vista's MBR from scratch, but I'm not sure I want to go down that route after all I have already done. This could be an easy fix, or an easy nuke button. If there's anything I can do to perform a restoration here, please... PLEASE let me know! I would be forever in your debt! (Especially after reading all this...)

Thanks so much for lending an ear.

High Hopes!
--Terrapin2190



PS - I can post links of some of the things I've researched, if it will help, please let me know!

---

### Post by oldfred on 2012-09-14
Moved to Other OS as it is primarily Vista issues.

You seem to have gone thru all the Windows repairs that I know. 

The MBR is just a simple boot loader that only checks for active or boot flagged partition and jumps to that partition's partition boot sector to continue to boot. 

System Restore is just an image of hard drive as purchased, so it should just recreate your system.  And anything you did before that would not really matter. But if it is not working then that should be an issue with HP.

Did you change any settings in BIOS like to AHCI and now it cannot install those drivers?

For a complete blow-by-blow on dealing with HP's four primary partitions with Windows 7, see Full Circle Magazine, issue 41, page 36. 
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by Terrapin2190 on 2012-09-15
Thanks so much for the speedy reply!

I did install Windows 7 side by side with Windows Vista (without partitioning) before I installed Ubuntu (with built in partitioner). I uninstalled Win7 when I realized that my boot settings had been modified (the BIOS, maybe?) and then had to reinstall Vista by manually moving the Windows.old folder back to drive c:\.

But thankfully I did solve my problem with a set of HP Recovery Discs I found. For some reason they only worked when they wanted to, so I used them as a last resort, thinking they probably wouldn't read from my faulty cd/dvd burner.

I did use the Windows 7 command prompt just to check if CDrom drive E:\ would read them before restarting and successfully booting from the discs. Thank God it worked! I thought for sure my PC was toast after this endevour.

On to clearer skies!
Uninstalling HP bloatware and trying not to lock this thing up again!

---

### Post by oldfred on 2012-09-15
Rather than go thru all that hassle again.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---


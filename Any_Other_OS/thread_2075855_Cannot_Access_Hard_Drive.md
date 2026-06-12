---
title: "Cannot Access Hard Drive"
date: 2012-10-24
forum: Any Other OS
---

### Post by Kugel7719 on 2012-10-24
OK so background information: I am running Ubuntu 9.10 on a CD. What I wam trying to accomplish is go in and access some files off of the hard drive of this computer to put onto a memory stick so we dont lose them when everything gets deleted during windows installation. there is a problem with the old windows vista we had and now are trying to install windows 7. so when i try to access the part of the computer were everything is stored from Ubuntu, i get this error:

"Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details."

I have never used Ubuntu before, and only need it for a few minutes to get some photos and stuff off our computer. is this a problem with the physical HDD and it is broken (which may also be the problem with windows) or is this just something software side that is wrong with the HDD/Ubuntu that can be fixed. If this is the case i would really appreciate some help from someone who knows what they are doing, or help as to at least figuring out what the problem is if no solution is readily available =D

---

### Post by ahallubuntu on 2012-10-24
Ubuntu 9.10 is really old (no longer supported).  On a normal working Windows hard drive it would be able to copy stuff off of a normal partition, however.

You should check the S.M.A.R.T. status of the drive.  You can do this with a Ubuntu CD but it is a bit more difficult because you have to try to install SmartMonTools, and in something as old as 9.10 I'm not sure how well that will work.

A better option is to try the excellent Parted Magic Linux distro which has SmartMonTools ("Disk Health") built in plus the ability to access Windows partitions (and copy files from them to a memory stick).  Parted Magic isn't as pretty as Ubuntu but it is a terrific, compact little Linux distro that would work perfect for what you want to do.  Just google for "Parted Magic."  (It was originally intended for partitioning, but you don't need to do that at all.)

(In Disk Health/S.M.A.R.T. look for the Attributes tab and find any attributes highlighted in red.  If none are, the disk is probably OK.)

---

### Post by Kugel7719 on 2012-10-24
Hey thanks alot for the quick response. the thing is that 9.10 Ubuntu will fit onto the tiny CDs we have lying around, and newer versions are too big, so i went with the smaller one to save me from buying a bigger CD for a quick 2 minute use. Ill try this in a few minutes and we'll see how things work out. =D

---

### Post by ahallubuntu on 2012-10-24
Parted Magic is pretty small too and should fit on a "tiny" CD.

---

### Post by Kugel7719 on 2012-10-24
alright im in the Disk Help program and the only thing highlighted in red is 'Soft Read Error Rate' id13. 

Norm-Ed Value: 99
Worst: 99
Threshold: 0
Raw Value 242

When i open the file manager and try to open the hard drive it says:

Run: Mount/dev/sda1
Status: Finished With Error ( Exit Status 13 )
 $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

GAH! im so close all i need to do is get some family photos off of the computer and im done with this but i just cant seem to open this hard drive! anyway thanks for all your help im going to try google searching with the new information you have gotten me. if you have further suggestions they would be greatly appreciated, i feel a little silly having you walk me through this holding my hand but you have been a massive help! anyway sorry for wasting so much of your time with this, but you seem to really know what you are doing and the help is invaluable.

---

### Post by jonnyboysmithy on 2012-10-24
[B]
You need to get windows to error check the disk.[/B]
One way would be to unplug the harddrive and put it in another machine and then get windows to check it for errors. 
I think this will be the easiest way.  While you're at it you might as well copy off the data you want.

If you dual boot then just start windows and get it to error check the drives.

Either way as far as I know you will need windows to check the disk.

EDIT:It might pay to check the S.M.A.R.T status of the disk.
Just to make sure the disk is physically healthy, after all your ntfs is inconsistent, usually it happens to me when I get a power cut or something.
Hope that helps :)

---

### Post by Kugel7719 on 2012-10-24
im hesitant to do that because it was a prebuilt pc and we have never opened it, and all i have available to me other than that computer is my laptop. Can you plug it in? im a complete begginer at this and dont knw what type of connection HDDs have. any way i can just access these files, or even copy the entire thing to another hard drive would be great. i just need to move whats on the hard drive to somewhere else, and its proving more difficult than i thought

---

### Post by oldfred on 2012-10-24
Moved to otherOS since Windows issues.

Do you have Windows on your other computer? Then you can make a repairCD or USB to run  chkdsk on your Vista system.

I have used a Windows 7 repair USB to run chkdsk on my XP install. It converted to a Windows 7 Partition Boot sector which I had to undo, but Vista & 7 use the same boot sector.

Backups ---------
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

---

### Post by jonnyboysmithy on 2012-10-24
Shows you how to run chkdisk from your windows7 installer:
[https://kb.wisc.edu/page.php?id=6565](https://kb.wisc.edu/page.php?id=6565)

---

### Post by jonnyboysmithy on 2012-10-25
> **meliscarop said:**
> I'm not sure how well that will work.
<snip>I'm positive it'll do the trick. You're not too sure?
You could try repair your vista installation just so that you can run the checkdisk using the nice interface. But right now I think the easiest way is to use to use the command  line as suggested above. Its up to you.

---

### Post by Kugel7719 on 2012-11-02
Hey thanks for the help, I tried the repair tool witthe windows 7 disk, it says it cannot check because the volume is in use by another process. it gives me tho option to dissmount and run the check but it says all open volumes of this handle would be invalid. should i try this or is there seriously an issue with tihs hard drive?

---


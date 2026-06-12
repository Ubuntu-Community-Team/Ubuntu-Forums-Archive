---
title: "Grub Rescue Shell, Ubuntu partition deleted"
date: 2013-01-12
forum: Any Other OS
---

### Post by JoshDude on 2013-01-12
Hi guys,

I've had a Windows XP and Ubuntu setup on my netbook (Samsung N130) for some time, but I was running low of hard disk space so opted to format the parition with Ubuntu installed (i know, i know - but for this netbook I prefer XP).

This decision has rendered my system unbootable, on a restart I get the following:

[FONT=Courier New]error: unknown filesystem.
grub rescue>[/FONT]

I attempted to fix my MBR using a bootable flash drive with XP installed as detailed in this guide [http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/). 

The operation completed successfully, though I receive the same problem on reboot, perhaps I did something wrong? Should it have not been on the C:\WINDOWS> command line, the parition I removed was originally on D:. I'm completed lost!

Thanks

---

### Post by oldfred on 2013-01-12
Moved to OtherOS as Windows issue.

Did you run fixMBR as that is what writes the Windows boot loader to the MBR overwriting the grub boot loader in the MBR?

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by JoshDude on 2013-01-13
Hi oldfred - thanks for the reply,

I followed the instructions on the link you provided as follows:

1. Booted from my Windows XP drive and chose to repair the Windows installation by pressing "r".
2. When prompted 'Which Windows installation would you like to log onto' I entered 1.
3. When prompted for an admin password I just pressed enter as I don't believe I have one.
4. At the C:\WINDOWS> command line I entered fixboot which produced the following:

[FONT=Courier New]The target partition is C:
Are you sure you want to write a new bootsector to the partition? (entered y)

The file system of the startup parition is NTFS

FIXBOOT is writing a new boot sector

The new bootsector was successfully written[/FONT]

5. I then ran fixmbr - received the usual:

[FONT=Courier New]** Caution ** this computer appears to have a non-standard or invalid boot record ... Are you sure you want to write a new MBR? (entered y to proceed)[/FONT]

[FONT=Courier New]The new master boot record has been successfully written.[/FONT]

6. Typed exit to restart the system, which brought me back to my bootable flash drive with Windows XP.
7. Restarted the system again after removing the flash drive, greeted with the same error: unknown filesystem.

EDIT: If it makes the process any easier - I'm prepared to lose any and all data currently on my hard drive.

---

### Post by oldfred on 2013-01-13
If you have an XP install that should have fixed it.

Post this from Ubuntu liveCD. Will not fix Windows issues, but may show what is wrong.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers)

---

### Post by JoshDude on 2013-01-14
Hello again oldfred,

I created a new bootable flash drive with an Ubuntu-Secure-Remix iso, and was successfully able to boot into Ubuntu.

Fom here I selected to 'Try Ubuntu', from where I ran Boot-Repair and selected to 'Create a BootInfo summary'. Noticed I could see all of the files on both my Windows XP C:/ drive as well as the empty D:/ drive.

Here is the URL that was output from the Boot-Info: [http://paste.ubuntu.com/1532264/](http://paste.ubuntu.com/1532264/)

Thanks for your help so far

---

### Post by oldfred on 2013-01-14
Boot-Repair cannot do much to fix Windows. Your configuration looks ok, but then something internal to Windows is wrong. Normally chkdsk is the first thing to try.

You have to have the 3 boot files shown in your sda2. Partition shows as NTFS and partition boot signature says it is ok. Sometimes that is not and a rebuild with testdisk may fix it. Not sure if fixBoot just restores backup and if backup has issues then fixBoot does not work. Sometimes just replacing ntldr works. But depending on where copied from may need  attributes reset.

       If files are still missing you can do this to copy from CD to C:\:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

   Boot files may need attributes also from Windows repair console:
attrib +r c:\filename
attrib +h c:\filename
attrib +s c:\filename

    
       Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

    
See if testdisk reports partition boot sector as ok and backup as ok.
       As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS.

---

### Post by kiyop on 2013-01-15
/dev/sda1 has /bootmgr and /boot/BCD. Something strange. Windows 7 and Windows XP are mixed, although you don't mention about Windows 7.
/dev/sda2 has /NTDETECT.COM, /ntldr and /boot.ini.

How about chainloading to /ntldr on /dev/sda2?
You can chainload to /ntldr by grub4dos.

---

### Post by oldfred on 2013-01-15
I have seen the Vista/7 recovery & XP install before. I think it usually is where after Vista came out you could down grade to XP, but the vendors already had changed recovery to a Vista style boot.

If you use testdisk to compare PBR to backup PBR you can use dump command to see the details of the PBRs. If you page down you will see plain text ntldr or bootmgr and know which style NTFS partition you have.

---

### Post by JoshDude on 2013-01-15
Appreciate the input, I'm not getting very far at the moment. Everything either seems to be as it should or I just hit a dead end - I have very little time at the moment so I apologise for the delays in getting back to this thread.

If I were to reboot using the WinXP flash drive - would I be able to format the hard drive and reinstall Windows on a clean hard drive? I've considering this as a backup option (in case this proves to be more trouble than it's worth), as I just need a system that will boot in Windows at this point. Would you advise that I use a utility such as KillDisk or DBAN first to wipe the HDD to ensure no trace of either OS or any kind of malware?

Thanks for the help thus far.

---

### Post by kiyop on 2013-01-16
If you do not need anything in your HDD now, you can format all the partition.
But are you sure if you need nothing in your HDD?

I suggest you trying the following:

Boot with Ubuntu-Secure-Remix and "try Ubuntu".
Open "terminal" and execute the following:
```
sudo su -
wget -c http://download.gna.org/grub4dos/grub4dos-0.4.4.zip
apt-get update
apt-get install unzip
unzip grub4dos-0.4.4.zip
cd grub4dos-0.4.4
mount -t ntfs-3g /dev/sda2 /mnt -o rw
dd if=/dev/sda bs=512 count=63 of=/mnt/sdambr63
sync
./bootlace.com /dev/sda
cp grldr /mnt/
echo "timeout 5
default 0
title chainload to ntldr
root (hd0,1)
chainloader /ntldr" > /mnt/menu.lst
sync
umount -l /mnt
shutdown -h now
```and remove USB and reboot.

---

### Post by JoshDude on 2013-01-16
Hi kiyop,

I don't believe there is anything that I need from the HDD, excluding perhaps the drivers (though I should be able to download these later).

Now when I attempt to boot with Ubuntu-Secure-Remix I now find myself stuck each time with the following message for more than 20mins:

[11.903564]    xor: automatically using best checksuming function:

Also when attempting to boot without a USB drive I'm presented with the 'No Operating system found' message which is completely new?

I've invested quite a bit of time attempting to fix this netbook now, and think now that a fresh start would be the most painless option. Would you personally recommend that I wipe the harddrive completely first before reinstalling either windows xp/ubuntu?

Thanks for the help

---

### Post by oldfred on 2013-01-16
Do not know about the xor error. Seems like corruption on some partition. chkdsk on NTFS or fsck on ext partitions.

The no operating system found is usually a BIOS message. Windows has to have a boot flag and you did have one on sda2. Grub does not use boot flag.  But some BIOS look for the boot flag and will not let you start to boot unless partition table has boot flag on a primary partition. 

Did boot flag get erased?

---

### Post by JoshDude on 2013-01-16
Hi oldfred,

I must have done. To be honest it was a few years ago when I set up the ubuntu/xp dual boot so I don't recall the process - so formatting the partition with ubuntu through windows may have caused this.

I did not attempt to modify/fix the boot problem with the LiveUsb, I simply ran the Boot-Info tool, but now I can't even get the Ubuntu drive to start properly.

I've decided to do a clean install of windows/ubuntu, effectively start over - I'm not sure if it is best practice to wipe the HDD first, or to just format the discs in the OS installation process?

I appreciate the help, you may close the thread if you wish. It's unfortunate that my issue wasn't resolved, though this may help solve theirs with the advice provided by both yourself and kiyop.

---

### Post by kiyop on 2013-01-17
> **JoshDude said:**
> I must have done. 
Do you mean that you must have removed the boot flag from /dev/sda2?
If you did, add boot flag on /dev/sda2 and try [#10]("http://ubuntuforums.org/showpost.php?p=12458108&postcount=10").

> **JoshDude said:**
> I don't believe there is anything that I need from the HDD, excluding perhaps the drivers (though I should be able to download these later).
I see. Do you think that there may be some malware, such as virus, trojan, spyware, in your Windows?

> **JoshDude said:**
>  Now when I attempt to boot with Ubuntu-Secure-Remix I now find myself stuck each time with the following message for more than 20mins:

[11.903564]    xor: automatically using best checksuming function:

Also when attempting to boot without a USB drive I'm presented with the 'No Operating system found' message which is completely new?
What did you do after posting [#5]("http://ubuntuforums.org/showpost.php?p=12455447&postcount=5")?
The situation must have been changed.
> **JoshDude said:**
> I did not attempt to modify/fix the boot problem with the LiveUsb, I simply ran the Boot-Info tool, but now I can't even get the Ubuntu drive to start properly.
If you have not done anything which may change the contents of the HDD, I wonder if your HDD and/or memory is/are (close to) out of order.

Did you change BIOS boot order? If so, set USB (or CD/DVD)  first boot media and then try boot with Ubuntu-secure-remix LiveUSB (or CD/DVD).
> **JoshDude said:**
> I've decided to do a clean install of windows/ubuntu, effectively start over - I'm not sure if it is best practice to wipe the HDD first, or to just format the discs in the OS installation process?

I appreciate the help, you may close the thread if you wish. It's unfortunate that my issue wasn't resolved,
I do not want you to give up fixing, but it may take shorter time to do clean-reinstall than to fix. Of course, it's up to you.

---

### Post by JoshDude on 2013-01-17
1. I may have removed the bootflag by mistake, however I'm unable to attempt #10 as I'm currently unable to boot in Ubuntu using my LiveUsb.

2. I'm almost certain there was, part of the reason why I chose to remove the Ubuntu partition was for recovery purposes, as the dual boot setup I was making the process that much more difficult.

3. I'd done nothing other than browse & backup a few files onto an external HDD that I was able to view in WindowsXP partition through Ubuntu.

4. I surely hope not. The system is only 2.5 yrs old.

5. I appreciate your help really, but it has proven a lot more difficult than anticipated to restore my system to an already unstable point. Hence why I'm opting for a clean start.

Thanks again. I have KillDisk on another flash drive and will attempt to erase the HDD this evening.

---

### Post by trent.josephsen on 2013-01-18
I have had trouble in the past when trying to install Windows on a disk that has partitions of multiple types -- Windows would format some partitions, but fail to recognize others, and so wasn't able to install onto the whole disk. On the other hand, when you do install onto the whole disk, Windows has this annoying tendency to put the hibernation file at the end of the partition so you can't resize it from within Windows.

If I were you I would wipe the whole thing and create an empty NTFS partition over half the drive (or however much you want Windows to have) using GParted or something. Then try to install Windows just to that one partition.

Good luck.

---


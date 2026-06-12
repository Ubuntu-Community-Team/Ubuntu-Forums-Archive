---
title: "Problem with fstab I think"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by Wilbur Kelly on 2007-02-22
Hi,
Over the weekend I installed a new harddrive and installed XP first, then Ubuntu second with them sharing the drive, a 300 GB drive.  The XP install insisted in wiping out the prepared (Partition Magic) partitions.  XP is running fine.  Ubuntu is also running pretty well.  I can connect to the internet.  Before changing out the hard drive I had a very similar installation with a much smaller drive.  Then I had Ubuntu running fine but could see the original SATA drive that is SDA1 with the original HP installed XP Media Center 2005 that now is only serving as a repository for stuff I intend to install on the new drive.  The new drive is the "slave" which has XP Professional installed in a NTSF partition and Ubuntu  in a SF3.  The second drive has GRUB loaded and it comes up fine into grub and boots into Ubuntu unless I intervene.  The machine boots into the second drive because that is the order I have set in the BIOS.  

I had this setup in the previous incarnation (before this drive replacement) only when I booted into Ubuntu I could see the SATA original drive SDA1 (I think) mounted on the Ubunty desktop.  I could also see the Filesystem drive on the Ubuntu desktop.  I didn't have the XP partition I have now on the second drive then.  

I have looked and found that I should be able to mount the windows partition by:

"Windows partitions should be automatically available from any Ubuntu system. If they are not, you can make them available using the Disks Manager.
1.Open System->Administration->Disks .
2.Select the correct hard disk, and click Partitions.
3.Select the relevant partition, and click Enable.
4.To unmount the partition, click Disable."

Well, there is not "Disks" under System->Administration, so I can't go to Partitions there.

Under Fstab I have:
**********************************************************************************************
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd2
UUID=b0b3ca62-3969-400f-9dbd-5205eace42d7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd5
UUID=77b948a6-1218-4ce1-bbf4-137fb1818263 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
***********************************************************************************************

So I think that is the problem.  The "second" (new) drive shows:
wkelly@wkelly-desktop:~$ sudo fdisk -l /dev/hdd

Disk /dev/hdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       19122   153597433+   7  HPFS/NTFS
/dev/hdd2           19123       38180   153083385   83  Linux
/dev/hdd3           38181       38913     5887822+   5  Extended
/dev/hdd5           38181       38913     5887791   82  Linux swap / Solaris
wkelly@wkelly-desktop:~$ 

The "original" drive shows:
wkelly@wkelly-desktop:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 250.0 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       31080   234964768+   7  HPFS/NTFS
/dev/sda2           31081       32301     9230760    c  W95 FAT32 (LBA)
wkelly@wkelly-desktop:~$ 

I have stumbled around in the manual to find this information but I think it suggests I know more about what I have found than I do.  I don't know how to use this information to change the Fstab file to mount the drives.  If I do what ever is required  to change the fstab file will that fix the fact that in where I should be able to go to: "If they are not, you can make them available using the Disks Manager.
1.Open System->Administration->Disks " 
that n fact:
"there is not "Disks" under System->Administration, so I can't go to Partitions there"

I don't know how I got here with this installation, the first one apparently went flawlessly.  Is this fixable by editing the fstab file or do I need to wipe the Ubuntu disk and reinstall from scratch.  I guess my Windows experience would suggest that course but I am hoping that Linux will allow a recovery with what I have.

Any advice will be gratefully appreciated.  
Thanks,
WK

---

### Post by mcduck on 2007-02-22
1. Run 'ls -la /dev/disk/by-uuid/' to get a list of UUID's for your partitions.
2. Create a mount point for your windows drive  by running 'sudo mkdir /media/windows'
3. run 'sudo nano /etc/fstab' and add a new line like 'UUID=<UUID-HERE> /media/windows ntfs  nls=utf8,umask=0222 0    0'. Replace <UUID_HERE> with the UUID you got for your partition in the first step. Press Ctrl-X to exit nano and answer 'y' when it asks if you want to save.
4. Reboot (I suppose 'sudo mount -a' could also work)

---

### Post by Wilbur Kelly on 2007-02-22
I really appreciate your reply.  I am late for work but will follow your recommendations as soon as I return from work today.  Thanks again. WK

---

### Post by Wilbur Kelly on 2007-02-23
I did as suggested and you were quite right with your instructions mcduck... I took the long route, mostly because I really am that new still.  I found the original HP disk and I found the new XP and copied both dutifully if not wisely to /dev/windows.  The result was not obvious to me at the time.  I had two names but both links opened only one disk.  I tried making a new directory but a mistype led me to create a new directory which I couldn't find.  I decided it might be easier to just reinstall a backup.  That led to corruption of my GRUB.  I told you it was the long route. So I wiped the linux install after saving a few saves and used supergrub to make the windows partition bootable again after removing the nonfunctional GRUB.  I reinstalled Ubuntu and then I did what you suggested (having learned from my earlier error to make two mount points /dev/windows1 (which I am saving to move things to my new disk) and /dev/windows2 (which I am using for a few programs that I need XP for or think I do so far)  Having done finally what you suggested I found the icons on my desktop just like they had been in my first install and they work just fine.  I really appreciate your help.  All the errors were/are mine and I think I learned from the experience.  Sorry it took so long to get badk but I think things are better than ever now.  Thanks again. WK

---


---
title: "Error 22 when logging into Win XP"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by Unstuck on 2007-12-08
I just tried logging into Windows for the first time after installing Startup Manager several months ago.  Instead of loading WinXP, I get 
> Error 22: No such partition
fdisk -l and menu.lst should be attached.

---

### Post by cotcot on 2007-12-08
There are 2 things strange for me.
You have an active partition on sda and sdb. So I do not know on which sd the boot loader is installed. You could try to remove the star on one of them. 

Menu.lst show windows on (hd1,1). This is the SECOND partition of sdb. I think it should be (hd1,0).

---

### Post by Unstuck on 2007-12-08
I changed Win from (hd1,1) to (hd1,0), and still get error 22.  I'm still quite a noob, so I don't know how to unstar sda or sdb.  Can you explain how to do this and what this does?

---

### Post by cotcot on 2007-12-08
in terminal ```
sudo gparted
```
Than you get the list of partitions. The active partition has the flag 'boot'.Right click on it allows you to change the flag. Keep the boot flag on the sd on which you think the grub bootloader was installed during ubuntu install.
The active partition is the partition that boot the operating system.

---

### Post by cotcot on 2007-12-08
If you get problems with booting you can repair the bootloader with the [[COLOR="Red"]Supergrubdisk[/COLOR]]("http://supergrub.forjamari.linex.org/") (I haven't used this myself yet) or reinstall it for instance according to following info which is a relevant quote from the [[COLOR="Red"]Grub Manual[/COLOR]]("http://www.gnu.org/software/grub/manual/grub.html#Top") :

> 3.2 Installing GRUB natively

Caution: Installing GRUB's stage1 in this manner will erase the normal boot-sector used by an OS.

GRUB can currently boot GNU Mach, Linux, FreeBSD, NetBSD, and OpenBSD directly, so using it on a boot sector (the first sector of a partition) should be okay. But generally, it would be a good idea to back up the first sector of the partition on which you are installing GRUB's stage1. This isn't as important if you are installing GRUB on the first sector of a hard disk, since it's easy to reinitialize it (e.g. by running `FDISK /MBR' from DOS).

If you decide to install GRUB in the native environment, which is definitely desirable, you'll need to create a GRUB boot disk, and reboot your computer with it. Otherwise, see Installing GRUB using grub-install.

Once started, GRUB will show the command-line interface (see Command-line interface). First, set the GRUB's root device4 to the partition containing the boot directory, like this:

     grub> root (hd0,0)

If you are not sure which partition actually holds this directory, use the command find (see find), like this:

     grub> find /boot/grub/stage1

This will search for the file name /boot/grub/stage1 and show the devices which contain the file.

Once you've set the root device correctly, run the command setup (see setup):

     grub> setup (hd0)


---

### Post by Unstuck on 2007-12-09
I ran "grub> find /boot/grub/stage1" to see what could be seen, this is what I got
> Error 15: File not found

That seems important...

I'll try SuperGrubDisk tomorrow.

---

### Post by cotcot on 2007-12-09
You could check the stage 1.5 files from the ubuntu live cd.
If you boot from this CD have a look on your sda1 for the /boot/grub/e2fs_stage1_5 ,  /boot/grub/fat_stage1_5 ,  etc

If you do not have them them you could try to reinstall grub as is described in [[COLOR="Red"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=24113")

---

### Post by Unstuck on 2007-12-11
I finally had a chance to try Super Grub Disc...no luck.  Tried reinstalling Grub...no luck.  Now, not only do I get Error 22 trying to log into XP, I also cannot log into Ubuntu.  The splash screen that precedes the page that asks for username and PW loads partially, then the whole screen goes black and the process quits without an error message.  From the live cd, fdisk -l is:
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a62544e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30119   241930836   83  Linux
/dev/sda2           30120       30401     2265165    5  Extended
/dev/sda5           30120       30401     2265133+  82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe25de25d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2434    19551073+   7  HPFS/NTFS


For some reason 'sudo gedit /boot/grub/menu.lst' is blank...

I'm considering reinstalling, but that will erase everything on my disc, correct?

---

### Post by Unstuck on 2007-12-11
Someone in [this]("http://ubuntuforums.org/showthread.php?t=381455&highlight=boot+hangup") thread suggested running
```
sudo e2fsck -C0 -p -f -v /dev/sda1
``` to which terminal replies > /dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)?

Now, my computer is kinda messed up right now, but I'm not sure I'm willing to inflict SEVERE filesystem damage upon it.  What is "e2fsck" and should I risk running it?

---

### Post by Unstuck on 2007-12-11
I used Super Grub Disc to fix the Ubuntu-booting problem.  Hooray.  But the Win partition error is still there.

---


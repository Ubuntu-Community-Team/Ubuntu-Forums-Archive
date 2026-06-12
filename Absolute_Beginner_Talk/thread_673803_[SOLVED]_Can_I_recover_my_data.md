---
title: "[SOLVED] Can I recover my data?"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by zabien1970 on 2008-01-21
Briefly, screwed up last week
installed alsamixer, went to watch a dvd, no sound, removed alsamixer, still no sound?, restarted computer now a warning cannot start display or something!!?, 
OK, figured I'd install windows and download a livecd (lost my old one), installing showed 3 partitiones

  /dev/sda1 ext3 size 77000mb  used 5000mb
  /dev/sda2 ntfs size 3000mb    used ?
  free 8mb

this is what it shows now
when I put the windows install cd in I chose to install cd in I chose to install in the second partition thinking this was my swap

 I'm now running off the livecd and tried installing manually partitioning in sda2 but keep getting stuck, it says no /root partition (I think it wants to be in sda1)

 So now, can I fix this and save my data or did I really screw up?

---

### Post by Paulmd on 2008-01-21
> **zabien1970 said:**
> Briefly, screwed up last week
installed alsamixer, went to watch a dvd, no sound, removed alsamixer, still no sound?, restarted computer now a warning cannot start display or something!!?, 
OK, figured I'd install windows and download a livecd (lost my old one), installing showed 3 partitiones

  /dev/sda1 ext3 size 77000mb  used 5000mb
  /dev/sda2 ntfs size 3000mb    used ?
  free 8mb

this is what it shows now
when I put the windows install cd in I chose to install cd in I chose to install in the second partition thinking this was my swap

 I'm now running off the livecd and tried installing manually partitioning in sda2 but keep getting stuck, it says no /root partition (I think it wants to be in sda1)

 So now, can I fix this and save my data or did I really screw up?


First. You really screwed up, installing windows, or indeed ANY os before you got your data off was not a good idea, you overwrite maybe 1-2 gb of data. You turned a a trivial recovery project in to a more difficult one.

Second, you can probably recover most of your data, it's an 80gb or so hdd, so that's maybe 2-3% of the hard drive that got overwritten, which is decent odds that there is still salvageable data.

Ok. Now that THAT's out of the way. Determine how much you care about whatever was stored, and how much money are you willing to spend. 

If the answer is "it's critically important business records and/or irreplaceable photos, and I'm willing to spend the money." The thing to do is remove the hard drive from the computer, and contact a professional data recovery service.

Next best is to obtain a spare hard drive with at least the capacity of your current one, and make a true copy of it.  ddrescue is a tool that works in linux, but it is not the only one. Then attempt recovery on the copy.

---

### Post by Sef on 2008-01-21
> I'm now running off the livecd and tried installing manually partitioning in sda2 but keep getting stuck, it says no /root partition (I think it wants to be in sda1)

1) If you are dual booting with Windows, then Windows likes to be on the first partition.

2) You need to set Ubuntu to have a / (root) partition.   Read [Psychocat's installing]("http://www.psychocats.net/ubuntu/installing").

3) To recover data, download [Trinity Rescue Kit.]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12")

---

### Post by zabien1970 on 2008-01-21
Ok, all may not be lost, I installed ubuntu on the second partition where windows was, now when I reboot it gives me a boot menu, the first one is
   Ubuntu, kernel 2.6.20-15-generic which loads my new install then a recovery option
then it says other operating systems:
  Ubuntu, kernel 2.6.20-16-generic which fails to launch a gui but gives me a command line which is where I was before
 ls shows me files such as alien and avent-window manager so I assume thats a good sign
 I believe I've been installing in the swap partition since I don't have one now.
 
 So can I swap this info over, I read I can create a /home folder, if so could I do this off the command line, burn to cd, then add it to my new install?

---

### Post by Paulmd on 2008-01-21
> **zabien1970 said:**
> Ok, all may not be lost, I installed ubuntu on the second partition where windows was, now when I reboot it gives me a boot menu, the first one is
   Ubuntu, kernel 2.6.20-15-generic which loads my new install then a recovery option
then it says other operating systems:
  Ubuntu, kernel 2.6.20-16-generic which fails to launch a gui but gives me a command line which is where I was before
 ls shows me files such as alien and avent-window manager so I assume thats a good sign
 I believe I've been installing in the swap partition since I don't have one now.
 
 So can I swap this info over, I read I can create a /home folder, if so could I do this off the command line, burn to cd, then add it to my new install?

Don't go creating, copying, or moving files and folders to the partition that you're trying to recover. You can overwrite what you're trying to rescue.

Look for your data, If you found it, you can burn it to a cd, or copy it to a flash drive or external harddrive.

You really should be running either from a live cd, or have your drive as a secondary unit in another computer.

---

### Post by az on 2008-01-21
> **zabien1970 said:**
> Ok, all may not be lost, I installed ubuntu on the second partition where windows was, now when I reboot it gives me a boot menu, the first one is
   Ubuntu, kernel 2.6.20-15-generic which loads my new install then a recovery option
then it says other operating systems:
  Ubuntu, kernel 2.6.20-16-generic which fails to launch a gui but gives me a command line which is where I was before
 ls shows me files such as alien and avent-window manager so I assume thats a good sign
 I believe I've been installing in the swap partition since I don't have one now.
 
 So can I swap this info over, I read I can create a /home folder, if so could I do this off the command line, burn to cd, then add it to my new install?

If you really did install windows inside your former swap partition, then your data is not lost.

Boot the computer with the live cd and mount both partitions to see when you have.  If the original install of Ubuntu is intact, you can chroot into it and re-install grub.  

sudo chroot /mnt (where /mnt is where the partition is mounted)

sudo grub-install/dev/sda will install grub to sda.

Reformat your swap and you will be in the same shape as before.  Use gparted from the live cd you are running.

To fix your graphics issues, boot into recovery mode from the original install and run

dpkg-reconfiguer -phigh xserver-xorg

and then init 2

---

### Post by zabien1970 on 2008-01-21
> **az said:**
> If you really did install windows inside your former swap partition, then your data is not lost.

I'm pretty sure that's what I did, but then I installed ubuntu over that since I couldn't get online, that's what I'm running on now.

> **az said:**
> Boot the computer with the live cd and mount both partitions to see when you have.  If the original install of Ubuntu is intact, you can chroot into it and re-install grub.  

sudo chroot /mnt (where /mnt is where the partition is mounted)

sudo grub-install/dev/sda will install grub to sda.

Reformat your swap and you will be in the same shape as before.  Use gparted from the live cd you are running.

Before I do this I'd like to fix my original install first if possible since it's the only way I can get to the forums, restarting my laptop I can get to the grub menu and choose my original install to boot from recovery mode and view my files 


> **az said:**
> To fix your graphics issues, boot into recovery mode from the original install and run

dpkg-reconfiguer -phigh xserver-xorg

and then init 2

Already tried reconfiguring when I first lost display, just tried again using -phigh and still no display

---

### Post by zabien1970 on 2008-01-22
Further progress:  Since I new I was removing alsa when I lost my display I went into synaptic and seen removing it also removes ubuntu-desktop.  Running sudo apt-get install ubuntu-desktop restored it and I am now able too boot into my original setup, 

Now for the new problem I created, in the process of trying to get online and to the forums I installed a temp ubuntu install in my /swap partition.  Now that I've fixed the original install I'm ready to restore /swap but I think thats where my grub file is. 
  So could I run sudo grub-install/dev/sda will install grub to sda as az suggested in a terminal

---

### Post by az on 2008-01-22
> **zabien1970 said:**
> 
  So could I run sudo grub-install/dev/sda will install grub to sda as az suggested in a terminal

Run it from a chroot in the partition you want to boot.

If you run it from the "former-swap" install of Ubuntu, once you remove it, grub will be looking for files that are no longer there and refuse to boot.

---

### Post by zabien1970 on 2008-01-22
> **az said:**
> Run it from a chroot in the partition you want to boot.

If you run it from the "former-swap" install of Ubuntu, once you remove it, grub will be looking for files that are no longer there and refuse to boot.

How would I do this, reading the man page mentions you could really screw things up if you run chroot wrong

running sudo fdisk -l gives me this:
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9355    75144006   83  Linux
/dev/sda2   *        9356        9728     2996122+  83  Linux
 
sda1 is my original install and sda2 is my former /swap

Edit:  I would also need to change it to boot from sda1

---

### Post by rosegarden78 on 2008-01-22
EDIT: My external HD was showing up in /dev folder is better place to look than /etc/fstab or /etc/mtab.
"cd /dev"
"ls sdb*"
Your drive will appear and disappear in the /dev folder when you power on/off.
Mount is simply using this command:
"sudo mount /dev/sdb1 /mnt"
to access it from the mnt folder.

DD is like a digital dump used by forensic specialists in computing.  You could check the forums for DD Backup Data.

---

### Post by zabien1970 on 2008-01-22
> **rosegarden78 said:**
> Why not mount the partitions to your desktop?  If the file table and structure is intact and in FAT32 format your file manager should browse the mounted folders.  Here's an example of how to mount: from a terminal type:

nano /etc/fstab
nano /etc/mtab

These commands allow you to find the names of your devices
From a terminal type:

mkdir /home/Desktop/myMountFolder
mount /dev/sda1 /home/Desktop/myMountFolder

These make a folder on your desktop and mounts your sda1 device to it.

???  Still a noob here so I'm not sure what you mean by this
 
nano /etc/fstab  gives me

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c2f49317-904e-4337-aa93-09db4071962a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=bf9b43f9-e9c4-460e-8b3f-e7eaecb5d1fe none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

nano /etc/mtab  gives me

/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
rpc_pipefs /var/lib/nfs/rpc_pipefs rpc_pipefs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/scd0 /media/cdrom0 iso9660 ro,noexec,nosuid,nodev,user=brendon 0 0

What I believe I need to do is make sure grub is in sda1, then I can restore sda2 to /swap and be back to where I was last week

Edit:  I'm currently running off my original install not the livecd

---

### Post by rosegarden78 on 2008-01-22
/dev/sda1   <----This is an Ubuntu partition ext3 format
/dev/sda5 <-----This is a swap partition
/dev/scd0  <-----This is a CD-ROM
/dev <---- This is folder where devices show up.

EDIT: If not in files above check /dev folder for your device.  My external HD shows up as /dev/sdb1 and so does my USB memory stick.

Why do you mention GRUB?  You're running Ubuntu so GRUB loaded your OS right?  Where is the partition you need to recover data?  You only have two partitions your Primary Linux (EXT3) and Swap.  If you had a previous installation you may have experienced permanent data loss.  It looks like your whole hard drive was formatted for use with Linux.

EDIT:  I recommend formatting the whole drive at Step 4 and using your former OS in VirtualBox after you backup your data.

---

### Post by zabien1970 on 2008-01-22
Last week I accidentally lost my display so I installed windows in my swap partition to download a livecd, this erased my grub, I then removed windows and installed ubuntu in my swap partition (this was all in sda2), my original install with all my files is in sda1, I have since fixed the display issue and am looking to return sda2 to /swap but I believe thats where my grub is and doing thismay leave me unable to boot.
I am considering going ahead and returning sda2 to /swap and if I cant boot then I can run the live cd to get back here and ask what to do next but it would be nice to assure grub is in sda1 first

---

### Post by rosegarden78 on 2008-01-22
Not sure you should install in swap.  I split my 36 GB primary windows partition into two primary partition when Ubuntu installation get to Step 4.  If you lost your display you'll have to lookup how to mount disks with the mount command.  Look for the FStab tutorial.

EDIT:  If it's usb device it shows up in /dev folder my LACIE looks like /dev/sdb1.

EDIT: Just backup and use whole disk for Ubuntu.

---

### Post by zabien1970 on 2008-01-22
I don't think you're following where I am, I already installed in swap to temporarily access my original install, then I managed to fix my display so now I want to uninstall ubuntu from swap and be back to where I started, all this I know how to do, where I'm unsure is when I erase ubuntu from swap will it erase my grub

---

### Post by zabien1970 on 2008-01-22
Ok, I booted off the live cd, ran gparted, unmounted sda2 and reformatted as /swap, then tagged sda1 as *boot, restarted and everything seems to be fine, thanks to all those that helped, I'm sure this wasn't the recommended way to fix this but being unable to find my original livecd this was all I could think of, thankfully it worked.
Now off to make a /home partition and backups:)

---

### Post by rosegarden78 on 2008-01-29
EDIT: I was dual-booting until yesterday somebody told me it burns up the hard disk.  So I backup data and fresh install Ubuntu.  The HD light doesn't blink as much as dual boot.  Don't have to worry about where to put things then whole disk is ready.  As far as XP I use it with VirtualBox on Ubuntu desktop.

---


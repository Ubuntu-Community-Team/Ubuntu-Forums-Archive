---
title: "Configuring Extra Harddrive"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by bertlacy on 2007-08-09
I have a Seagate PATA 350GB Hard drive installed as my primary disk but I also have a SATA Western Digital Cavier 250 GB hard disk installed but my computer is not recognizing it.

When I boot my bios sees the drive and but when I go to "Computer" under 'Places' i don't see it anywhere.

I want to mount it so I can use it as a backup, etc.

Can someone tell me how to mount it?

---

### Post by bertlacy on 2007-08-09
Ok, i have an update to this post...

I did a 'sudo fdisk -l' and I get this...

Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       38536   309540388+  83  Linux
/dev/hda2           38537       38913     3028252+   5  Extended
/dev/hda5           38537       38913     3028221   82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sda doesn't contain a valid partition table


I want to mount the drive in /dev/sda but I don't know how.  :(

---

### Post by Inxsible on 2007-08-09
> **bertlacy said:**
> Ok, i have an update to this post...

I did a 'sudo fdisk -l' and I get this...

Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       38536   309540388+  83  Linux
/dev/hda2           38537       38913     3028252+   5  Extended
/dev/hda5           38537       38913     3028221   82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

[COLOR=Red] Disk /dev/sda doesn't contain a valid partition table[/COLOR]


I want to mount the drive in /dev/sda but I don't know how.  :(That sounds ominous !!

Does your 250GB drive work in windows ? are you able to read/write to it using other OS

Did you delete the partitions on it and never format it to any file system?

---

### Post by bertlacy on 2007-08-09
No, this is a brand new hard drive that i just installed.  I want to be able to back stuff up there but don't know how.

Does this help or do you need more info?

---

### Post by natakim on 2007-08-10
perhaps you need to format it first?

similar thing happened when i bought a couple of new drives, used gpartition to format as ext3.

---

### Post by bertlacy on 2007-08-10
Ok, but do i need to format it since it is brand new and never been used?

I could be totally wrong here, if i am. please tell me how to do this.

---

### Post by Inxsible on 2007-08-10
> **bertlacy said:**
> No, this is a brand new hard drive that i just installed.  I want to be able to back stuff up there but don't know how.

Does this help or do you need more info?Well, if it isnt formatted, then the first thing to do would be to format it in a file system of your choice.

NTFS - Native Windows - Linux can read. Writing with ntfs-3g

EXT3 - Native Linux - Windows can read/write by installting Fs-Driver

FAT32 - Native to both - but cannot handle files > 4GB

others like reiserfs4, jfs etc.

You can use GParted on the LiveCD to format it and even create partitions on it. You can find GParted under System --> Administration --> GParted on the LiveCD.

Hope that helps !

---

### Post by bertlacy on 2007-08-10
Ok, i am foinf to download Gparted and see if I can get it to work.

Would a simple 'mount ...' command work?

---

### Post by natakim on 2007-08-10
> **bertlacy said:**
> Ok, but do i need to format it since it is brand new and never been used?

I could be totally wrong here, if i am. please tell me how to do this.

yes, i think, as i did.


go: main menu/system/admin/gnome partition editor

---

### Post by natakim on 2007-08-10
> **bertlacy said:**
> Ok, i am foinf to download Gparted and see if I can get it to work.

Would a simple 'mount ...' command work?

doubt it.

---

### Post by bertlacy on 2007-08-10
Ok, i have Gparted up and it states the sda (the drive I want to use) is unallocated.

So...  Do i want to partition it as windows, linux, etc.

Sorry guys for all the questions.

---

### Post by natakim on 2007-08-10
personally i'd be happier with ext3. i heard bad things about ntfs, and ext3 is journaled (apparently better filling system, ie no defrag). the drivers for windows are good (FS-driver), so if you dual boot windows can rw to the disk.

---

### Post by bertlacy on 2007-08-10
Ok, do i need to make it as the 'Primary Partition' or 'Extended'?

---

### Post by Inxsible on 2007-08-10
> **bertlacy said:**
> Ok, do i need to make it as the 'Primary Partition' or 'Extended'?
you can have as many partitions as you like. but i guess 1 would suffice. make it a primary partition

---

### Post by natakim on 2007-08-10
> **bertlacy said:**
> Ok, do i need to make it as the 'Primary Partition' or 'Extended'?


this i can't remember. sorry. maybe try primary.

edit: listen to the one above (inxsible), i think it is a safe bet that they know.

---

### Post by kevin11951 on 2007-08-10
ok, here is what to do, if everyone else is right. 
[LIST]
[*]boot into your regular ubuntu hdd
[/LIST]
[LIST]
[*]go to add/remove programs
[/LIST]
[LIST]
[*]Install  Gnome Partition Editor
[/LIST]
[LIST]
[*]Open gnome partition editor in system > Administation.
[/LIST]
[LIST]
[*]click the drop down box, top right
[/LIST]
[LIST]
[*]click on the external hdd
[/LIST]
[LIST]
[*]unmount hdd IN GNOME PARTITION EDITOR if needed
[/LIST]
[LIST]
[*]delete all partition
[/LIST]
[LIST]
[*]right click> new*
[/LIST]
[LIST]
[*]create fat32 partition (leave all else deafult)
[/LIST]
[LIST]
[*]APPLY EVERYTHING!!!
[/LIST]
[LIST]
[*]close gnome partition editor
[/LIST]
[LIST]
[*]un-plug, replug hdd
[/LIST]
[LIST]
[*]done!
[/LIST]

---

### Post by bertlacy on 2007-08-10
Ok, i formatted it as a Primary partition.  Now how do i save files to it?

---

### Post by natakim on 2007-08-10
> **bertlacy said:**
> Ok, i formatted it as a Primary partition.  Now how do i save files to it?


i believe you will need to create a mount point etc.

but try the shutdown, disconnect, reconnect, then startup. the system may detect it at start-up. if so it's easier than creating mount points yourself, i always run into some headache here.

i assume you will then have to change the ownership permissions.

---

### Post by kevin11951 on 2007-08-10
it should be right there on desktop, if your permissions are wrong type "sudo chmod -R 777 /directory of drive" in terminal

---

### Post by bertlacy on 2007-08-10
ok, i rebooted and the drive is there on the desktop and under filesystems.  But i can't write to it so i need to change the permissions.

---

### Post by kevin11951 on 2007-08-10
also to make sure the files stay there you need to UNMOUNT it, not just unplug it, and you will NEED this script: "gksu umount /directory of drive" create a unmount.sh file in gedit, and then set permission to allow you to execute it as program under properties of the file.

---

### Post by HermanAB on 2007-08-10
OK, here is what you got to do:
a. Find out exactly what the device name is: /dev/sda, /dev/sdb or whatever.  This requires a little bit of sleuthing.  If you use the command 'mount' or 'df' you'll see the drives that are already mounted and working.  The command 'ls /dev' will show you all devices.  If you see /dev/sdb but it isn't listed by 'mount' or 'df', then that is the one.
b. Create a file system a.k.a. format it using the command:
sudo mkfs.ext3 -j /dev/sdb
c. Create a mount point for the drive, for example /data with the command:
sudo mkdir /data
d. Mount the drive:
sudo -t ext3 /dev/sdb /data

The drive will now be accessible as /data.

You should now add an entry to the file /etc/fstab to ensure that it will be mounted automatically next time you boot up:
sudo gedit /etc/fstab
(Copy a similar line and change the obvious things)

Cheers,

Herman

---

### Post by natakim on 2007-08-10
> **bertlacy said:**
> ok, i rebooted and the drive is there on the desktop and under filesystems.  But i can't write to it so i need to change the permissions.


i always end up going back to this thread to figure out what to do. i'm sure it's simple but somehow something always goes wrong.

[http://ubuntuforums.org/showthread.php?t=456960&highlight=change+name+hard+drive]("http://ubuntuforums.org/showthread.php?t=456960&highlight=change+name+hard+drive")

---

### Post by bertlacy on 2007-08-10
I did that but I get a error listed below...

robert@rubuntu:/$ sudo -t ext3 /dev/sda1 /data
sudo: illegal option `-t'
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }

---

### Post by HermanAB on 2007-08-10
Oooops... sorry!

sudo mount -t ext3 /dev/sda1 /data

---


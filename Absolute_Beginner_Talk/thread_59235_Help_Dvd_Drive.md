---
title: "Help Dvd Drive"
date: 2005-08-23
forum: Absolute Beginner Talk
---

### Post by evansa4 on 2005-08-23
Hi i just installed a dvd how do i get linuxs to find it

---

### Post by vruum on 2005-08-23
Chances are Ubuntu's already as found it, try putting an audio or data cd in, an icon should appear on your desktop. If it doesn't, you could maybe see if it shows in your /dev directory

---

### Post by evansa4 on 2005-08-23
yes it has found it BUT i have 2 drives a cd rw and a dvd and it only show the cdrw but when i put a disk in the dvd it opens and when i put 1 in the cdrw is opens and when i put a disk in each drives nothing happens

---

### Post by vruum on 2005-08-23
hmm, okay, i'm not really sure what you're saying, does the dvd "disappear" from the desktop, when you put something in the cd-rw? wild speculation might suggest a problem with your fstab. How does the file /etc/fstab look ?

---

### Post by evansa4 on 2005-08-23
dont 1 there tyied it in termial and it said

adam@Adam:~$ /etc/fstab
bash: /etc/fstab: Permission denied

also tyied

adam@Adam:~$ sudo /etc/fstab
Password:
sudo: /etc/fstab: command not found
 
not working

---

### Post by Stormy Eyes on 2005-08-23
Try **sudo less /etc/fstab** instead if you just want to view it, and **sudo nano /etc/fstab** if you want to alter it. But don't alter /etc/fstab unless you know what you're doing. If you screw up that file, Linux won't be able to mount your filesystems the next time you boot. That means that you won't be able to see your data, or possibly even run your system. So be careful with /etc/fstab. In fact, be careful with everything in /etc.

---

### Post by evansa4 on 2005-08-23
ok this is what came up 


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

/dev/hdb1 /mnt/winXP ntfs ro,auto,uid=1000,gid=1000 0 0

---

### Post by Stormy Eyes on 2005-08-23
Your CD-RW drive is showing up as /dev/hdc. Chances are that your DVD drive is showing up as /dev/hdd if you installed it on the same IDE bus as your CD-RW drive. I'm going to tell you exactly what you have to do, so please paste the commands carefully.

1. **sudo mkdir /media/dvd** -- this will create an entry in your /media directory.

2. **sudo ln -s /dev/hdd /dev/dvd** -- movie players usually look for /dev/dvd when playing DVDs.

3. **sudo gedit /etc/fstab** -- It's easier to copy and paste in a GUI filemanger when you're a newbie.

4. Copy the following line:

**/dev/hdc /media/cdrom0 udf,iso9660 ro,user,noauto 0 0**

and paste it on a new line.

5. In the line you just pasted into /etc/fstab, change "/dev/hdc" to "/dev/hdd" and change "/media/cdrom0" to "/media/dvd". Save your changes, and close the text editor.

6. Now pop in a DVD and see if that works. If so, you should be able to open up the DVD in Nautilus and browse its contents under /media/dvd.

---

### Post by evansa4 on 2005-08-23
ok did the first 2 commands in termial what do u mean bye next 2

---

### Post by Stormy Eyes on 2005-08-23
[QUOTE=evansa4]ok did the first 2 commands in termial what do u mean bye next 2[/QUOTE]

Doing "sudo gedit /etc/fstab" will open the /etc/fstab in GNOME's text editor so that you can alter it. That's step 3.

Step 4 requires that you find the line that begins with "/dev/hdc", highlight it, and copy it. You must then create a blank line and paste what you just copied. 

Finally, Step 5 requires that you change "/dev/hdc" to "/dev/hdd" and "/media/cdrom0" to "/media/dvd" in the line you just pasted in the text editor window.

---

### Post by evansa4 on 2005-08-23
ok did that now what do i do?


will i have my cdrw and dvd rom woking?


they  are too diffent drives

---

### Post by Stormy Eyes on 2005-08-23
[QUOTE=evansa4]ok did that now what do i do?[/quote]

Show me your /etc/fstab file now that you've made the changes I told you to make.

[QUOTE=evansa4]will i have my cdrw and dvd rom working?[/QUOTE]

They should, if you followed my instructions. Let's have a look at your /etc/fstab.

---

### Post by vruum on 2005-08-23
They should both work now, if we fixed the right problem  ;-)

---

### Post by Stormy Eyes on 2005-08-23
[QUOTE=vruum]They should both work now, if we fixed the right problem  ;-)[/QUOTE]

In other words, if Linux detected the second drive but doesn't know what to do with it, it should know now. But we have to wait for evansa4 to post his current /etc/fstab.

---

### Post by evansa4 on 2005-08-23
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/dvd   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

/dev/hdb1 /mnt/winXP ntfs ro,auto,uid=1000,gid=1000 0 0

/etc/fstab


will another cd icon apper in my computer?

---

### Post by Stormy Eyes on 2005-08-23
[QUOTE=evansa4]will another cd icon apper in my computer?[/QUOTE]

No. You did not follow my instructions correctly. You were supposed to copy the /dev/hdc line, create a *new line*, and paste what you copied into the new line. I'll show you what you should have had:

```
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0

/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/dvd   udf,iso9660 ro,user,noauto  0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

/dev/hdb1 /mnt/winXP ntfs ro,auto,uid=1000,gid=1000 0 0
```

Notice that there should be an entry for **both** /dev/hdc *and* /dev/hdd. Paste the above into your /etc/fstab after wiping out what's already there, and then save. This should give you what you want.

---

### Post by evansa4 on 2005-08-23
ok did what u said now what?

---

### Post by vruum on 2005-08-23
is it working now?

---

### Post by evansa4 on 2005-08-23
yes i have 2 roms installed thanks verrry much now is it ok if you try and help me with my 2nd hdd drive please

---

### Post by vruum on 2005-08-23
I don't know how much help i've been, if any. 
but i'll try. what's wrong with your hdd?

---

### Post by evansa4 on 2005-08-23
same thing linuxs is not picking it up

---

### Post by vruum on 2005-08-23
okay, is it the one with windows on it?

---

### Post by Stormy Eyes on 2005-08-23
Did you try **sudo mount /mnt/winXP**?

---

### Post by evansa4 on 2005-08-23
yes this came up 

wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by Stormy Eyes on 2005-08-23
[QUOTE=evansa4]yes this came up 

wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/QUOTE]

OK. I want you to try the following commands:

1. **ls -al /mnt/winXP** -- let's see if the mount point exists.
2. **sudo mount -t ntfs /dev/hdb1 /mnt/winXP** -- manually mount the partition

---

### Post by evansa4 on 2005-08-23
ok tryed first 1 this came up

adam@Adam:~$ ls -al /mnt/winXP
total 8
drwxr-xr-x  2 root root 4096 2005-08-22 15:12 .
drwxr-xr-x  3 root root 4096 2005-08-22 20:08 ..

---

### Post by Stormy Eyes on 2005-08-23
[QUOTE=evansa4]ok tryed first 1 this came up

adam@Adam:~$ ls -al /mnt/winXP
total 8
drwxr-xr-x  2 root root 4096 2005-08-22 15:12 .
drwxr-xr-x  3 root root 4096 2005-08-22 20:08 ..[/QUOTE]

OK, did you try the second command?

---

### Post by evansa4 on 2005-08-23
yes it came up 

mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by vruum on 2005-08-23
do you know which filesystem the drive is? if not try:

sudo parted /dev/hdb

and press "p", it will show a list of filesystems on /dev/hdb, your 2nd drive

---

### Post by evansa4 on 2005-08-23
yes winxp formated buy nfts

---

### Post by vruum on 2005-08-23
are you able to boot xp? just to make sure the drive is not damaged?

---

### Post by evansa4 on 2005-08-23
no xp IS not on that drive its a spare 1 for data sore

---

### Post by Stormy Eyes on 2005-08-23
Since I don't dual boot or have any NTFS partitions, I can't offer any further help. [You might find something on Google, though.](http://www.google.com/search?q=ntfs+%22missing+codepage+or+other+error%22&sourceid=mozilla-search&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox-a&rls=org.mozilla:en-US:official)

---

### Post by vruum on 2005-08-23
okay, I'm kinda guessing here. but try mounting the drive without any parameters:

sudo mount /dev/hdb1 /mnt/winXP

if that doesn't work try

sudo mount -tntfs /dev/hdb1 /mnt/winXP

followed by :

dmesg | tail,
 
and post the output here. 

also to list the disks Linux knows about
type:

ls /dev | grep hd

---

### Post by evansa4 on 2005-08-23
look i have 2 hdd one is a 10 gig linuxs is on and a 2nd 20 gig wich is spare and linuxs is not picking it up and hdb1 is the first hdd that will reck my system if i do any thing 2 it

---

### Post by vruum on 2005-08-23
well, since you do have a /dev/hdb1 linux is obviously picking it up, it just can't read from it. I was only trying to figure out why that is. but hey.

---

### Post by evansa4 on 2005-08-23
here is my hdds

hda
hda1
hda2
hda5
hdb
hdb1
hdc
hdd

---

### Post by vruum on 2005-08-23
Okay, thanks. to find out what kind of drive Linux thinks hdb1 is, try:

sudo parted /dev/hdb

and pressing "p" will print the partition table of the drive, it wont destroy anything. If /dev/hdb1 is listed as ntfs then it should work, but for some reason isn't. 

so, if /dev/hdb1 is listed as ntfs then try mounting it again, and when it fails, type:

dmesg | tail  

and post the output here.

---

### Post by evansa4 on 2005-08-23
ok the 1st command said this

Disk geometry for /dev/hdb: 0.000-19536.767 megabytes
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags
1          0.031  19524.309  primary               boot

also this said dmesg | tail

NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device hdb1): ntfs_fill_super(): Not an NTFS volume.
NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device hdb1): ntfs_fill_super(): Not an NTFS volume.
VFS: Can't find ext3 filesystem on dev hdb1.
NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device hdb1): ntfs_fill_super(): Not an NTFS volume.

---

### Post by vruum on 2005-08-23
it looks like it's a fat32 system try mounting it without parameters:

sudo mount /dev/hdb1 /mnt/winXP
*edit* it actually looks like there's no filesystem on it. are you sure it's formatted correctly?

---

### Post by evansa4 on 2005-08-23
how is it when i formated it with nstf

---

### Post by evansa4 on 2005-08-23
and this happens 

adam@Adam:~$ sudo mount /dev/hdb1 /mnt/winXP
mount: you must specify the filesystem type

---

### Post by vruum on 2005-08-23
Okay, I'm about to give up since I don't really have a ntfs drive to test on. I've got just a few suggestions left. 
1: boot into windows and check that the drive is ntfs and that there are no errors on        
    it. 
2: if the drive is empty or the data on it can be stored somewhere else. wipe it and 
    format it in fat32 as linux can't write to ntfs.
3: wait, someone else is bound to have had similar problems, did you check out 
    stormy eyes' googles?

sorry, I suck.

---

### Post by evansa4 on 2005-08-23
[QUOTE=vruum]Okay, I'm about to give up since I don't really have a ntfs drive to test on. I've got just a few suggestions left. 
1: boot into windows and check that the drive is ntfs and that there are no errors on        
    it. 
2: if the drive is empty or the data on it can be stored somewhere else. wipe it and 
    format it in fat32 as linux can't write to ntfs.
3: wait, someone else is bound to have had similar problems, did you check out 
    stormy eyes' googles?

sorry, I suck.[/QUOTE]

i dont have windows the 2nd hdd is used for a speare and will format to fat32

---


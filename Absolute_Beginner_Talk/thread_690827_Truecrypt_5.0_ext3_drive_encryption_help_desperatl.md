---
title: "Truecrypt 5.0 ext3 drive encryption help desperatly needed"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by kingleer on 2008-02-07
Edit: I solved my problem. 

Problem: Truecrypt 5.0 was being a royal pain in the ***. 

Solution: Go back to truecrypt 4.3a.

Doddo, thanks. Your instructions are what I basically did. Works great in TC 4.3a where I've got the CLI, not in TC 5. 

Anyway, I only occasionally play with truecrypt and don't really use it. I was just pissed that TC 5 wasn't working when I tried experimenting with it.

---

### Post by doddo on 2008-02-08
Hello there!

This sounds like a whole lot of job for what I've experienced to be a quick and easy task.

This is how I use to set up encrypted devices (never had any trouble with reiserfs, xfs nor ext3)

These steps:
1. Plug in the device
2. use "dmesg" to determine what drive it is

3. The next step would be to create a partition table to the disk. One can make one partition of the whole disk.

4. encrypt the device. For this example, lets say the disk is sdb and the partition to encrypt is 1, so sdb1 then.
```
 $ sudo truecrypt -c /dev/sdb1
```
truecrypt will now prompt for all questions. I do not make a VFAT file system  at this point.

5. once done, have truecrypt map the device, like
```
truecrypt /dev/sdb1
```
6. Write the file system.
6.1 Locate the mapped drive
```
 doddo@r0mulan ~ $ sudo truecrypt -l
/dev/mapper/truecrypt0 /dev/sdb1 
```

6.2 choose fstype. You wanted ext3, so the proper command would be
```
 sudo mkfs.ext3 /dev/mapper/truecrypt0
```

7 mount the device (i have /mnt/disk as mountpoint for this example)
```
 sudo mount /dev/mapper/truecrypt0 /mnt/disk
```
All done! Great

From now on, you can mount the device with
```
truecrypt /dev/sdb1 /mnt/disk
```

---

### Post by MacGeneral on 2008-02-16
[COLOR="Red"]**Warning: The device I used in this short tutorial is */dev/sda1* - you have to alter it to fit your needs (and make sure you select the correct device before doing any of this!)**[/COLOR]

**If you want to use TrueCrypt in a "terminal-mode" only, use [COLOR="DarkRed"]truecrypt -t (...)[/COLOR] instead of *truecrypt (...)*!**


1. Encrypt the whole partition with the TrueCrypt 5 GUI
[LIST]Configure as needed[/LIST]
[LIST]Select Filesystem "None"[/LIST]


2. Mount the TrueCrypt volume
```
truecrypt /dev/sda1 --filesystem=none
```

TrueCrypt will pop up window asking for your (sudo, not su) password.

**Note: this will actually NOT mount the volume, but it will unlock it so you can access it to change the fs-type**


3. Check which "loop device" is used by TrueCrypt
```
truecrypt -l
```

It should return something like
> 1: /dev/sda1 /dev/loop0 -
in a window


4. Format the TrueCrypt Volume with ext2/ext3/reiserfs 
```
sudo mkfs.ext3 /dev/loop0
```
(mkfs.* = ext2, ext3, hfsplus, vfat etc pp)

**Note: Never format /dev/sda1 etc directly if you plan to use it along with TrueCrypt because it will remove all the previously set up encryption!!**


That's it, now unmount all Volumes with the TrueCrypt GUI or with
```
truecrypt -d /dev/sda1
```

and remount it using the GUI (or command line)
```
truecrypt /dev/sda1 /path/to/mountdirectory
```


have fun ;)

---

### Post by skralljt on 2008-02-22
If anybody has been having problems with the directions mentioned in the previous posts, specifically mkfs stalling while writing inode tables:  you must try this command in a terminal:  export MKE2FS_SYNC=10.  This came from the truecrypt forums not a moment too soon, I already had several resets because of mkfs stalling, and having to do lots of fscks on the reboot.  Also note that this command allows you to write an ext3 filesystem even though it says mke2fs, according to others who have tried it.

edit:  now when  I run the command sudo cp -ruv /media/drive /media/truecrypt1 my system copies files for a half hour or so and then locks up again.  argh.

---

### Post by skralljt on 2008-02-22
If anybody has been having problems with the directions mentioned in the previous posts, specifically mkfs stalling while writing inode tables:  you must try this command in a terminal:  export MKE2FS_SYNC=10.  This came from the truecrypt forums not a moment too soon, I already had several resets because of mkfs stalling, and having to do lots of fscks on the reboot.  Also note that this command allows you to write an ext3 filesystem even though it says mke2fs, according to others who have tried it.

edit:  now when  I run the command sudo cp -ruv /media/drive /media/truecrypt1 my system copies files for a half hour or so and then locks up again.  argh.

second edit:  you can fix this problem by mounting with some sort of sync option in kde or upgrading to the new 8.04 kernel which is in alpha.  here is the output of dmesg right when my box becomes unresponsive:  
"Feb 22 12:40:38 amd64 kernel: [  564.707609] EXT2-fs error (device loop0): ext2_free_inode: bit already cleared for inode 11405207"

the problem is that there are several bugs in the 7.10 kernel that cause it to stall when writing to a truecrypt device or container.  compiling from source does not solve the problem.

---

### Post by shanepardue on 2008-03-06
Is there a way to check and see which filesystem your encrypted device is formatted with? 
I followed this guide to change my truecrypt device to reiserfs, but the properties still show
 "vfat". Thanks for your help.

---

### Post by shanepardue on 2008-03-06
> **shanepardue said:**
> Is there a way to check and see which filesystem your encrypted device is formatted with? 
I followed this guide to change my truecrypt device to reiserfs, but the properties still show
 "vfat". Thanks for your help.
I take that back..I can confirm it's still fat32, but I've used the "sudo mkfs.reiserfs /dev/loop0" 
command to no avail. I always make sure to unmount the encrypted device first..I'm not 
supposed to use the command with an -f tag on a mounted device am I?

edit: I missed this command: truecrypt /dev/sda1 --filesystem=none

---

### Post by bruncio on 2008-03-15
Unfortunately it seems like it's not the problem of the ubuntu 7.10 kernel. TC 5.1  doesn't work with the custom build (from vanilla sources) 2.6.24.3 kernel either - it hangs after writing several MBs. The only solution (besides using TC 4.3a) is to use sync mount option, but after that the transfer drops below 3MB/s.

---

### Post by skralljt on 2008-03-29
the export mke2fs sync command doesn't help for making an ext3 filesystem; at the journal creation stage the whole thing goes tits up.  I guess that I am stuck with ext2!

---


---
title: "NTFS help"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by podean on 2006-02-16
Hi. I'm as n00b as n00b could be right now...

If there is a topic already about this, pardon me please! :(  I couldn't find it and don't see a search thing.

Well I've known about Ubuntu for a while, and decided to install it yesterday. I had Windows XP formatted hard drives, with the NTFS. I have 2 hard drives.

I backed up all my data onto the second hard drive. (pictures and whatnot). 

The second drive is NTFS, as stated, and I'm wondering if someone could teach me how to read from/copy from that drive into this one. There has to be a program or something... I just can't find it. And I've been looking all night!

I don't want to reinstall Windows just to get my files.

This is just a basic question. \\:D/ 

Thanks


---------

fstab contents:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by carlosqueso on 2006-02-16
you can read from it....but you won't be able to write to it.   I've also found that using the mount command doesn't seem to work too well.  Anyway....

First, let's get some information, can you post the contents of your fstab file? type ```
sudo gedit /etc/fstab
``` leave the window with your fstab file open, because we're going to edit it in a minute.

---

### Post by podean on 2006-02-16
[QUOTE=carlosqueso]you can read from it....but you won't be able to write to it.   I've also found that using the mount command doesn't seem to work too well.  Anyway....

First, let's get some information, can you post the contents of your fstab file? type ```
sudo gedit /etc/fstab
``` leave the window with your fstab file open, because we're going to edit it in a minute.[/QUOTE]

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



hope this will help?

---

### Post by frodon on 2006-02-16
Your best friend is the ubuntu starter guide ;) : [http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

---

### Post by carlosqueso on 2006-02-16
yes, it helps quite a bit.  Ok, so you first need to open up another terminal window and type ```
sudo mkdir /mnt/seconddrive
``` where seconddrive can be what you want to call the second hard drive.  Now type ```
sudo fdisk -l
``` in the terminal and you should see something like ```
/dev/hdb1     <number>    <number>    <number>    <number>   <something about windows>
```  we need the device (the /dev/hdb1) number.  Once you know that number, go back into your fstab file  and add the line: ```
/dev/hdb1 /mnt/seconddrive ntfs umask=0222
``` but replace the hdb1 with whatever number we found in the second step and seconddrive with the name of the directory you made in the first.  Close and save your fstab file and type ```
sudo mount -a
``` and you should be good to go.

---

### Post by podean on 2006-02-16
ok

so I added this line:

/dev/sda1 /mnt/seconddrive ntfs umask=0222

(since I just named it seconddrive... seemed logical)

HMM

---

### Post by podean on 2006-02-16
but now what :s

---

### Post by podean on 2006-02-16
Ok, so I assume this is the one...

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2430    19518943+   7  HPFS/NTFS


Yes... so I did that...

edit

I went to the new directory... but there's nothing there. I'm confuuused.

---

### Post by carlosqueso on 2006-02-16
you shouldn't have added sda1.  your last line in your fstab needs to look like 

```
/dev/hdb1 /mnt/seconddrive ntfs umask=0222
```  then you should be able to type ```
sudo mount -a
``` and afterwards be able to navagate to the /mnt/seconddrive directory.

---

### Post by podean on 2006-02-16
ok i did that... but I still dont see the files. should I try rebooting? (even though I shouldnt have to)?

edit

NEVERMIND IT WORKED

THANK GOD

AND THANK YOU!

:)))))

---

### Post by carlosqueso on 2006-02-16
It can't hurt.....did you close and save the fstab file before you did sudo mount -a?  If you did, try rebooting and it SHOULD work.

---

### Post by podean on 2006-02-16
[QUOTE=carlosqueso]It can't hurt.....did you close and save the fstab file before you did sudo mount -a?  If you did, try rebooting and it SHOULD work.[/QUOTE]


it worked :) \\:D/ 

I can finally get on with my life.

I <3 Ubuntu Linux

---

### Post by carlosqueso on 2006-02-16
Awesome!  You're most welcome...and I'm glad you love Ubuntu!

---


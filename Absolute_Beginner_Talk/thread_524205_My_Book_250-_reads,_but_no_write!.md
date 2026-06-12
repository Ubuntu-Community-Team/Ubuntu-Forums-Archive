---
title: "My Book 250- reads, but no write!"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by pyrplhaze on 2007-08-12
Hello all from a total noob....I am sure my problem has a fairly simple fix, I just don't know what it is, or even where to start looking.

My WD My Book 250 will read (I can watch video, listen to music, etc..) but I cannot save anything to it.  The error says "You do not have permissions to write to this folder"

I am sure I am just missing something, but this is really making me go nuts. 

Any, and all, help appreciated!

thanks

---

### Post by bren on 2007-08-12
is this mybook 250 an NTFS formatted drive

post results of 

> sudo fdisk -l

so we can see for sure.

if it is NFTS then you need to install ntfs-3g before you can write (read only is default)

> sudo apt-get install ntfs-3g

sudo ntfs-config

hope that helps

bren

(if it doesnt then search on here for chown and permissions..... this is the second thing to try)

---

### Post by yabbadabbadont on 2007-08-12
Edit: Too late.  Never mind.

---

### Post by pyrplhaze on 2007-08-12
Thanks for the reply...will try this later tonigt when I am on my comp.

later.

---

### Post by pyrplhaze on 2007-08-13
Ok, heres what I've got...from what I can tell, it looks like it is NTFS 
> Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5874    47182873+   7  HPFS/NTFS
/dev/sda2            5875        7231    10900102+  83  Linux
/dev/sda3            7232        7297      530145    5  Extended
/dev/sda5            7232        7297      530113+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 1994 MB, 1994227200 bytes
4 heads, 16 sectors/track, 60858 cylinders
Units = cylinders of 64 * 512 = 32768 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60859     1947479+   e  W95 FAT16 (LBA)


So, upon my assuming that it is NTFS, I went ahead with the install of ntfs-3g.  Once installed, I try and run the "config" command, and this is what I get:
> sudo: ntfs-config: command not found


Sooooo...I guess I am either not doing something right, or just plain missing something.  Whatever it is, I am still getting the same message when I try and write to that drive...the one about not having permissions to write to that folder.

Any more suggestions would be welcome!

thanks!

---

### Post by Ek0nomik on 2007-08-13
> **pyrplhaze said:**
> Ok, heres what I've got...from what I can tell, it looks like it is NTFS 


So, upon my assuming that it is NTFS, I went ahead with the install of ntfs-3g.  Once installed, I try and run the "config" command, and this is what I get:


Sooooo...I guess I am either not doing something right, or just plain missing something.  Whatever it is, I am still getting the same message when I try and write to that drive...the one about not having permissions to write to that folder.

Any more suggestions would be welcome!

thanks!

You don't need a colon after sudo.  Try this (Accessories/Terminal):

```
gksudo ntfs-config
```

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)
[http://doc.gwos.org/index.php/NTFS-3g](http://doc.gwos.org/index.php/NTFS-3g)
[http://ubuntuos.wordpress.com/2006/08/02/howto-write-to-windows-ntfs-drive-from-ubuntu-ntfs-3g/](http://ubuntuos.wordpress.com/2006/08/02/howto-write-to-windows-ntfs-drive-from-ubuntu-ntfs-3g/)

---

### Post by pyrplhaze on 2007-08-13
sweet.  ok, so that did something.  I just have no clue as to what it did.  after entering "gksudo ntfs-config"  the screen dimmed, and asked me for my password.  I entered my password, and nothing happened!

oh, and I didnt enter the colon, that was the response...this is how it went down...
> josh@josh-desktop:~$ sudo ntfs-config
sudo: ntfs-config: command not found


ideas?

---

### Post by Ek0nomik on 2007-08-13
> **pyrplhaze said:**
> sweet.  ok, so that did something.  I just have no clue as to what it did.  after entering "gksudo ntfs-config"  the screen dimmed, and asked me for my password.  I entered my password, and nothing happened!

oh, and I didnt enter the colon, that was the response...this is how it went down...


ideas?

You probably didn't install it.  :lol:

```
sudo apt-get install ntfs-config
```

*Then* try to run it.

---

### Post by pyrplhaze on 2007-08-13
ok, we're in business, I think...

a little window popped up that says "the following new partitions were detected and can be configured"

only issue is that  /dev/sda1 is the only one listed...and if I am reading correctly, my external is /dev/sdb

any way to add /dev/sdb to the list?

---

### Post by Ek0nomik on 2007-08-13
> **pyrplhaze said:**
> ok, we're in business, I think...

a little window popped up that says "the following new partitions were detected and can be configured"

only issue is that  /dev/sda1 is the only one listed...and if I am reading correctly, my external is /dev/sdb

any way to add /dev/sdb to the list?

It may take a restart for it to appear.

You will want to add an entry to your /etc/fstab file so the drive is mounted everytime you startup (you don't have to, but I presume you want this done as it makes things a little easier)

First, create a directory for your drive to be mounted to:

```
mkdir /media/anyNameyouWant
```

If it gives you an error about permissions, put 'sudo', without the ' in front of the command.

*If* you had to use sudo, run this:

```
sudo chown yourUsername:yourUsername /media/anyNameyouWant
```

Now we need to edit the fstab file.

First, create a backup:

```
sudo cp /etc/fstab /etc/fstab.08.13.2007
```

Now open the file to edit it:

```
gksudo gedit /etc/fstab
```

Add this entry to your fstab:

```
/dev/sdb1 /media/anyNameyouWant ntfs-3g defaults,locale=en_US.utf8 0 0
```

Restart, and hopefully it will automount.

Let me know how things go.  :)

---

### Post by pyrplhaze on 2007-08-13
Awesome...I really appreciate this.  All it took was a restart, and we are cruisin!  I knew it wouldn't be to terribly hard!  Thanks so much!

And forgive me for being ignorant of the lingo, but if "mounting" the drive means to enable the use of the drive, this happens on startup...It has always shown up on my desktop as an icon labled "My Book"

so do I still need to run that code?

---

### Post by Ek0nomik on 2007-08-13
> **pyrplhaze said:**
> Awesome...I really appreciate this.  All it took was a restart, and we are cruisin!  I knew it wouldn't be to terribly hard!  Thanks so much!

And forgive me for being ignorant of the lingo, but if "mounting" the drive means to enable the use of the drive, this happens on startup...It has always shown up on my desktop as an icon labled "My Book"

so do I still need to run that code?

The 'MyBook' icon is just a shortcut to accessing the files on the drive, correct?

You can remove the icon from your desktop if you wish:

```
gksudo gconf-editor
```

Then I believe it is under Nautilus/Desktop, and you uncheck a show_drives field.  I am at work with Windows, so I can't see it in front of me.  But I think my memory is sharp.  :)

---

### Post by pyrplhaze on 2007-08-13
Yep.  Just a shortcut.

Lol, your memory seems to be doing fine thus far, so I trust ya :)

once again, I really appreciate the help...my linux experience just got better!

thanks!

---


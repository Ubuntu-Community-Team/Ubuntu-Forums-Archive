---
title: "data restoration with Ubuntu?"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by dibdib on 2007-08-22
I'm new to Ubuntu and Linux in general.  Does Ubuntu have any data restoration tools available when booting off the cd, and if so how do I use them to recover a hard drive?  I already have an external usb drive for recovery.

---

### Post by Jimmyfj on 2007-08-22
Other than a good backup policy I am not familiar with a restore tool like the one in Windows. I use TimeVault for snapshots and images that I can restore if needed. All my vital data is stored on an external USB disk. I chose this because I run a develop release, Gutsy 7.10 64 bit and know that i WILL break. But you'll never loose any sleep if only you keep your backup up to date.

---

### Post by dibdib on 2007-08-22
It's not a backup issue, so much of an issue with waking this morning to find my XP installation won't boot, and after attempting all software solutions the fact that chkdsk won't run suggests to me that the hard drive may have finally blown after a meager two years.  I'm not certain, but before I mess around with anything I would really like to get my data to a safe place.  This is sort of last ditch effort, I already dissected two laptops this morning trying to slave the drive and access it that way.

How about changing access permissions on my USB external drive under Ubuntu to read/write?  Right now it's mounted but set to read only.  Under /media, directory access for owner/group/others under properties are all greyed out with the message "You are not the owner, so you can't change these permissions."  Under Computer I can click any but it gives me the error "Sorry, couldn't change the permissions of <label>"  I'm guessing it has something to do with logging in as admin, but I booted off the cd and don't recall ever being asked for login.administrator

---

### Post by Jimmyfj on 2007-08-22
In Ubuntu: 

sudo chown -R USERNAME:USERNAME /media/yourdevice (IE: disk) - This will change ownership to the username you provide.

If the dsk is in NTFS format you need to go to Programs/Add/Remove/System tools and install NTFS Configuration Tools and then enable read/write through that program. Hope I got you right this time, sorry if I didn't.

---

### Post by annda on 2007-08-22
you can use testdisk (it's in the repositories). it's actually designed for recovering lost/deleted partitions, but who knows, it might help you.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by bodhi.zazen on 2007-08-22
What are you trying to do exactly ?

The Ubuntu CD can be used to access (copy/restore) data, but I am wondering if you need more then that ?

---

### Post by dibdib on 2007-08-22
No problems, I appreciate the help.  I'm digging the Ubuntu cd boot so far, the fact that it even functions with my Alienware laptop's hardware is a step over the Knoppix disc I tried a couple months ago.  When I get my system back in working order I'll definitely do a full install and check it out, then learn this stuff the proper way.

I enabled read/write through NTFS config, but I don't think I have the command down.  I entered exactly as shown, "sudo chown -R unbuntu:ubuntu /media/Maxtor" but no changes.  Still can't write to drive nor change permission.

---

### Post by bodhi.zazen on 2007-08-22
Yea, you can not use the chown with FAT/NTFS partitions.

You can either enter this command in a terminal :```
gksu nautilus
```

Or re-mount the partition :

umount /dev/xxxx

mount -t ntfs-3g /dev/xxx /media/xxx -o umask=000

See here :

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)[/indent][/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by dibdib on 2007-08-22
looks good, I need to take off but I'll give it a shot later.  Thanks everybody!

---

### Post by shaggy2dope0001 on 2007-08-29
hey annda,  

i was looking through this post just to see if i could find any info and guess what... you had already posted what i was needing. just wanting to say thankya very much. i had a ntfs partition completely disapear and your link to the testdisk was exactly what i needed. it fixed my problem in no time flat and the only other way i had to get my data back was going to take somewhere in the neighborhood of a week. 

now if there was only a way to convert the partition over to another type without formatting i would like to know how also... if ya can help would be appreciated

---

### Post by splintercellguy on 2007-08-29
GPartEd MIGHT be able to but I'm not entirely sure.

---

### Post by shaggy2dope0001 on 2007-08-30
well right now i am backing up everything i have to an external also formatted to ntfs but i should be able to reformat the internal drives after that to fat32 and i shouldnt have any problems but its going to take some time

---

### Post by shaggy2dope0001 on 2007-09-06
no gparted wouldnt do it but i can manage just by creating back ups and reformating so that its all in fat32 so that my windows and my ubuntu can both have full rights to the drives.  do you know if there is a manual i might be able to download that can help with doing things in ubuntu?  well all smiles from me so far still got a few things to work out b4 i completely go over.

---


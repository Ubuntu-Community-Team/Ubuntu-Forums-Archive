---
title: "os x/ubuntu partition compatability"
date: 2007-04-11
forum: Apple Intel Users
---

### Post by alSuhail on 2007-04-11
hi everyone,

I'm going to install feisty soon and I'm wondering what the compatability between os x and ubuntu partitions is like. Can I read and write between the two of them or will I need to make a FAT32 partition as common ground for both?

thanks

---

### Post by siepo on 2007-04-11
You can mount a non-journaled hfsplus partition in read-write mode. I guess you could turn journaling off with the os x disk utility. Os x can not read linux partitions, at least not out of the box. I have a fat32 partition for exchanging data because I don't trust Linux' rw support for hfsplus well enough.

---

### Post by cyberdork33 on 2007-04-11
There is a driver to read ext2/3 partitions on OSX. 

[http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/)

---

### Post by viciouslime on 2007-04-11
> **cyberdork33 said:**
> There is a driver to read ext2/3 partitions on OSX. 

[http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/)

It works very well too...

---

### Post by ronocdh on 2007-04-12
> **viciouslime said:**
> It works very well too...

It works GREAT! =) In OS X I can read and write to my Ubuntu partition. The HFS+ part mounts fine in Ubuntu, but you'll notice you can't access your user-specific files... you can get around this by making sure your usernames for OS X and Ubuntu are just the same. If you've already installed and don't want to reinstall (or add a user), you can use the NetInfo Manager utility in OS X to change your username nondestructively.

I have never actually used NetInfo to do this, but I've heard of it being done many times.

---

### Post by cyberdork33 on 2007-04-13
actually I think you have to have matching UIDs...

---

### Post by ronocdh on 2007-04-13
> **cyberdork33 said:**
> actually I think you have to have matching UIDs...

I don't understand the difference. My mistake! I meant "UID" by username, I suppose. =) Anyway, the NetInfo utility is the tool of choice for the job.

---

### Post by jiminy on 2007-04-14
Not exactly—UID is a number, normally set by the system, which goes with your user name . . .

---

### Post by Chrisj303 on 2007-04-14
I installed extfsmanager, and it dosen't do squat! - It sees my ext3 linux partition, but won't mount it at all.It won't even let me try!
I've read some real horror stories regarding changing UID numbers, i don't think it something any regular user should take lightly.
Is their a Terminal command associated with extfs that i could try?


chrisj303

---

### Post by cyberdork33 on 2007-04-14
> **Chrisj303 said:**
> I installed extfsmanager, and it dosen't do squat! - It sees my ext3 linux partition, but won't mount it at all.It won't even let me try!
I've read some real horror stories regarding changing UID numbers, i don't think it something any regular user should take lightly.
Is their a Terminal command associated with extfs that i could try?


chrisj303

What DOES it do? Sometimes it will not mount untill you repair permissions on the partition or something (It should tell you what the problem is in the info screen

---

### Post by Chrisj303 on 2007-04-14
> **cyberdork33 said:**
> What DOES it do? Sometimes it will not mount untill you repair permissions on the partition or something (It should tell you what the problem is in the info screen

It does nothing - it won't even let me attempt to mount my ubuntu partition. I have the latest verion (1.4d). It lists the partition, but it is greyed out. I have already tried repairing permissions but that didn't help.


cheers,
chrisj303

---

### Post by ronocdh on 2007-04-17
> **Chrisj303 said:**
> It does nothing - it won't even let me attempt to mount my ubuntu partition. I have the latest verion (1.4d). It lists the partition, but it is greyed out. I have already tried repairing permissions but that didn't help.


cheers,
chrisj303

Truly a very wild guess: could your boot tables be out of sync? Perhaps OS X is consulting an outdated list when starting up, and that's why you're forced to do a hard mount (although I acknowledge that even that isn't working).

I say you test your ext2fs compatibility by formatting a small external as ext3 (you can use Linux/GParted to do this if you want), and then plug it in and mount it in OS X. If you can't do that, then your ext2fs setup didn't work. You could even do this with a pen drive if you want.

---

### Post by cyberdork33 on 2007-04-17
> **Chrisj303 said:**
> It does nothing - it won't even let me attempt to mount my ubuntu partition. I have the latest verion (1.4d). It lists the partition, but it is greyed out. I have already tried repairing permissions but that didn't help.


cheers,
chrisj303

Even though it is greyed out, you should be able to select it, or select the disk, and look at the info. If you can show us what the info box says then we might be able to help you.

---

### Post by Chrisj303 on 2007-04-17
> **cyberdork33 said:**
> Even though it is greyed out, you should be able to select it, or select the disk, and look at the info. If you can show us what the info box says then we might be able to help you.

Yes, i can still select the partition, even though it is greyed out, but the 'Mount' and 'Info' buttons are also greyed out - nothing happens if i push them.
When i select my ubuntu partition this is what i get in the box to the left:

IOKit Name: Linux
Device: disk0s3
Connection Bus: SATA
Connection Type: Internal
Ejectable: No
DVD/CD: No
Mount Point: Not Mounted
Writable: Yes
Device Size: 20.00 GB (21,474,836,480 bytes)
Device Block Size: 512 bytes

Any help would be appreiciated, i seem to be losing on preety much all fronts!

chrisj303

---

### Post by Chrisj303 on 2007-04-17
> **ronocdh said:**
> Truly a very wild guess: could your boot tables be out of sync? Perhaps OS X is consulting an outdated list when starting up, and that's why you're forced to do a hard mount (although I acknowledge that even that isn't working).

I say you test your ext2fs compatibility by formatting a small external as ext3 (you can use Linux/GParted to do this if you want), and then plug it in and mount it in OS X. If you can't do that, then your ext2fs setup didn't work. You could even do this with a pen drive if you want.


I will try this tommorrow - though i have tried re-installing extfs twice, i can't see how i could have got it wrong...
My tables arn't out of sync - rEFIt say's there not anyway!
cheers,
chrisj303

---

### Post by cyberdork33 on 2007-04-18
well your info looks good. I am at a loss...

---

### Post by withershins on 2007-05-07
I would just like to say that I have the exact same problem with ExtFSManager, and am running the same version.  Really makes me sad.  But I'm really willing to try things out to find a possible solution.  I'm not afraid of the terminal, or even looking at the source code (is it open source?) with the help of instructions.  If anyone has any ideas of what can be done, plz post something!

---

### Post by Chrisj303 on 2007-05-08
Ive now got this sorted to mount my ext3 partition in OSX (using ext2fsmanager) , i first created a folder "UBUNTU" on my desktop.

Then in a terminal i do :

sudo mount_ext2 /dev/disk0s3 /Users/chris********/Desktop/UBUNTU


Note that you must substitute /disk0s3/ for whatever your ubuntu partition is.

At execution of the above, the terminal should give you a "kextloaded succesfully" - or similar.
At this point there is a bit of a GUI bug - the desktop does not update, so it will appear that it did not mount.

From the finder menu:    GO > GO TO FOLDER > (Point to the UBUNTU foder)

The desktop GUI should now update, and you will see your mounted linux partition.

To unmount, which is important, i do :

sudo umount /dev/disk0s3

I have saved both of these commands, as "mount/unmount UBUNTU" within my terminals libary, so the whole process is quicker and cleaner.

Also, once you have mounted via the terminal - you can use extfsmanager to define various options to the mount, as the "options" tab within system prefs is not greyed out.


Hope that helps,

chrisj303


P.s - i am using extfsmanager 1.4d.

---

### Post by withershins on 2007-05-10
Awesome, I'm gonna try this right now.  Thanks for posting this.

EDIT: K so I just tried this and didn't work.  I followed your instructions implicitly.... any ideas?  Once again thanks for helping out.

EDIT 2: Forgot to paste this :)

mount_ext2: open '/dev/diskOs3' failed, No such file or directory
kextload: /Library/Extensions/ext2fs.kext loaded successfully
mount_ext2: /dev/diskOs3 on /Users/*****/Desktop/UBUNTU: No such file or directory

---

### Post by withershins on 2007-05-10
I replaced my "O" in "diskOs3" with 0, and now it works.  That was kinda stupid of me.

---

### Post by darkmaster on 2007-07-10
Here I have another similar weird problem. I partitioned in 2 my disk with bootcamp and then used the Ubuntu installer to partition in 2 the partitioned space so to have a disk for ubuntu (And, yes, a little one for swap file) and another disc with fat32 for OX and Ubuntu to share data but.... OSX doesn't mount automatically the fat32 disc. Why? Does anyone know? I also opened a thread about it but nobody answers.... here's the link. 

[http://ubuntuforums.org/showthread.php?t=495480](http://ubuntuforums.org/showthread.php?t=495480)

If you could help I'd be really thankfull. Probably I'm missing some basic operation???

---

### Post by ultianimal on 2007-08-20
Hey.  I'm trying to implement the fix that Chris suggested, but what is the ***** in the command to mount?  The password I assume?  If so, what spacing?  IE  UsernamePASS or Username PASS?

Help please?


E-man

---

### Post by cyberdork33 on 2007-08-20
> **ultianimal said:**
> Hey.  I'm trying to implement the fix that Chris suggested, but what is the ***** in the command to mount?  The password I assume?  If so, what spacing?  IE  UsernamePASS or Username PASS?

Help please?

E-man
That whole section is just the path to the folder he is mounting the filesystem on, no password.

---

### Post by moderndrummer on 2007-10-02
Thanx for the info guys, it seems that ext2fs works great with osx. I managed to mount my ubuntu partition. still I can't write on it since the comand i used is -rdonly. I would like to ask: is it safe to mount it as writable? is there danger to lose data? does anyone know?

What's more, i ll try to change my mac username this afternoon with netinfo manager, see what comes along.. I'll be posting my progress..
Thanx everyone :)

---

### Post by cyberdork33 on 2007-10-02
> **moderndrummer said:**
> Thanx for the info guys, it seems that ext2fs works great with osx. I managed to mount my ubuntu partition. still I can't write on it since the comand i used is -rdonly. I would like to ask: is it safe to mount it as writable? is there danger to lose data? does anyone know?

What's more, i ll try to change my mac username this afternoon with netinfo manager, see what comes along.. I'll be posting my progress..
Thanx everyone :)

It is not the username that matters, it is the UID.

---


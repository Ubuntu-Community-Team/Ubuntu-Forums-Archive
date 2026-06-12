---
title: "Writing to external drive?"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by mario8723 on 2007-02-26
I use an external USB Western Digital hard drive (MyBook). Ubuntu has no problem recognizing it (THANK GOODNESS) but I can only read from it.

How do I make it so that I can write to it as well?

---

### Post by igknighted on 2007-02-26
If it is formatted in ntfs you will need to install the ntfs-3g driver.  It should be available in the repo's.  Also, check the mount options.  If it is mounted with the option "ro" change it to "rw".

---

### Post by mario8723 on 2007-02-26
It is NTFS...

---

### Post by mario8723 on 2007-02-26
How do I check the mount options?

---

### Post by moore.bryan on 2007-02-26
[I]what's your fstab file look like?
```
cat /etc/fstab
```
[/I]

---

### Post by mario8723 on 2007-02-26
At work right now, will post when I get home. Thanks to all for the quick responses! This community is why I will never switch to another distro!!

---

### Post by TheMono on 2007-02-26
Because it is an external drive, you don't really want it in your fstab. You need to install ntfs-3g, and also get a patched pmount so that Gnome will know to mount it rewritable - see [http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970) for the easy way!

---

### Post by moore.bryan on 2007-02-26
> **TheMono said:**
> Because it is an external drive, you don't really want it in your fstab. You need to install ntfs-3g, and also get a patched pmount so that Gnome will know to mount it rewritable - see [http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970) for the easy way!
*usually good advice, but that didn't work for me... since i never unplug my external hd, i set it up in fstab and it took care of all my issues...*

---

### Post by mario8723 on 2007-02-26
I don't unplug my external either. Which is the better way to go about this?

---

### Post by mario8723 on 2007-02-27
Okay, I followed the directions located here: [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

However, I still can't write to my drive. I'm sure I did something wrong, I just don't know what...

My /etc/fstab looks like this:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1 -- converted during upgrade to edgy
UUID=fa9d920d-3bc0-42cd-aa51-cf32c14ed138 / ext3 defaults,errors=remount-ro 0 1
# /dev/hdc5 -- converted during upgrade to edgy
UUID=be7b7a1b-004d-4987-90ec-58647a0b0020 none swap sw 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/sda1    /media/windows    ntfs-3g    defaults,locale=en_US.utf8    0    0

I upgraded my fuse module following the directions in the README.Debian file mentioned after installation of ntfs - 3g.

mario8723@mario8723-desktop:~$ sudo fdisk -l | grep NTFS
Password:
/dev/sda1               1       19457   156288321    7  HPFS/NTFS

Where did I go wrong, or what else do I have to do?

---

### Post by antoz on 2007-02-27
You could format your external drive to FAT 32 then both Windows and Linux will be able to read & write to it. Cheers,A

---

### Post by mario8723 on 2007-02-27
Can't...tons of stuff on there already. If it were a new drive, I would agree...

---

### Post by moore.bryan on 2007-02-27
> **mario8723 said:**
> #/dev/sda1    /media/windows    ntfs-3g    defaults,locale=en_US.utf8    0    0
*this is where i ran into problems... i can't seem to use "defaults;" instead, specify the arguments "auto,user,exec,rw,sync" in place of defaults.*

---

### Post by stalker145 on 2007-02-27
> **antoz said:**
> You could format your external drive to FAT 32 then both Windows and Linux will be able to read & write to it. Cheers,A

> **mario8723 said:**
> Can't...tons of stuff on there already. If it were a new drive, I would agree...

Is it so much that you can't simply copy the items from the drive somewhere else (like your local disk) and format it? I had to do that when I originally moved to Linux last year and I had a few hundred gigs of trash. It may take some planning if you have some space available... just a thought.

---

### Post by igknighted on 2007-02-27
Avoid FAT32 like the plague, it corrupts easily and has file size limitations (if you were to ever back up a DVD to that drive for example).  If you DO reformat, go with ext3.  If you don't, ntfs should work right fine.

---

### Post by kpkeerthi on 2007-02-27
```

My /etc/fstab looks like this:
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hdc1 -- converted during upgrade to edgy
UUID=fa9d920d-3bc0-42cd-aa51-cf32c14ed138 / ext3 defaults,errors=remount-ro 0 1
# /dev/hdc5 -- converted during upgrade to edgy
UUID=be7b7a1b-004d-4987-90ec-58647a0b0020 none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0
**[COLOR="Red"]#/dev/sda1 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0[/COLOR]**

```

Mario,
Why is your last line in fstab commented out? Thats the line to mount your external drive. right?

---

### Post by mario8723 on 2007-02-27
yes, that is my external...

---

### Post by igknighted on 2007-02-27
if you remove the # sign from in front of it then it should work.

---

### Post by mario8723 on 2007-02-27
Okay, so I uncommented Line 10 and my /etc/fstab now looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1 -- converted during upgrade to edgy
UUID=fa9d920d-3bc0-42cd-aa51-cf32c14ed138 / ext3 defaults,errors=remount-ro 0 1
# /dev/hdc5 -- converted during upgrade to edgy
UUID=be7b7a1b-004d-4987-90ec-58647a0b0020 none swap sw 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1    /media/My Book    ntfs-3g    auto,user,exec,rw,sync,locale=en_US.utf8    0    0

I changed 'windows' to 'My Book' since that is how it displays. Anyway, now when I go to mount it or open the files I get:

[mntent]: line 10 in /etc/fstab is bad

mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

What gives? Any assistance is greatly appreciated.

---

### Post by kpkeerthi on 2007-02-27
Spaces!!! Change 'My Book' to 'My\ Book'. Better yet ged rid of the spaces and have something like MyBook.

---

### Post by MozartlovesUbun2 on 2007-08-27
Hi
I'm new to Linux and Ubuntu, been a windows user and it feels great to finally have rid myself of that trash OS. Feisty Fawn is running smoothly and the compiz/beryl eyecandy is stunning. Now as with all ex window users all my USB external drives are in NTFS, getting the read/write ability with Automatix was easy, but now here is my problem the drives I plug in are recognized but I have no write permission, Feisty really should have a right-click option inbuilt for this, well I need something with a gui which  allows me to change and set the permissions as I need, the command line usage is still new and daunting to me, also the family members in the house would appreciate that.
thanks

ooops now I screwed it up a bit by right-clicking the desktop icon and changing the "ro" into "rw" and now it won't even mount the USB external disc! throws up this message:

--------------------------
Cannot mount volume
invalid mount option when attempting to mount the volume "Music"
--------------------------

Help please

---


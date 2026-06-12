---
title: "Installation and multiple hard disks?"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by Huesos on 2007-03-21
So the live-cd finally works, the solution given to me by someone in the Ubuntu forum helped and pretty soon it's installation time.

But I have kind of a stupid question first. I have several disks in my hard drive. When the installer automatically makes partitions for Ubuntu, will they all be included? In other words, will I have quick and easy access to the content of those disks as well? Because when running the system from the live-cd I couldn't seem to find them in the file system. I am currently a windows user who is used to be able to just click on "my computer" and access them from there so help me out, please.

---

### Post by oilchangeguy on 2007-03-21
first let's get a clarification. do you have multiple hard drives in your computer? or multiple partitions on a single hard drive? because you say you have several disks in your hard drive, and that doesn't make any sense.

---

### Post by Huesos on 2007-03-21
I have multiple hard drives, sorry about that. :)

---

### Post by Falados on 2007-03-21
During the Live CD installation, there is a drop-down menu to select different hard disks and format/install on those.  I believe the automatic install only considers the first one (or the one that It presents to you when it says 'Automatically Wipe and Install on /dev/hda' or something to that effect. )

In essence, if you want to use the other disks, they must be mounted (And can be mounted after installation too).  If you want to use the other disks for ubuntu installation, you must do a manual partition scheme.

---

### Post by Huesos on 2007-03-21
> **Falados said:**
> During the Live CD installation, there is a drop-down menu to select different hard disks and format/install on those.  I believe the automatic install only considers the first one (or the one that It presents to you when it says 'Automatically Wipe and Install on /dev/hda' or something to that effect. )

In essence, if you want to use the other disks, they must be mounted (And can be mounted after installation too).  If you want to use the other disks for ubuntu installation, you must do a manual partition scheme.

I was afraid of that. I've played around in Gparted and it seams pretty complicated to me. I have 2 hard drives of 80 gb size and one of 180 gb. How would you recomend I partitioned it all?

---

### Post by Falados on 2007-03-21
I usually do something like this:

ROOT (/): Gets around 10-20 Gigs depending on how much software you plan to install.. Sky is the limit with this really.

HOME (/home): Again its own partition so that if you need to install a different distro or upgrade, you can save most of your application settings and documents with little effort

BOOT (/boot): Around 50-100MB :  It has only kernels and initrd in it... if it has anything else beyond grub, it shouldn't be there... its a very minimal partition.. ultimately if you are unsure about it, just leave it out, it'll get dumped into ROOT

SWAP: make it twice the size of your physical RAM, and If you can make use of harddrive parrallelism (try to put it on another disk), otherwise just dump it on the same harddrive as root.

I suppose the ways you can format your installation are endless, but thats usually how it do it (Even when I used other distros)

---

### Post by Akrash on 2007-03-22
> **Falados said:**
> In essence, if you want to use the other disks, they must be mounted (And can be mounted after installation too).  If you want to use the other disks for ubuntu installation, you must do a manual partition scheme.

Hey,

How would I go about doing what you said. I want to mount my other 3 hard drives. I'm a complete noob to ubuntu so details would be GREATLY appreciated.

Thanks

---

### Post by Huesos on 2007-03-22
> **Falados said:**
> I usually do something like this:

ROOT (/): Gets around 10-20 Gigs depending on how much software you plan to install.. Sky is the limit with this really.

HOME (/home): Again its own partition so that if you need to install a different distro or upgrade, you can save most of your application settings and documents with little effort

BOOT (/boot): Around 50-100MB :  It has only kernels and initrd in it... if it has anything else beyond grub, it shouldn't be there... its a very minimal partition.. ultimately if you are unsure about it, just leave it out, it'll get dumped into ROOT

SWAP: make it twice the size of your physical RAM, and If you can make use of harddrive parrallelism (try to put it on another disk), otherwise just dump it on the same harddrive as root.

I suppose the ways you can format your installation are endless, but thats usually how it do it (Even when I used other distros)

See, I'm a complete newb to Ubuntu and partitioning overall. What you just wrote seams very complicated to me. I guess I have to experiment... :/ But it kind of feels like I'm in over my head.

---

### Post by Falados on 2007-03-22
If you feel you would like Ubuntu to do this for you, just make sure you switch to the other drives and format them as a large partition, that way you can still use them for storage and such... It really depends on what purpose you want the other drives to serve.

---

### Post by Huesos on 2007-03-22
O.k, this question is going to be hard to explain but... do all 3 hard drives show up as one big "make partitions"-table, or do I have to configure them one at a time?

---

### Post by confused57 on 2007-03-22
> **Akrash said:**
> Hey,

How would I go about doing what you said. I want to mount my other 3 hard drives. I'm a complete noob to ubuntu so details would be GREATLY appreciated.

Thanks

This link explains mounting different filesystem:

[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

or

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
see the sections "Mount Windows" & "Mount Linux"

---

### Post by Huesos on 2007-03-22
Explain to me how each hard drive should be partitioned? 'Cause I'm not sure I understand it.

I don't want the drives just sitting there doing nothing. The swap partition and rootpartition will fit in the first hard drive and still leave room for more. So can I use the rest of it as well as the other hard drives to make one single home-partition or will it result in 3? Is that even possible? If so, is it practical?

---

### Post by Akrash on 2007-03-22
> **confused57 said:**
> This link explains mounting different filesystem:

[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

or

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
see the sections "Mount Windows" & "Mount Linux"

Thanks You, this really helped and I learned some extra stuff.

---

### Post by confused57 on 2007-03-22
> **Huesos said:**
> Explain to me how each hard drive should be partitioned? 'Cause I'm not sure I understand it.

I don't want the drives just sitting there doing nothing. The swap partition and rootpartition will fit in the first hard drive and still leave room for more. So can I use the rest of it as well as the other hard drives to make one single home-partition or will it result in 3? Is that even possible? If so, is it practical?
You might want to boot the desktop live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
the -l is a small "L"

This will show your current partition tables of your hard drives...you might want to check out the links in my signature for some partitioning & installation advice.
Post the results of the above command & how you might want to partition & use all 3 of your hard drives...it's good to plan things out before you install.  As someone mentioned, there's countless ways of setting your system up and if you have Windows or another OS, we'll need to know to help.

The installer should recognize all of your drives and give you the option of formatting at install, but I'd recommend installing Ubuntu on one drive & using the others for data storage.
You can always install Ubuntu to one disk, partition the other afterwards & create mountpoints, so that you can use them for storage or installing other Linux OSes.

A great partitioner for Linux is the gparted live cd:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)
it's only a 30 mb download & it's free, I use it all the time, with great results

I'd suggest you burn a copy of the Super Grub Disk(500 kb download):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by RealG187 on 2007-04-13
Does ubuntu boot off a slave HD last time I checked it froze, but it did the same thing for Windoze! My PC has da option ro bot from IDE0,IDE1, etc and it starts to boot...

---


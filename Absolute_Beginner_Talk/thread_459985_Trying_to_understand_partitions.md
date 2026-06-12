---
title: "Trying to understand partitions"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by ICUR2Ys on 2007-05-31
I read on these forums where people have two partitions for dual boot.  I also read that it would be a good thing if they would create a third partition.

My computer was running microsoft.  I loaded linux took the default told it to reformat the disks. So now this is what I have.

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        7130    57271693+  83  Linux
/dev/hda2           13577       14593     8169052+   5  Extended
/dev/hda3            7131       10469    26820517+  83  Linux
/dev/hda4   *       10470       13576    24956977+  83  Linux
/dev/hda5           14000       14593     4771273+  82  Linux swap / Solaris
/dev/hda6           13717       13999     2273134+  82  Linux swap / Solaris
/dev/hda7           13577       13716     1124487   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         256     2056288+   7  HPFS/NTFS
/dev/hdb2             257        7644    59344110    7  HPFS/NTFS
/dev/hdb3           10173       14589    35477922+   f  W95 Ext'd (LBA)
/dev/hdb4            7645       10172    20304530+  83  Linux
/dev/hdb5           10173       14589    35477891   83  Linux

Partition table entries are not in disk order

By my way of thinking I count 12 partitions and that is without dual booting.  If linux did this on its own and I have it right that there are 12 partitions what is all this about making 3 partitions?

---

### Post by LaRoza on 2007-05-31
If you were to install Ubuntu to a harddisk with the option to wipe the drive and install, you would have two partitions, one in ext3 and one swap.

Without knowing the history of this drive, or your install options, I can not say what everything on the drives are.

edit- The third partition that is commonly recommended is the /home partition, [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome) has the whys and howtos.

You have two drives listed in the output.

---

### Post by Inxsible on 2007-05-31
> **ICUR2Ys said:**
> I read on these forums where people have two partitions for dual boot.  I also read that it would be a good thing if they would create a third partition.

My computer was running microsoft.  I loaded linux took the default told it to reformat the disks. So now this is what I have.

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        7130    57271693+  83  Linux
/dev/hda2           13577       14593     8169052+   5  Extended
/dev/hda3            7131       10469    26820517+  83  Linux
/dev/hda4   *       10470       13576    24956977+  83  Linux
/dev/hda5           14000       14593     4771273+  82  Linux swap / Solaris
/dev/hda6           13717       13999     2273134+  82  Linux swap / Solaris
/dev/hda7           13577       13716     1124487   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         256     2056288+   7  HPFS/NTFS
/dev/hdb2             257        7644    59344110    7  HPFS/NTFS
/dev/hdb3           10173       14589    35477922+   f  W95 Ext'd (LBA)
/dev/hdb4            7645       10172    20304530+  83  Linux
/dev/hdb5           10173       14589    35477891   83  Linux

Partition table entries are not in disk order

By my way of thinking I count 12 partitions and that is without dual booting.  If linux did this on its own and I have it right that there are 12 partitions what is all this about making 3 partitions?

You have two hard drives in your computer...both of 120 GB each.
/dev/hda4 is where your Linux OS is.
You also created 3 swap drives !!! 
/dev/hda5
/dev/hda6
/dev/hda7

You do not need 3 swap drives on the same disk !

On your slave drive (/dev/hdb)
you have Windows OS on /dev/hdb1

hdb2 is another windows partition in ntfs format
hdb3 is in FAT32 format
hdb4 and hdb5 are again Linux partitions in EXT3 format

Please see this for more info:
[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

---

### Post by aeiah on 2007-05-31
perhaps you can get a clearer idea of what you did by using gparted to get a graphical representation. you dont need all the partitions you have (how did they get there anyway? have you been trying to reinstall and such?)

use gparted either by installing via synaptic if you're on your ubuntu install, or using the ubuntu livecd, or using the gparted livecd

---

### Post by ICUR2Ys on 2007-05-31
I took whatever they install procedure gave me.  It would not have occurred to me to even put 2 swap drives out there.  I did a clean install with edgy and then later I again used a live cd to install feisty.  Maybe it is because of that.  I don't know.  Some of the mystery is starting to go out of all this.  Thanks for the input.

---

### Post by ICUR2Ys on 2007-05-31
I don't know how I got them, I didn't even know I had them until I learned to use fdisk yesterday.  I will locate gparted and try that now.  Thank all.

---

### Post by Inxsible on 2007-05-31
When you installed Feisty, you should have used the same swap drive instead of creating another one.

That being said, I think i saw only 1 Linux drive with a boot flag. Did you install Feisty over Edgy ?

I would say, if you havent done much with it, perform a re-install but this time, make sure you know what partitions you are making !

---

### Post by aeiah on 2007-05-31
gparted will just give you a clearer idea since its graphical. it'll also probably tell you the mountpoints, if there are any, for those strange partitions. the problem probably arose from your installation of feisty next to edgy without setting it up intentionally as dual boot (and also having a hdd with ntfs windows partitions).

if you run gparted / gnome partition editor from a livecd you can delete all the partitions you dont need and reorganise things, create new partitions etc. if you run it from your ubuntu install you'll only be able to delete the partitions that arent mounted.

make sure you dont wipe grub. it'll probably be in your first partition on your linux hdd (hda1)

---

### Post by aeiah on 2007-05-31
id also advice a reinstall if its possible. it'll clean things up quicker than messing around, and you'll have everything exactly how it should be.

on your linux hdd you should probably have 3 partitions:

/root - ext3: 10gb
/home - ext3: remaining GB
swap:  twice your ram

---

### Post by ICUR2Ys on 2007-05-31
I did install feisty over edgy.  I didn't know anything about what partitions were needed so I just took what ever the install gave me I didn't provide any input.

This is what I got back when I ran gparted:

sudo gparted --display
terminate called after throwing an instance of 'Glib::OptionError'
Aborted (core dumped)

Inxsible what do you see that requires a reinstall?

---

### Post by ICUR2Ys on 2007-05-31
Well it seems that you are all telling me that I should do a reinstall.  Well OK as soon as I can get the butterflys to settle down.  I need more information to do this, if I just run the system and let it do its own thing I might end up with 4 swap partitions.  If I try to control the install then I don't know how many partitions to have how large they should be.  I don't even know how many swap partitiions there should be.  I need some detailed help or nothing is going to improve and will probably be worse.  I didn't even know when I posted this that there was a problem.

---

### Post by Inxsible on 2007-05-31
> **ICUR2Ys said:**
> Well it seems that you are all telling me that I should do a reinstall. Well OK as soon as I can get the butterflys to settle down. I need more information to do this, if I just run the system and let it do its own thing I might end up with 4 swap partitions. If I try to control the install then I don't know how many partitions to have how large they should be. I don't even know how many swap partitiions there should be. I need some detailed help or nothing is going to improve and will probably be worse. I didn't even know when I posted this that there was a problem.
 
Wipe your entire /dev/hda and reinstall Feisty over it
 
For more info on using the Gparted check this. It provides a step by step method including screenshots:
 
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
 
You can find GParted on your Live CD. Put in your LiveCD and once you get to the desktop, Go to Systems -- > Administration -- > GParted

---

### Post by Inxsible on 2007-05-31
You only need 1 swap, even if you have multiple distros of Linux running. But dont worry about all that now. Simply follow the link that I gave you in the earlier post.
 
/ (root) ~ 10 GB
/home ~ 20GB
swap ~ 1.5 times your RAM and maxxed at 1GB
 
you can create additional partitions if you like where you will be able to store data.This is how mine is set up
 
160 GB total HDD:
10 GB /
20GB /home
1GB swap
72 GB /shared --- This is where i keep my music and movies
 
My NTFS partitions on the same drive are:
25GB Windows OS (C: )
25GB Windows Data (D: )
 
Since you have an entire drive for Linux, you dont have to worry about Windows which is safe on the other (slave) drive i.e. hdb

---

### Post by Inxsible on 2007-05-31
Of your 120 GB on [COLOR=red]hda [/COLOR][COLOR=black]I would suggest the following:[/COLOR]
 
[COLOR=#000000]/ = 10 GB - EXT3[/COLOR]
[COLOR=#000000]/home = 20 GB - EXT3[/COLOR]
[COLOR=#000000]swap = 1 GB or 1.5 GB - ---[/COLOR]
 
[COLOR=#000000]/data = remaining space - EXT3 --------- you can keep your music here (or anything else you like) and share it with Windows from this drive itself[/COLOR]
[COLOR=#000000](You can use any other name -- if you dont like 'data' :) ....Do not use 'media' as Ubuntu creates a folder of the same name and you dont want to be confused with it)[/COLOR]
 
[COLOR=#000000]DO NOT MAKE ANY CHANGES ON YOUR hdb drive...or you might unwittingly erase your Windows[/COLOR]
 
[COLOR=#000000]Hope that helps ![/COLOR]

---

### Post by aeiah on 2007-05-31
nah dont let it do its own thing, and dont worry it isnt as difficult as i think you assume :)

you can manually edit the partition table, which sounds complex, but it isnt. so if you pop the live cd in and run the partition editor (gparted) you'll be confronted with something like this, but with all your swap files and random partitions
[img]http://gparted.sourceforge.net/screens/gparted_1_big.jpg[/img]

you'd just delete all of them, and start creating the partitions you need (make sure you've got the right hard drive selected though!). what you'd need is a root partition, one swap partition, and a home partition (the home partition isnt necessary but it can be good practice.)

im guessing all your music and media files, documents etc are on your other hard drive somewhere? you can leave that be for now

the sizes of these partitions somewhat depends on your preference. as a rule, and since you arent short of space on that drive, you could allocate something like 12gb to the root partition (where ubuntu will be installed to. often just denoted as a slash / )

your swap partion wants to be twice the size of your ram, as a rule. so if you have 256mb ram, you'd want 512mb swap. this rule stops being useful after 2GB (or probably 1gb of ram actually). i have 2gb of ram and just have a 2gb swap file.

your home partition can take up the rest of the hard drive if you want

once you've done this, you can install ubuntu and elect to manually edit the partition tables when it gives you the option, and select the partitions you just made (as well as selecting the locations for other partitions in your system, like your ntfs partitions on your other hdd).

there are loads of step by step guides for this kinda thing on the forum which should set you straight if you're unclear

---

### Post by Inxsible on 2007-05-31
Yep, there are a million ways to set up your partitions, and it depends on the way you prefer it. Set it up according to what I have or what aeiah suggested.
 
Good Luck !

---

### Post by candtalan on 2007-05-31
> **ICUR2Ys said:**
> Well it seems that you are all telling me that I should do a reinstall.  Well OK as soon as I can get the butterflys to settle down. 


If you do not have an immediate actual 'problem' then a reinstall or sort out is only a *theoretical* need, so do not loose sleep over it will you? Things are working ok basically at present there is no panic!

Your partitions are certainly complicated and you would be wise to plan to simplify things, but - no great urgency, it is up to you.

> **ICUR2Ys said:**
> 
 I need more information to do this, if I just run the system and let it do its own thing I might end up with 4 swap partitions.  If I try to control the install then I don't know how many partitions to have how large they should be.  I don't even know how many swap partitiions there should be.  I need some detailed help or nothing is going to improve and will probably be worse.  I didn't even know when I posted this that there was a problem.

The *only* problem is that you now think you have a problem! Relax!

Your linux is mostly on the first hard drive hda, your windows is on the second, hdb. There  is some linux on hdb also but you can ignore that for the present time.

If you have your data backed up, (I include the data on the windows drive also, - just in case and good practice anyway), then the simplest approach when you come to action is to tell the installer to take over the complete first hard drive hda. 

This should install simply, and automatically give you only two partitions on hda ( '/' and 'swap'). It should also give a dual boot with windows. (If there is an extra reference to linux [on hdb] at boot time, ignore it, it can be dealt with later)

The whole drive takeover (hda) is the simplest and sort of basic installation. If it was me, this is what I would do. Just be sure that you choose the linux drive hda and leave the windows drive hdb untouched.

A more sophisticated approach would be to: yourself add and configure a third partition (I call mine 'data' or similar, mounted in the file system at /media/data) and use it in linux but it is set aside from the system installation, and so it can remain unaffected during any future re- installation. 

Even greater elegance can be had by making the /home directory as a separate actual partition. Such sophistcated approaches need you to do a manual install (using the live CD options). Not very difficult, but it needs some care and also a little experience helps too. I do all of my installs using the manual thing, since they are mostly at least dual boot with various partitions here and there. It can get to be quite good 'fun' after a while.

hth
good luck

---

### Post by ICUR2Ys on 2007-06-01
I did the install and I have been updating and installing the many programs that I had before the install.  The system is much neater now.  I now have 4 partitions:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1337    10739421   83  Linux
/dev/hda2            1338        4012    21486937+  83  Linux
/dev/hda3            4013        4208     1574370   82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14593   117218241   83  Linux
dace@dace-desktop:~$ 

I learned quite a bit about setting up the system properly.  Since I had to do it manually.

Since I think my system will probably be more solid.  Since there is a reason for each partition and an appropriate size assigned to the partitions.  I appreciate everyones help and explanations .  Thank you very much.

---


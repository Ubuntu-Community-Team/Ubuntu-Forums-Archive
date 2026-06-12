---
title: "Help me with partitioning..."
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by geezas on 2006-12-15
Ok, so I'm new to this Ubuntu/Linux thing...
I finally installed it and launced Ubuntu from the HDD.
I have no clue how to partition my hard drive like I want to.
Here is what I have now..
I go to "System" >> "Administration" >> "Disks"

> _Partition List:_
Partition 5
Swap Partition
Partition 3
Partition 2

**Partition (5) Properties**
Device: /dev/hda5
Filesystem: Unformatted                        {Format}
Access Path: none                                 {Change}
Size: 17.33 GiB (Free space not available)
Status: Inaccessible                              {Enable} {[COLOR="Silver"]Browse[/COLOR]}

**Swap Partition**
Device: /dev/hda6
Filesystem: Memory Swap                     {[COLOR="silver"]Format[/COLOR]}
Size: 133.32 MiB

**Partition (3) Properties**
Device: /dev/hda3
Filesystem: Extended 3                         {[COLOR="silver"]Format[/COLOR]}
Access Path: /                                      {Change}
Size: 2.07 GiB (203.89 MiB Free)
Status: Accessible                                {Disable} {Browse}

**Partition (2) Properties**
Device: /dev/hda2
Filesystem: Windows NTFS                    {[COLOR="silver"]Format[/COLOR]}
Access Path: /tmp/disks-conf-hda2        {Change}
Size: 55.02 GiB (16.39 GiB Free)
Status: Accessible                                {Disable} {Browse}

**So...**
I want my HDD to have two partitions, one for Ubuntu OS (and swap), and another one for all my files.  I dont have windows on the HDD.  That 55 gig ntfs partition has music, videos, pics and other files that I would like to keep.  Is it possible to reformat that partition so its accessible by ubuntu and keep the files in it?
Let's say i want 20 Gigs for Ubuntu, 2 gigs for swap, and the rest for the big partition.
**Can someone please tell me what do I need to do?  I'm new to Ubuntu so step by step would be nice, cause I don't know what 'access path' is, nor do I know what '/dev/hda' means.**

Please help me, or ask me further questions, I will be checking this post every minute... I want to set up my ubuntu and figure out how things work....

---

### Post by bulldog on 2006-12-15
You're booting from hard disk...........why should you partition after the install :D


/offtopic,
Hi friend bodhi.:-)

---

### Post by bodhi.zazen on 2006-12-15
[Psychocats Install guide](http://www.psychocats.net/ubuntu/installing)

[Basic partitioning](http://www.ubuntuforums.org/showthread.php?&t=282018)

You should not need to make your swap larger then 1 Gb.

---

### Post by geezas on 2006-12-15
...oh, and when I press browse on the ntfs partition, i get a window saying:

"**The Folder contents could not be displayed.**

You do not have the permissions necessary to
view the contents of "disks-conf-hda2."

then when I press ok, right click with the mouse and choose properties, then click on permissions tab, I see:

File owner: root
File group: root

and in the bottom it says: You are not the owner, so you can't change these permissions

---

### Post by geezas on 2006-12-15
> You're booting from hard disk...........why should you partition after the install 

I was trying to do it before the install but could not work things out...

---

### Post by wpshooter on 2006-12-15
Knowing how to setup your partitions is infomation that you should have had BEFORE you installed Ubuntu !!!

What I would do first is figure out how to save that music, videos, pics and other files to some other media, so that you can get it back on your hard drive for use with Ubuntu after you get the Ubuntu O/S installed.

**After** doing the above backup step, I would get the **KILLDISK** program and **WIPE** the hard drive of the computer completely clean.

[http://www.killdisk.com/](http://www.killdisk.com/)

After that is done you can boot back to your DESKTOP CD version of Ubuntu and make sure that you check the integrity of your CD by running the verification test function found on the initial Ubuntu boot screen menu.

If that passes, then reboot again and run the memtest function.

If that passes, then reboot again and let the DESKTOP (live CD) get up to the Desktop and click on the installer icon to start the installation.

Might want to consider partitioning your drive as follows:

/ - for root - ext3 - filesystem type
/home - for home directory - ext3 filesystem type
/linux swap - for Ubuntu linux swap partition - linux swap type
/storage - for storage of data files, music, etc. - fat32 partition type

Good luck.

---

### Post by geezas on 2006-12-15
Thanks for the last post....

How can I save the files?  I can't access them through ubuntu...  There is no other OS.  How can I burn a dvd - lets say - with my files when ubuntu cant access ntfs?

and why you said fat32 for storage?  why not the ext3 like for ubuntu?
and whats the home partition for?

---

### Post by bodhi.zazen on 2006-12-15
wpshooter: That seems a little drastic, no ? Wipe the HD Ha....

You are going to scare poor geezas. At least you scare me :( :lol:

geezas: You can easily resize your partitions with gparted.

Take a look at the partitioning guide.

If you are up and running, perhaps there is no real need to do any further partitioning. Yea it is not optimal, but ask yourself is it worth the hassle?

If so, post the output of:```
sudo fdisk -l
```

This will list all your partitions. Then what size do you want to make them ?

You can move and resize them easily with Gparted, no worries.

To enable the ntfs you need to modify fstab.

```
gksudo gedit /etc/fstab
```

Post the contents. Likely all you need to do is add the option umask=222 in the 4th column....

If you want read-write access to the ntfs I would advise [ntfs-3g](http://doc.gwos.org/index.php/Mount_NTFS_volumes_with_write_support=).

As an alternate, make a large ext3 partition and migrate your music....

I can help or Bulldog is also quite helpful :) I will be in and out but will check on you :)

BEFORE YOU DO ANYTHING READ READ READ

You are in this predicament because you did not do a little reading before hand :)

---

### Post by geezas on 2006-12-15
bodhi.zazen, your words sound more optimistic ;]

> geezas: You can easily resize your partitions with gparted.

Where is GParted? How do I access it?

> If so, post the output of:
Code:
sudo fdisk -l
Where do I write this code?

---

### Post by bodhi.zazen on 2006-12-15
You need to post commands in a terminal.

You will find your terminal in the Gnome menu. This calls up a window in which you can enter commands.

Gparted is a program, you used it to partition when you installed Ubuntu. You should manage your partitions from a live CD.

Gparted also comes as a live CD and is light weight and efficient so we will manage your partitions either from the ubutnu desktop CD (from which you installed) or the GParted Cd.

GParted:

	Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

	Download: [Download Gparted](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

I resize partitions all the time and although we may need to move some data there is no need to wipe you HD, IMO at least :)

---

### Post by wpshooter on 2006-12-15
Bodhi:

No I don't think it is drastic, he can probably get all that done and have forgotten about it before he even begins to figure out your instructionis.  I don't think he is ready for your method yet and my instructions will get him a good solid/stable installation with the properly laid out paritions to save him from possible future problems. 

But of course, that is his decision.

Thanks.

---

### Post by bodhi.zazen on 2006-12-15
> **wpshooter said:**
> Bodhi:

No I don't think it is drastic, he can probably get all that done and have forgotten about it before he even begins to figure out your instructionis.  I don't think he is ready for your method yet and my instructions will get him a good solid/stable installation with the properly laid out paritions to save him from possible future problems. 

But of course, that is his decision.

Thanks.

Bah Humbug :)

Wipe a HD, burn and reload music, re-install all in less time to resize a few partitions and edit fstab,

NO WAY :---)

And your solution is no more (or less) stable, with the possible exception of ntfs-3g

---

### Post by geezas on 2006-12-15
Ok, I found the terminal (didnt expect to find it in applications > accesories, I was looking in System > administration)

I typed:
  sudo fdisk -|
and noting hapened, so I typed
  sudo fdisk
I got this:
  Password:Password:

and nothing appeared on the screen when i typed,,, so i pressed enter, typed first couple letter of the password and got:
  taSorry, try again

I tried couple more times and it said:
  sudo: 3 incorrect password attempts

What now?

---

### Post by bodhi.zazen on 2006-12-15
LOL :lol:

When it asks for your password type your log-in password.

You will not see text in the terminal as you type (your password) :)

---

### Post by geezas on 2006-12-15
aahh... it could've showed starts or something,...

.,.and people say that ubuntu is intuitive... ;]


anyway... so i entered this:
  gksudo gedit /etc/fstab

and i got this:

(gedit:10858): GnomeUI-WARNING **: While connecting to session manager: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

And window bellow poper up showing:

# /etc/fstab: static file system information.
#
# <file system> <mount point>  <type> <options> <dump> <pass>
proc                  /proc                proc      defaults     0          0
/dev/hda3         /                       ext3      defaults,errors=remount-ro 0        1
/dev/hda6         none                 swap     sw            0          0
/dev/hdc           /media/cdrom0  udf ,iso9660 user, noauto   0          0


Does it tell you anything?
Why there is hda 3 and 6, instead of 1 and 2?

p.s. I dont need the ntfs partition, i want it to be workable with ubuntu, i just want to keep some files while reformating, not whole 50 gigs, just two or three

---

### Post by bodhi.zazen on 2006-12-15
That is fstab, leave it for now...

I need to see the output of ```
sudo fdisk -l
```

I think you can boot to a live CD, start up GParted, delete your Partition (5) Properties
Device: /dev/hda5 and swap.

Then resize your Partition (3) Properties
Device: /dev/hda3

To all the space except 1 GB for a new swap partition at the end of the drive.

Make a swap partition size = 1 Gb

Exit GParted

Re-boot to Ubuntu (Hard drive)

Re-open fstab and add a line:> /dev/hda2 /media/music ntfs users,umask=222 0 0

Save and close gedit

Now, in a terminal:```
sudo mkdir /media/music
mount /media/music
```

You can move data you need to save to your ubuntu home directory, perhaps under a directory /home/user_name/music

You can then re-format /dev/hda2 to ext3 and mount it as a data partition. Unmount the dirve before you format it !

You need to edit fstab and change to:
```
/dev/hda2 /media/music auto auto,users 0 0
```

Then:```
sudo mount /media/music
sudo chmod 777 /media/muaic
```

I have to go for now, I'll check in later tonight.

This may help: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

---

### Post by geezas on 2006-12-15
Ok, so I launched Ubuntu from the CD again and I am going through installation again so that I could use GParted.
I added commands to delete all partitios except the hda2 (the ntfs one).
Now I have about 20 gigs unalocated.
How do I put 1 gig of swap so that it will be most effective?  I know that swap works faster when it is on the inner part of the disk, but how do I tell the GParted to put it there?

---

### Post by bodhi.zazen on 2006-12-15
> **geezas said:**
> Ok, so I launched Ubuntu from the CD again and I am going through installation again so that I could use GParted.
I added commands to delete all partitios except the hda2 (the ntfs one).
Now I have about 20 gigs unalocated.
How do I put 1 gig of swap so that it will be most effective?  I know that swap works faster when it is on the inner part of the disk, but how do I tell the GParted to put it there?

Just add a partition in the unalocated space, size = 1 Gb..... It will be close to the middle.

---

### Post by Kazna on 2006-12-15
[B]You don't need to reinstall or install to partition or access a HDD. Read this: [http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

[/B]Do this: Go to the last tab on the top toolbar and find **GNOME Parted **after booting from the **Live CD. **Next, click on it and it will let you choose the size, number of partitions, resize, format etc of the HDD. Create **ONE **swap (format) partition, double your RAM (~1GB) and the rest can be ext3 format partitions at any size above 3-4Gb you want.

Click apply and it will do all that for you without installing anything.

---

### Post by geezas on 2006-12-15
O - 5 gigs of free space
X - 5 gigs of hda2 (ntfs)

GParted shows this now, how should I allocate my swap partition?

OOOOXXXXXXXXOOO

so as you can see, I can choose either left or right side for the swap.
which side represents the inner edge? left or right?
Since Im doing this, I want to do it right.
Isn't an actual location of a swap file is important to the performance when swap is used?  I think it is....

And, Zazen, thanks for all the help...

---

### Post by geezas on 2006-12-15
Screw it.... I just made three partitions
hda1 1GB Swap
hda3 15GB Ext3 Root
hda2 60GB Ext3 Data

---

### Post by bodhi.zazen on 2006-12-15
Hey, that looks good.

I posted too fast as I was in a hurry, sorry :(

The location of swap is not so important because, unlike windows, you will not use it so much....

Also, as you found out, you would need to move partitions....

This is not so hard, see the "copy" and "paste" functions at the top of gparted ?

At any rate, no worries but it looks like you did what wpshooter suggested without wiping the HD :)

No worries, look at all that learning :)

At this rate you are going to be one partitioning guru :p

Oh, is there anything else we can do to help ?

---


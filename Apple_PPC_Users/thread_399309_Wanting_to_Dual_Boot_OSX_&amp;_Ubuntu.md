---
title: "Wanting to Dual Boot OSX &amp; Ubuntu"
date: 2007-04-02
forum: Apple PPC Users
---

### Post by notwen on 2007-04-02
I have a 700mhz g3 ibook and am wanting to re-install both osx 10.3 and ubuntu 6.10 on it.  I'm not familiar w/ yaboot and am wanting the easiest dual-boot config(hopefully similar to grub).  I've heard instaling OSX and using diskutil to partition the HD and then install Ubuntu using the largest free space works best and I believe this is the route I'm going to go.  The HD is around 18GB.  Any suggestions would be appreciated.  Thanks in advance. =]

---

### Post by grazie on 2007-04-02
How much space you want for OSX and how much for Linux only you can decide. However, there are a few things to think about first. It is very desirable to share data (both read+write) between OSX and Linux, but the default installations doesn't really cater for this. The easiest solution is to make the OSX partition none journaling so that linux can write to it. Journaling can also be turned on+off  after OSX installation. The big disadvantage is you'll that have no journaling in OSX. You could make an hfs+ (none journaling) data partition and share data on that. If I recall correctly, the OSX disk utility can only make hfs, hfs+, ufs and fat32 partitions. You could also make a seperate ext2 /home or data partition and share data on that, but getting the user id/group and permissions right can be a bit tricky. Also, you need to install an additional ext2 driver on OSX.

If I were you, I'd create the OSX partition and then install linux in the largest free space as you've stated. If it goes well and you want to try something a little more advanced/flexible you can install linux again and select manual partitioning. If you do try the manual partitioning, don't forget a swap and a bootstrap partition. If it doesn't go to plan, just wipe clean the linux partitions and do the largest free space linux install again. gparted is an excellent gui tool for partition maintenance that comes with on Desktop CD, but not the Alternate CD. You need at least 192mb of ram to install from the Desktop CD, but preferably 256mb.

A mistake that many new linux users make is that they always use the whole disk. Use what you need and leave the rest as free space. It's never been easeir to add new partitions. However, if you want to dual boot on an 18G disk, you're probably going to need to use most/all of it from the start.

---

### Post by notwen on 2007-04-02
Brought my laptop to work and am currently installing OSX, i split the HD into 9.6GB(OSX) and 9GB(8gb for linux, 1gb for swap).  How big does the partition for bootstrap have to be at minimum?  As for the shared partition for file sharing betwen the two OSes, I always have a 4gb flash drive to move files from one to the other.  I'll be sure to post once all is complete or if I hit any snags.  Thanks for the advice. =]

---

### Post by ssam on 2007-04-02
when you are running the mac os x dick utility, leave all the space for linux as unallocated. let the ubuntu partitioner worry about how big the partitions it puts in the free space are.

---

### Post by notwen on 2007-04-02
Both OSX and Ubuntu 7.04 are now installed on my 700mhz G3.  Yaboot works just fine.    Thanks for all the advice/info. =]

---

### Post by Lefkows on 2007-04-14
I am interested in doing something similar but on an external Firewire HD. Does dual boot mean that you get a choice at startup as to whether you want to boot OSX or Linux? How does dual boot work?

---

### Post by Auria on 2007-04-14
> **Lefkows said:**
> Does dual boot mean that you get a choice at startup as to whether you want to boot OSX or Linux?

yes exactly

im not sure how to do that on an external drive though

---

### Post by oswaldkelso on 2007-04-17
> **Auria said:**
> yes exactly

im not sure how to do that on an external drive though

I would emagine the easy way is to put osx on the external hard drive (must be firewire). I use an external harddrive and as it has no problems running osx from it.

If ubuntu would see it I dont know but if you hold down the alt key on boot you could choose ubuntu from the mac hd or osx from the external firewire.

---

### Post by bries on 2007-04-25
> **ssam said:**
> when you are running the mac os x dick utility, leave all the space for linux as unallocated. let the ubuntu partitioner worry about how big the partitions it puts in the free space are.

I think this is the best advise one could get when installing Ubuntu onto a iBook for the first time. A lot of advise is given on setting up different partitions yourself, while the Ubuntu installer will do it for you.

---

### Post by jltnol on 2007-04-28
Similar question about dual boot...


I have a 12" Powerbook and just installed OSX again from scratch.  I did partition the drive into two partitions.. one larger HSF+ for OSX and one smaller Unix for Ubuntu.

Now, I'm trying to install Ubuntu on the smaller partition, and am asked to Prepare Disk Space, and have three option:

Guided (use entire disk)    {I'm guessing this is NOT what I want}
Guided (use largest continuous free space)   {Using this option returns an error message:   ....  to small... }

and 

Manual, where I have these options:

hda1 0 MB
free space 124 MB
hda3 29730MB {I'm thinking this is the OSX parititon)
hda4  8MB
hda5 10133MB  {I'm thinking this is the partition I'd like to use for Ubuntu
free space 0MB

I'm just getting started with Linux and for the time being, don't think I need to worry about moving files between the to OS's..  

 I've searched the forums and this thread seems to be the closest to what I'm trying to do, but I'm still in the dark. If I should just start over, that's fine.  I'm very familiar with the Disk Utility in OSX, but am completly in the woods with Ubuntu.

---

### Post by engla on 2007-04-29
jltnol: Boot back up in OS X and check some things.
1) The UFS (Unix thing) filesystem you set up in OS X is not really for ubuntu. You could reformat that partion to free space and use the free space option in the installer later. This is always the easiest way.
2) Other way is also simple: Go back in OS X and write down the exact sizes of your partitions. Use this for identification in the installer later.

Good luck!

---

### Post by jltnol on 2007-04-30
Thanks for your help.

Ok. so if I understand correctly, the UNIX partition I set up is not the right format for ubuntu.  I get it .

Also, if I make this space "free" then the ubuntu install can use it for the install.

Ok
so the ONLY way(or at least the easiest way) seems to be to re-format the drive, and divide it into 2 partitions,  one formatted HSF+ for the OSX install, and the other leave as "free space", which the ubuntu installer will see as "unused" and install there.


I don't see a way to change the UNIX partition to "FREE" under OSX.

I'll keep you posted.

---

### Post by engla on 2007-05-01
There should actually be some utility on the install disk that can edit the partitions and mark it as free, as long as you can identify which is which. However the applications on the alternative install disk (that you are using) are not very easy to use and has a very technical interface. you can try it though, there should be 'parted' (but I haven't tried myself, and perhaps there is an easier alternative)

On the desktop install cd (live cd), there is the GUI tool gParted that should handle partitioning in an easy and overviewable way so you won't be as afraid to do something wrong...

---


---
title: "The horrors of trying to install Ubuntu"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by enterprise1 on 2008-01-19
Had often thought about trying another OS and Linux in the form of Ubuntu sounded a good choice having seen a few good write ups.

As the C drive on my XP machine was fast filling up I decided to go for a Seagate 320Gig usb drive for my additional storage needs and thought this would be an ideal opportunity to install another os on the new drive as I would never consider touching my main c drive for this purpose.

All the info I had found seamed to indicate the installation was quite safe and the software would resize your drive or existing partition to create space for Ubuntu leaving the rest of the disk safe.

Downloaded Ubuntu 7.10 and created CD booted and tried to install, all options appeared to point at a c drive installation so went for manual inst but this did not give resizing options so went ahead anyway as there were no other options, this option destroyed all of my backup data on the new drive and is lost for good.

The next time I thought I would create 3 partitions on the new drive 1 x 20gig which is what is recommended for Ubuntu and 2 x 150gig for storage and back ups.

The installation would not install on the 20 gig partition it wanted to repartition the whole drove again and create another small partition for the swap, all info I had seen said this would be created within the existing partition area?? 

Have tried system rescue and gparted could not get them to do anything constructive or accept commands

Is there a tutorial for the installation that I could use as I have spent over 40hours trying to install and trying to recover destroyed data

Ubuntu sounded a good idea at the time but it has cost me dearly in time and data lost for good 

Any help to install would be appreciated.

---

### Post by HermanAB on 2008-01-19
Hmm, one BIG problem with Ubuntu is the dreadful install wizard.  Ubuntu doesn't play nice in groups - it needs a chaperone.  One can install it in a dual boot system, but it needs careful work.  You should change distros to Mandriva or its step-child PLCOS.  Mandriva has a proper install wizard that really works well and that won't destroy pre-existing installs like  Windows.

Many a sys-admin secretly keeps a Mandriva CD1 in their toolbox only for the  famous DiskDrake wizard...

I can't for the life of me understand by Ubuntu still hasn't got the installer working right.

Cheers,

Herman

---

### Post by bodhi.zazen on 2008-01-19
Yea, installing an OS is a major undertaking.

A few suggestions.

1.  Here is an install guide : [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

2. gparted must be run on root and the drive/ partition must not be mounted.

3. Here is a link on gparted : [Documentation](http://gparted.sourceforge.net/documentation.php)

4. And here is a link in basic partitioning : [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by Thund3rstruck on 2008-01-20
> **enterprise1 said:**
> 
Downloaded Ubuntu 7.10 and created CD booted and tried to install, all options appeared to point at a c drive installation so went for manual inst but this did not give resizing options so went ahead anyway as there were no other options, this option destroyed all of my backup data on the new drive and is lost for good.


Wow. Yea, playing with the partition structure is NEVER safe and if you read guides that suggested otherwise then they're mis-informed. After performing the necessary backups of your data only then should you consider such an undertaking, 

However, during the install that was pointing to your C:\ disk it was actually asking you if it was ok to resize the existing partition and use the free space to install Ubuntu (Dual Boot). There is a slide bar where you can increase or decrease the partition size. 

Of course you want to avoid the option "Use entire disk".

---

### Post by bwtranch on 2008-01-20
Seems like your a pretty intelligent person  and I'm sure you have made a backup of all your valuable data, right? Best thing to do when you are trying a new OS is to go down to your favorite store and buy a computer. They don't cost very much, but, they last a long while. Won't you please tell the man I didn't do any harm, I'm just tryin' to have me some fun, well done.

---

### Post by jhetrick62 on 2008-01-20
I always set the new partitions that I need up ahead of time with gparted off of knoppix or the Live cd, and then use the manual mode to set the disk space up and it is easy to designate the "entire partition" this way and you have no chance of that happening.

---

### Post by jeffus_il on 2008-01-20
Were you expecting Ubuntu to resize your windows partition during an install?
I have five Ubuntu machine in my home, each with different hardware and some different versions of Ubuntu, I have never destroyed anything or lost data. I wonder if you would expect windows to resize Linux partitions during an install? You should have posted before you tried what you did and you would have got advice as to the best and safest way to go about what you had to do.

---

### Post by zipperback on 2008-01-20
Trying to get a dual boot system up and running can be sometimes quite problematic.

Try this link for help with getting it setup properly.

[http://ubuntuforums.org/showthread.php?t=642627#6](http://ubuntuforums.org/showthread.php?t=642627#6)

- zipperback
:popcorn:

---

### Post by Styln on 2008-01-20
I installed Ubuntu 7.04 on an IBM Laptop in dual boot mode. But before I did the installation I backed up all my data. After cleaning up all unused/needed files I checked the HD from errors and defragged the volume. Finding no erros I installed Acronis Disk Director and resized my existing single volume/partition to support dual booting into separate partitions: one for  Windows and one for Ubuntu. Then I installed Ubuntu into the newly created empty partition. This worked perfectly for me and should work for you as well. It's the simplest way to go as, but it doesn't support file sharing.

Measure twice, cut once,

Styln

---

### Post by frup on 2008-01-20
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

[IMG]http://img379.imageshack.us/img379/4594/feistydual07vo7.png[/IMG]

See the use entire disc option how it has 2 options? your partitions or at least the new drive should show up there. Maybe select the entire 320GB drive and then partition the rest of it afterwards?


Otherwise select manual and just choose the partition you want as /

/dev/ means device
hda means drive 1. hda1 is partition 1 on hda. hda2 is partition 2
hdb means drive 2 etc.

it may be sd instead of hd, to be safe don't have an ipod or something plugged in at the same time :D

---

### Post by cjm5229 on 2008-01-20
On your live CD in System>Administration you will find "Partition Editor" That Is Gparted. If you Partition your drive with that before you install, it will work a lot better.  Also, you should set up at least three partitions for Ubuntu, Root, Swap, and Home. That way you will have all your files in Home seperate nad if you should have to reinstall your OS you can just install the root portion and not lose your files. If Windows used a file system like Linux does you could partition a Windows system with out losing Data a lot easier, But Windows throws data all over the HDD so that if you don't defragment the HDD first you will lose files. That said if you are new to Ubuntu and just want to try it out with out screwing up Windows anymore than Microsoft has already, I would suggest using Wubi. You can just install it into Windows and do not need to repartition If you don't like it, you just uninstall it like you would any other program. Just create the file that it installs in on your USB HDD. I don't think Wubi is working yet with 7.10 but you can still use 7.04. Then when you decide to Dualboot just remember to set up your Partitions first and install Ubuntu into the partitions. 
"Disclaimer" I don't use Wubi myself because that would require me to have Windows installed, and the only place I will install Windows is in a Virtual Machine, The other computers in the house are all dualbooted with XP or Vista, but the only time I do anything on those is when someone messes up Windows and I have to fix it.
Good Luck, Keep Trying, And Read the forums, it is worth the effort..
Carl

---

### Post by sailor2001 on 2008-01-20
for dual booting, I've noticed advice here that seems quite appropriate.. Use windows as your partioning device first.  Rt. click 'my computer' 'manage' and I believe it's drives or something and then resize your windows to leave an 'unallocated partition' where you would then install ubuntu.....no data lost that way

---

### Post by The Cog on 2008-01-20
There are possibly two issues here.

Firstly, enterprose1 wanted to install Ubuntu on an external USB disk. I don't know if that's even possible to be honest. It's not the standard way to install any OS, and may have had an effect of complicating things. 

Second, Ubuntu cannot install onto NTFS partitions. It MUST be on a proper Linux compatible filesystem and ext3 is the default. He doesn't say, but if he filled the disk with NTFS partitions, this will be why the installer didn't offer to install onto any of them.

---

### Post by philinux on 2008-01-20
Its possible but wont it be very slooow?

---

### Post by billgoldberg on 2008-01-20
Should have done some research first.

I always rezise first with gparted and then install, when I want to dual boot. Then it's as easy as selecting the partition you want it installed on.

---


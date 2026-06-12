---
title: "Adding Kubuntu 6.06 x86 to a 64-bit system"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by The Iron Curtain on 2007-02-13
Hi,
I have been using Ubuntu (x86, 6.06) on a laptop since last November. January, I built a desktop and installed Ubuntu 6.10 for the AMD64. I've run into some problems getting things to work on the 64-bit architechture (multimedia codecs to start off), and I don't notice a huge diference between the two (I'm not using any programs that take advantage of all the CPU's bells and whistles.). I figure that I might as well be able to use all of the .debs and .rpms that are compiled for x86 (yes, I know I can force the arch, and there solutions exist, but I'm a newbie and I don't want to mess with that right now).

Thus, I have decided to put in a new installation of Kubuntu (I also want to try out the KDE) 6.06 for x86.

When installing Ubuntu for the first time, I made 3 partitions: ~40 GB for / (root), ~140 GB for /home, and some for swap. I want to resize the 40GB partition to 2 ~20GB partitions that will hold the roots for both versions of K/Ubuntu. I want to still use all of my files from the /home partition. 

Is this possible?

I have an AMD Athlon 64 3400 (or 3200, I forget which) and a single 200GB HDD with 512MB RAM.

As far as I recall, I have to use a LiveCD because my HDD has to be unmounted. I'm not sure where to go from there...

Thank you all!

---

### Post by DerArzt on 2007-02-13
from the live cd you should be able to adjust partitions by going to a terminal and typing [HTML]sudo gparted[/HTML]
there you can graphically adjust partitions, make new ones, and delete them. You will however, have to fix your grub loader files. I would highly recommend looking that up before you try anything.

---

### Post by sardion on 2007-02-13
It is possible, certainly.  The utilities you need to use are ext2resize (to resize the partition without erasing it) and then the standard partitioning tools.  This is not an easy task unfortunately.

You will need to install ext2resize to your working ubuntu install (its in the repos).  Then boot off a live cd.  Then, while running on the livecd, mount the existing drive and copy the ext2resize binary to the livecd's fake home partition.  then unmount the drive and do the resizing.

Ext2resize is a pain in the ***.  I *strongly* suggest reading up on it a lot before using it since you are likely to hose your system if you don't know what you are doing.

Plan B: much easier: boot from the livecd and erase your / (root) partition using the partitioning tool on the livecd (just start installing).  Then make 2 new partitions and install into one of them.  Then boot of the kubuntu cd and install into the other.  Only issue here is you lose your / partition (but /home will be ok).  Just make sure that in the installer's partitioning you specify to mount the /dev/hdaXX for home as /home.

---

### Post by The Iron Curtain on 2007-02-13
Okay...I heard gparted was prety intuitive (I even installed it just to check out the controls)

I want to keep my existing Ubuntu 6.10 AMD64

I'll read up on GRUB loader files

I wanted to know how my file permissions translate over for my /home user files. I will be using the same username on the new Kubuntu 6.06. Will I be able to acess, read, write to my old /home user folder? I want to avoid making a back-up JUST to copy it elsewhere on the HDD.

---

### Post by sardion on 2007-02-13
So long as the username and id are the same everything will work fine.

Just make sure that you name the default user that (k)ubuntu creates the same thing and you will have no problems.

---

### Post by euler_fan on 2007-02-13
I triple boot windows, ubuntu 6.10 32-bit and ubuntu 6.10 64-bit. What I did, backwards of you but it should work, is I installed the other OS's, putting all my "free space" that I was going to turn into the 32-bit partition into one of my other two partitions, but you don't have this problem

Then, I inserted the live CD and used GParted from the LiveCD (worked great) and told it to make a new primary partition for the 32-bit system and a spare swap partition (just to make sure everything worked for both). I told it to go, and the did a graphical install, selecting to manually edit the partition table, and then clicking past that and selecting my newest primary partition to do the install on.

It worked like a charm.

Of course, I did it after backing everything up (not a clean install).

One thing I suggest if you haven't done this already is to make seperate partitions for /home and your OS. I don't know the specifics, but apparently if you want to re-install your OS, you don't have to back everything up. I would anyway, though . . . :)

---

### Post by The Iron Curtain on 2007-02-14
> **sardion said:**
> So long as the username and id are the same everything will work fine.

Just make sure that you name the default user that (k)ubuntu creates the same thing and you will have no problems.

Okay. I'm glad that works


> **euler_fan said:**
> I triple boot windows, ubuntu 6.10 32-bit and ubuntu 6.10 64-bit. What I did, backwards of you but it should work, is I installed the other OS's, putting all my "free space" that I was going to turn into the 32-bit partition into one of my other two partitions, but you don't have this problem

Then, I inserted the live CD and used GParted from the LiveCD (worked great) and told it to make a new primary partition for the 32-bit system and a spare swap partition (just to make sure everything worked for both). I told it to go, and the did a graphical install, selecting to manually edit the partition table, and then clicking past that and selecting my newest primary partition to do the install on.

It worked like a charm.

Of course, I did it after backing everything up (not a clean install).

One thing I suggest if you haven't done this already is to make seperate partitions for /home and your OS. I don't know the specifics, but apparently if you want to re-install your OS, you don't have to back everything up. I would anyway, though . . . :)

Thank you! I do have a seperate partition from my OS and home, so that should be no problem. Glad some one else who knows more than me did this before

Okay, i will read up on GRUB boot loaders

---

### Post by euler_fan on 2007-02-14
One final detail . . . my GRUB noticed my three OS's just fine, but as I update my 386 kernel, it progressively pushes the others off the boot loader option. I don't like this and have not gone through the effort of learning to get rid of the old kernels from the GRUB boot menu. This is slightly bothersome, but until I do another kernel update, I don't think I will be too worried (the others still start fine).

I heard doing a kernel update is supposed to clean this all up automatically, but mine did not . . . hmmm . . .

---

### Post by The Iron Curtain on 2007-02-14
I backed up my important files, I burned the Kubuntu LiveCD. I'm gonna take the plunge (agani). See you folks ont eh other side. Thanks again for all of your help :D

---

### Post by The Iron Curtain on 2007-02-15
...And there's an error. The Kubuntu splash page shows and I select the option to install/run it and then it show an Error. Something about MP-BIOS timing and IO-APIC. Any suggestions?

---

### Post by Ptero-4 on 2007-02-15
use noapic nolapic as boot options. Also if you`re not going to keep the 64bit ubuntu, you don`t need to repartition, just install ubuntu 32bits (with whatever DE you want first) and then install the other DE later, the metapackages (the ones ending in -desktop) only vary in the DE specific packages so installing one over the other won`t overwrite anything the other installed first.

---

### Post by The Iron Curtain on 2007-02-15
Thank you! I will try that

---


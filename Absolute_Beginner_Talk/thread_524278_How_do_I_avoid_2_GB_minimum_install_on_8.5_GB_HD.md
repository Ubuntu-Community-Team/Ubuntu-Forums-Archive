---
title: "How do I avoid 2 GB minimum install on 8.5 GB HD?"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by seaworthy4life on 2007-08-12
I had to reinstall since I accidentally maxed out my free space.  Now, every time I try to reinstall, It automatically gives me the 2 GB minimum install.  On my original installs, it used about 5 GB, which is what I was expecting, since this gives me the functionality that I need without having to figure out everything I am missing.  

How do I force it to give me the regular 5 GB install rather than the 2 GB minimum install?  My HD is only 8.5 gigs, but even after following the instructions on the Enable Multimedia sticky, it won't do everything it is supposed to do unless I get it to do the original 5 GB install.  While installing, I instruct it to use the entire hard drive with a 500 MB swap, same as always.

---

### Post by Warren Watts on 2007-08-12
There isn't any data on the drive you still need, right?  if not, have you tried completely removing all the partitions, and letting the Installer re-partition?

It kinda sounds like the installer is trying to squeeze the install into a smaller existing partition.

---

### Post by seaworthy4life on 2007-08-12
Since I am electing to use the entire hard drive, it should be repartitioning the hard drive.  After the installation, I only have two partitions, the swap with 500 mb and the primary, with 2 GB used and 5.4 GB free.

---

### Post by Arthur Archnix on 2007-08-12
What disc are you using to install, live or alternate? If alternate, what are you typing at the install? By 2Gig install do you mean a CLI system only? If so, then do:  
```
sudo aptitude install ubuntu-desktop
```
Otherwise, please write back with a bit more information.

---

### Post by seaworthy4life on 2007-08-12
I am using a Live CD.  I don't know what a CLI system is.  It is just forcing the small installation package for some reason, but then giving me 5 GB of free space afterwards.  I am thinking about reinstalling, this time using the manual partitioner, though I am not sure if that will make any difference.  In this small package, I don't even have a partitioner to inspect the status of everything at the moment.  Working on that right now.

---

### Post by seaworthy4life on 2007-08-12
-edit 

disregard

---

### Post by jenson on 2007-08-13
> **seaworthy4life said:**
> I had to reinstall since I accidentally maxed out my free space.  Now, every time I try to reinstall, It automatically gives me the 2 GB minimum install.  On my original installs, it used about 5 GB, which is what I was expecting, since this gives me the functionality that I need without having to figure out everything I am missing.  

How do I force it to give me the regular 5 GB install rather than the 2 GB minimum install?  My HD is only 8.5 gigs, but even after following the instructions on the Enable Multimedia sticky, it won't do everything it is supposed to do unless I get it to do the original 5 GB install.  While installing, I instruct it to use the entire hard drive with a 500 MB swap, same as always.

Hi seaworthy4life,

Did you use the partitioner that come with the Ubuntu Live CD? First shrink the existing partition and create one ext3 partition follow by a swap?

I have some problem when dual booting, I have to boot into XP partition to defragment it before I boot back my Ubuntu LiveCD to shrink XP partition and create one ext3 and one SWAP partition each. Then I manage to install properly.

Are you using a hard disk that is completely formatted? Or are you using a hard disk that you previously installed with Windows OS, but the data on the HDD only take 2GB now? If so, I think you have to defragment it first before you shrink it down and create two new partitions for Ubuntu installation through LiveCD.

Hmm. I'm not really sure what your actual problem is, if my reply doesn't help you in anyway, please accept my apologies and sorry for wasting your precious time, as I know it's a pain when you can't get your problems solved asap =)  Cheers!

Regards,
Jenson

---

### Post by ramjet_1953 on 2007-08-13
Your hardware really is just on the limits of any OS install that has a GUI.

I have three suggestions:

1. Download the alternate CD, as it is far less memory hungry and often succeeds, where the LiveCD doesn't. OR

2. Download XUbuntu, which is a much lighter install.

3. Download the gparted live CD and use it to format and partition your HDD. Even just blank it completely and allow Ububtu or XUbuntu partition it.

You can get the gparted iso from here:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Just burn the iso image SLOWLY to a CD and then boot from it to partition your HDD.

Regards,
Roger :cool:

---

### Post by Arthur Archnix on 2007-08-13
Ok, well as far as I know installation from the live cd does one thing, and one thing only, installs the whole damn CD. A setup of around 2 gigs sounds about right. I don't think you're doing anything wrong on the install side of things. So at this point you should comment out the cd from the repos, and then update and upgrade your system.
```
sudo gedit /etc/apt/sources.list
```
Comment out the cd sources using #, save and exit.
```
sudo apt-get update
sudo apt-get upgrade
```
Then, if you're missing some functionality or something else feels wrong, let us know what that is.

---

### Post by kozy6871 on 2007-08-13
A CLI stands for 'command line interpreter'.  It is the alternative to a GUI (or Graphic User Interface) system.  You type commands into a CLI and you point-and-click a GUI.

---


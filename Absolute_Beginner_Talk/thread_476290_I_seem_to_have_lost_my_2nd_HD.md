---
title: "I seem to have lost my 2nd HD"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by fast eddie on 2007-06-17
I installed ubuntu onto my old Dell pc last night and now I cant find my 2nd HD.

I have 2 physically separate drives:
1. 250G with os running on it
2. 500G with music files on

I installed ubuntu and followed all the default instructions and let it automatically partition the drives but now it doesn't show my second 500G drive when I look in "Places".

Can some one please tell me how I find this drive or what to do next

Cheers for the help

---

### Post by Gimpy_Rob on 2007-06-17
Hey, no problem, you just need to instruct linux to mount the drive regularly.  First things first, make sure linux sees it.

Please post result of the following at terminal
```
sudo fdisk -l
```

---

### Post by fast eddie on 2007-06-17
Thanks for the quick reply. Here is the output of that command:


Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30017   241111521   83  Linux
/dev/sda2           30018       30394     3028252+   5  Extended
/dev/sda5           30018       30394     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS
graham@MusicServer:~$

---

### Post by Gimpy_Rob on 2007-06-17
Perfect, there's that drive you were worried about.

Now, its in a file system called NTFS, which is fancy for "MS windows new one"
In the past, working with them has been a bit of a pain, but there is a new stable version of the NTFS drivers out there now that works with them just fine.  Give me a min and I'll grab the info on it.

In the meantime, we'll be editing the /etc/fstab file... could you post the result of ```
cat /etc/fstab
```

This just lists your current settings for mounting the filesystems listed above

---

### Post by Dedoimedo on 2007-06-17
Hello,
You have not lost it, it's there - sdb.
It's just not mounted. You'll have to mount it to make it visible.
Do you know how to do that or need help?
Dedoimedo

---

### Post by Gimpy_Rob on 2007-06-17
Unless, of course, this drive is empty and it will never touch a windows machine... In that case, we should format it to a native linux filesystem.

So, is it empty? and will it ever touch a windows machine (other then with a network, I mean, directly hook up to it?)

---

### Post by fast eddie on 2007-06-17
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7223c33d-9da7-454e-8212-7298348f1e74 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=7053e585-8031-4666-a1fc-bdb0d16cbbb8 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by fast eddie on 2007-06-17
I do need help to mount it please - sorry to be clueless but this is my first go at linux and I am a bit confused

It contains all my music but I have a copy on another machine and an external USB hd as well so if we have to format it to a native linux filesystem then it doesnt really matter. I would like to do whatever would be best and the most stable as this is going to be running as my server for my Squeexebox.

Thanks for your help if I havnt already said that

---

### Post by Gimpy_Rob on 2007-06-17
Hey, no problem, I ask questions on this forum as well, everyone should have somebody who's been there.

Ok, I suggest for now mounting it as a windows partition, and leaving it like that for a while.  From what I read, the new version is really nice and should work alright.  If you ever have problems, maybe consider an EXT3 instead.

Now, I havn't done this personally, and I don't have any NTFS drives I use daily... but here's what I've figured. (if you have problems, say so.. I have a windows computer, I'll make an NTFS drive and follow the same steps you are, but for now, try the following)

```
sudo apt-get install ntfs-config
```
this will install the stuff to work with the NTFS systems.

Click Applications &#8594; System Tools &#8594; NTFS Configuration Tool 
 The upcoming tool will detect NTFS partitions on your system. Check each partition you wish to access, and, if you wish to, click the mount directory to change it. When finished, click Apply. 
 On the next screen Enable write support for internal device will be selected by default. Click OK. 
Your NTFS drive will be now be available in the mount point you selected.

(text from [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions))

Tell us how it went

---

### Post by fast eddie on 2007-06-17
Here is the output of that command but I dont think it worked - see last couple of lines

graham@MusicServer:~$ sudo apt-get install ntfs-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  fontconfig-config fuse-utils libatk1.0-0 libc6 libc6-i686 libcairo2
  libdatrie0 libdbus-1-3 libfontconfig1 libfuse2 libglib2.0-0 libntfs-3g0
  libpango1.0-0 libpango1.0-common libpng12-0 libthai-data libthai0 libxml2
  libxrandr2 ntfs-3g
Suggested packages:
  glibc-doc ttf-thryomanes
Recommended packages:
  libatk1.0-data libglib2.0-data
The following NEW packages will be installed:
  fuse-utils libdatrie0 libfuse2 libntfs-3g0 libthai-data libthai0 ntfs-3g
  ntfs-config
The following packages will be upgraded:
  fontconfig-config libatk1.0-0 libc6 libc6-i686 libcairo2 libdbus-1-3
  libfontconfig1 libglib2.0-0 libpango1.0-0 libpango1.0-common libpng12-0
  libxml2 libxrandr2
13 upgraded, 8 newly installed, 0 to remove and 818 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

---

### Post by Gimpy_Rob on 2007-06-17
Umm,  similar to an error I've seen when another program that installs programs is open, like synaptec or adept, is this the case? 

P.S.
Any other gurus that might have a suggestion?

---

### Post by fast eddie on 2007-06-17
Uh oh - I think you may start to get p1ssed off with me now.

I am just doing a distro upgrade download at the moment but I thought I was only downloading the files and they would be installed later - didnt realise that it could interfere with this :redface:

From this then I guess I will have to start this when the upgrade has finished

installed 6.10 but forgot I set the upgrade to 7.04 last night just before going to bed

---

### Post by Gimpy_Rob on 2007-06-17
Heh, raging :P

No, I was proved right, how could I be mad with that?

So, just do that again when the distro upgrade is done...
one thing ubuntu does not like is updating/installing more then one thing at once... This is because of the dependencies and such that linux apps use, and apt keeps track of them all... and if there is more then one thing going on at once, it would lose track.

So, when there is nothing else installing, just try again.  I'm tracking this thread, so post what happens.

---

### Post by Dedoimedo on 2007-06-17
Hello,

First, run only one instance of upgrade / update whatever...

Second, here's about mounting:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Windows](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Windows)

[http://www.dedoimedo.com/computers/linux_commands.html#mounting_drives](http://www.dedoimedo.com/computers/linux_commands.html#mounting_drives)

Dedoimedo

---

### Post by fast eddie on 2007-06-17
I am really sorry I have been kinda wasting your time.

Once the upgrade has completed I will try what you suggest and let you know but it could be a while as I am only on file 300 of 940 and downloading at a rate of 30k. This crap speed is something to do with my dsl line being upgraded and BT have to test the line for 20 days to find the maximum speed the line can support.

Once again, sorry for not telling you that at the start but I didnt realise that ubuntu does not like is updating/installing more then one thing at once:redface:

---

### Post by fast eddie on 2007-06-17
Wey hey - it appears that I have done it :D

All I need to do now is figure out how I can control my new music server from my windows machine. Then I can put it away in the cupboard and run it headless and just add the music files to it remotely  :guitar:

Oh yeah, need to be able to set the wake on lan as well but need to let it go into hibernation before i can test this.

Thanks for all your help - much appreciated

---


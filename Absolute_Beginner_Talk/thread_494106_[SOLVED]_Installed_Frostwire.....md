---
title: "[SOLVED] Installed Frostwire...."
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Mt Dew on 2007-07-06
I've added Frostwire to my programs list but what I have downloaded so far has filled up my home/username file.  What can I do?  I need a really big folder for this.  Thanks for the help in advance!

---

### Post by Raineer on 2007-07-06
Well there has to be an option in Frostwire to change where it downloads to.

That being said, your /home partition should be your largest one as that is where all your media files will go (and anything else you download)

If it's really "filled up" that partition, google "Gparted Live CD" and resize your partitions. Make /home a lot bigger, you probably have too much allocated to / (root) or /boot

---

### Post by Mt Dew on 2007-07-06
But it says I have 5 gigs of hd disk space left.   I've only downloaded 38 songs so far...go figure.  When I change the folder to download to it resumes downloading.
When I installed Ubuntu about 5 days ago, I just let it do it's thing when I installed it.

---

### Post by Raineer on 2007-07-06
Maybe just don't start up any downloads and change the directory.

It will still need to be under /home/you/ to work, maybe /home/you/downloads.

If you have 5 gigs left then you aren't "filled up" so that's nothing really to worry about, it's just about organizing your files to make them cleaner.

---

### Post by UnixAnt on 2007-07-06
Forgive me - but what exactly is giving you cause for concern?

Has /home/$USERNAME really filled up completely, but there is 5gb available overall on the / partition or 5gb of unallocated disk space, etc?

If you open up a terminal and type the following:

$ df -h

It will show you the mounted partitions you have and how much space they are taking up.

I've just downloaded Frostwire to take a look myself, and if you go to Tools...>Options from the menu, the first dialog box you see lets you specify where you would like to save your downloads.  But also bear in mind that whilst the application is in the process of downloading, files will build up in your /home/$USERNAME/Incomplete directory.

---

### Post by Mt Dew on 2007-07-06
Is there an additional program that will help me organize them better?  I'm not really understanding the file structure yet.  I'm afraid to mess something up.  Also when I looked at the disk analyzer it says that my user folder is at 100%.  I don't under stand this at all!

---

### Post by Mt Dew on 2007-07-06
> **UnixAnt said:**
> 
If you open up a terminal and type the following:

$ df -h

It will show you the mounted partitions you have and how much space they are taking up.

.
This what I got when I put that in terminal:

xxxxx@xxxxx-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.0G  3.4G  5.2G  40% /
varrun                252M  120K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb            252M   96K  252M   1% /proc/bus/usb
udev                  252M   96K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   33M  219M  14% /lib/modules/2.6.20-16-generic/volatile

Does this help in any way?

---

### Post by UnixAnt on 2007-07-06
Yes, that helps.

Looking at the output from df, it shows me that there is only one partition - the root partition: /

If you had separate partitions, they would all have their own separate entries, such as:

/dev/sda1 ...... /
/dev/sda2 ...../home
/dev/sda3 ..... /usr/local

and so on.

Just quickly, in case you aren't sure about Linux/Unix partitions, it works like this:

Linux/Unix does not care where a filesystem is mounted.  You could have 1 disk, 20 disks, 15 partitions, etc, etc - all Linux cares about is where they are mounted.  So whereas in Windows each physical drive is assigned a drive letter (C:, E:, H:, etc) the same is not true in Linux.  What happens usually is that you create a number of separate partitions when you first install the OS.  So for instance, you have a 40gb drive to play with, the minimum you could get away with (other than simply having / and a swap partition) would be:

/boot
/
/home
swap

This is fairly typical for a desktop/laptop.  From your df output, it looks like you have simply 2 partitions: 1 for / and swap.  What is happening in your situation is EVERYTHING is mounted underneath /, so anything which fills up outside your /home/$USERNAME directory will affect your overall disk capacity.  One of the usual culprits is the /var filesystem, as this contains log files which are constantly being amended.

My advice: if its at all possible, install Linux again.  But this time, manually partition your hard disk to have multiple mount points.  So for instance, set up a /boot partition of say 100mb to hold Grub and its configuration.  Assign some space to a /home partition, some more to /, add a swap partition, and make / var separate (give it about 2gb).

---

### Post by Mt Dew on 2007-07-06
Yes, I still have the disk.  Do I just insert it or do I have to format the hd first?
What goes into / and /home?  I want  to make sure I give enough space to download these space hogging MP3's.  I just realized they are 5mgs apiece!  I'm used to wma that are about 1/2 that size...And I will have no additional user logins if that makes any difference.

My HD is @ 10gb

Do I need Grub?


Thanks!

---

### Post by UnixAnt on 2007-07-06
GRUB is the GRand Unified Bootloader, and its installed by default by the Ubuntu installer unless you specify otherwise.

GRUB is basically the boot menu you will see when you fire up your machine, and it stores its config files in /boot, which doesn't necessarily need to be on a separate partition by the way - its just something I have done for a long time and am in the habit of doing :)

If 10gb is the maximum size of your disk, then I wouldn't count on downloading too much multimedia from the Internet, but as a simple partitioning scheme I would use the following:

[this assumes Linux will be the only OS to occupy the 10gb capacity]

***CAUTION - This is a DESTRUCTIVE process and will wipe all your data from the disk***

Create the following partitions during installation:

/ (4 gb)
/home (5gb)
swap (between 512mb and 1gb in size)

Now whatever happens to the / mount point, this will not affect what is going on in /home.  The only way /home will increase will be if you install some software which uses /home to store its settings, and also by downloading files from Frostwire, Deluge (torrents), etc, etc

---

### Post by Mt Dew on 2007-07-08
Thanks.  I will use that as a guide for the reinstall of Ubuntu, but........

I have decided to put a 20g hd in and add a 2nd 20g hd.  The 1st hd is empty and I will use this for the  reinstall of Ubuntu.

The 2nd hd I want to use as storage, but it already has some files that I want to keep.  It actually has a copy of windows that I got the BSOD on and was unable to repair.  Can this be done?

Should I start a new thread?

---


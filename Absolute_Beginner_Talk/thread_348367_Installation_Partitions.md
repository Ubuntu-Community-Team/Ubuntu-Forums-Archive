---
title: "Installation Partitions"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Spaaarkz on 2007-01-28
Hello,

First of all, I am a bit of noob, I am comfortable building and maintaining my windows machines, but am not that confident with creating a dual boot machine with Linux. 

I was going to install ubuntu but have gotten a bit scared during the install procedure. According to this guide: [http://psychocats.net/ubuntu/installing]("http://psychocats.net/ubuntu/installing") I should be able to let the install take care of the partitioning of my hard drive. 

However, I do not have the option to "Resize IDE1 master, partition #1 (hda1) and use free space". I only have the option to erase the entire disk or to manually edit the partition table. 

Ultimately, I have one hard disk which has two partitions on it (both of ~40Gb). I want to create a dual boot machine, leaving my windows installation as it is, and to have Ubuntu on the second partition (of which I have 20GB free space I want it to install into). 

I am not confident enough to manually create the partitions as I do not fully understand what I am doing. Does Ubuntu / Linux need 3 or 4 separate partitions to install? I.e. one for the /boot, /swap etc. I tried doing this but got into problems about primary partitions and secondary partitions, so I got scared :(

Is there an easier way for me to do this rather than manually changing the partitions? I do not want to loose windows (at least not yet) but want to try Linux. I am terrified that if I go through with the install it will over-write the windows installation........

If anyone can offer some help, or suggest a good walk through guide to help me out, it would be most appreciated.

Thanks,
Spaaarkz.

---

### Post by bruenig on 2007-01-28
Go into manually edit the partition table. Remember that there are no changes made until you hit apply. Click on the second partition and then select resize. Resize it, then with the unallocated space, right click to create a new partition and make it ext3. From there you should be able to hit apply and move to the mount point part. It should select the mount points for you automatically. But if it doesn't make sure that the new partition's mount point is / which is the ubuntu root partition.

---

### Post by old_geekster on 2007-01-29
> **Spaaarkz said:**
> Hello,

First of all, I am a bit of noob, I am comfortable building and maintaining my windows machines, but am not that confident with creating a dual boot machine with Linux. 

I was going to install ubuntu but have gotten a bit scared during the install procedure. According to this guide: [http://psychocats.net/ubuntu/installing]("http://psychocats.net/ubuntu/installing") I should be able to let the install take care of the partitioning of my hard drive. 

However, I do not have the option to "Resize IDE1 master, partition #1 (hda1) and use free space". I only have the option to erase the entire disk or to manually edit the partition table. 

Ultimately, I have one hard disk which has two partitions on it (both of ~40Gb). I want to create a dual boot machine, leaving my windows installation as it is, and to have Ubuntu on the second partition (of which I have 20GB free space I want it to install into). 

I am not confident enough to manually create the partitions as I do not fully understand what I am doing. Does Ubuntu / Linux need 3 or 4 separate partitions to install? I.e. one for the /boot, /swap etc. I tried doing this but got into problems about primary partitions and secondary partitions, so I got scared :(

Is there an easier way for me to do this rather than manually changing the partitions? I do not want to loose windows (at least not yet) but want to try Linux. I am terrified that if I go through with the install it will over-write the windows installation........

If anyone can offer some help, or suggest a good walk through guide to help me out, it would be most appreciated.

Thanks,
Spaaarkz.
I know exactly how you feel.  I have been using Ubuntu for about a week.  Although I have it on a second drive, Ubuntu still sees my Windows HDD.  I was extremely nervous the first time I made partions.  Like you, I wanted to assure that Windows was not changed.  After some nail biting, I got it done.

The previous post and the guide that you listed, should help you get the job done.

Good luck!

---

### Post by Lord Of The Dance on 2007-01-29
Before you start make sure to backup any important documents, and make sure you have your windows cd. You probably won't need them, but better to be safe.

To run Ubuntu you need an ext3 partition mounted as the root, and should have a linux swap partition (for virtual memory) which is typically 1.5 times your RAM.

I would strongly advise you to mount another ext3 partition as "/home", this is the like WinXP's "documents and settings" folder. If you ever need to reinstall linux or upgrade to the next version, your settings, documents, ect will be preserved.

**Optional:** Linux can't usually write to NTFS file systems. So if you want to share files between Windows and Linux you should do one of the following:

1. Set up a FAT32 partition. These can be read by both Linux and windows.
2. Use removable storage to share files.
3. I believe that [http://www.fs-driver.org/](http://www.fs-driver.org/) offers a driver to allow windows to access ext3 partitions. I've never used it and I'm not sure if it is entirely safe.

I should add that if you need to set up more then four partitions on a single drive, you will need to use an extended partition. These act as containers for more partitions.

Ubuntu automatically installs GRUB boot manager, which should detect any other existing operating systems and prompt you to select one on startup.

---

### Post by housam on 2007-01-29
About partitioning , You only able to create 4 primary partitions on a single HDD. If you need more partitions , you have to convert one of the primary partitions to an extended partition which can be devided to any number of partitions you want.
Please note that partition magic is not the suitable tool for partitioning for ubuntu. use the Gparted to do the job, it is perfect for ntfs and ext3 format.
Do the defrag at least twice before resizing your xp partition and back-up every thing. create all your partitions manually before installing ubuntu, that put every thing under control. here is an example:
Resize the windows poartition to create an unallocated space of about 41Gb ( or what ever you like )
Now devide the unallocated space to two new partitions:
-10 Gb ext3 for the root ( / ) as primary partition
-31 Gb as EXTENDED PARTITION
Devide the extended partition to 2 new logical partitions
-1 Gb swap for the ( swap )
-30 Gb ext3 partition as /home 
After that go for the installation and when it comes to the partition mater , choose the manual way .
__________________

---

### Post by Spaaarkz on 2007-01-29
Thank you all for your replies and help - it really is appreciated.
I will have a go at installing ubuntu when I get a bit of time.
Cheers again,
Spaaarkz.

---

### Post by Bartender on 2007-01-29
I'd like to second housam's comments - [GPLCD]("http://gparted.sourceforge.net/livecd.php") has worked great for several weird partitioning experiments.  Your mileage may vary, but I don't see the point in using Partition Magic.  PM refers to your partitions in Windows-speak, and what's the point in that?  You want to get familiar with Linux terminology (dev/sda1, sda2, etc.)

One additional comment - if you try to build a 4th primary GPLCD will bring up an error message and sit on its hands.  After 3 primaries, build the extended box and start creating logical partitions inside.

---


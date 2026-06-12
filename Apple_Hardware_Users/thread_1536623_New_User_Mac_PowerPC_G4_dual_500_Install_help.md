---
title: "New User Mac PowerPC G4 dual 500 Install help"
date: 2010-07-22
forum: Apple Hardware Users
---

### Post by rrrrob on 2010-07-22
Hello All,

I'm finally attempting my first Linux install and I'm looking for some information.  I have a Mac PowerPC G4 dual 500 MHz with 1GB of RAM and 2 internal hard drives.  My goal is to set it up as a web server for testing and run it without a monitor and keyboard (headless).  I tried ubuntu-10.4-server-powerpc.iso but I had trouble.  It booted off the CD and I hit return to accept the default install.  When I did this the screen flashed bright white and then went to black, after which nothing showed on screen.

I haven't been able to find any information that matches my situation and needs thus I'm asking.

What version of Ubuntu should I be using to accomplish this?

And are there any special instructions?

Thanks for the help
Rob

---

### Post by rrrrob on 2010-07-22
I'm trying ubuntu-6.06.2-server-powerpc.iso

The system has OS 10.4.11 loaded on the first drive and I have done the following.

Formatted second drive as a UNIX File System

Copied the following files to UNIX drive, yaboot, yaboot.conf, ignited.gz, vmlinux

Restarted comp holding down option + command + o + f

at the prompt I typed "boot ide2:3,yaboot"  and pressed return

the screen flashed, went grey, and came back up with a buster symbol (circle with a diagonal line threw it upper left to lower right)

I think I have followed the directions, but I can't find anything about this buster symbol.

---

### Post by rrrrob on 2010-07-25
Ok,

I have searched the forum and read the documentation, yet I am still lost...

I've gotten the installer for Ubuntu 10.04 server to install.  Yea!!!  Amazing how a little bit of progress can wipe away the previous frustration.

I can now boot into the Mac OS 10.4.11  partition if I hold down the option key and choose the appropriate drive.  I can also see the drive with the Linux logo on it. However, when I choose the Linux drive I am getting the following.

*************  From the screen  ****************
First stage Ubuntu bootstrap

Press l for GNU/Linux
      x for Mac OSX
      c for CDROM

Stage 1 Boot:

************************************************


If I type "l" or simply let it continue on its own I see the following


*************  From the screen  ****************
Loading second stage bootstrap…

"little flashing folder icon"

************************************************


After a short period of time the screen flashes to solid white and nothing more happens.

I'm assuming that this is not correct.  I'm not sure what should be happening at this point sense this is my first install.  Can someone please tell me what should be happening at this point? and how I might be able to get there? 


Thanks for the help
Rob

---

### Post by imrazor on 2010-07-25
> **rrrrob said:**
> Ok,

I have searched the forum and read the documentation, yet I am still lost...

I've gotten the installer for Ubuntu 10.04 server to install.  Yea!!!  Amazing how a little bit of progress can wipe away the previous frustration.

I can now boot into the Mac OS 10.4.11  partition if I hold down the option key and choose the appropriate drive.  I can also see the drive with the Linux logo on it. However, when I choose the Linux drive I am getting the following.

*************  From the screen  ****************
First stage Ubuntu bootstrap

Press l for GNU/Linux
      x for Mac OSX
      c for CDROM

Stage 1 Boot:

************************************************


If I type "l" or simply let it continue on its own I see the following


*************  From the screen  ****************
Loading second stage bootstrap…

"little flashing folder icon"

************************************************


After a short period of time the screen flashes to solid white and nothing more happens.

I'm assuming that this is not correct.  I'm not sure what should be happening at this point sense this is my first install.  Can someone please tell me what should be happening at this point? and how I might be able to get there? 


Thanks for the help
Rob

I'm going to take a stab at this, even though I'm not an expert on Ubuntu PPC. The flashing folder is usually an indicator that the Mac can't find a suitable volume to boot from. Did you select guided/automatic partitioning? (Did 6.06 even have that option?) If not, Linux needs a special boot partition to boot from, separate from your root partition. If it's not present, has the wrong partition type specified, is not marked bootable, yaboot.conf isn't pointing to it or it is simply empty, the OS will not boot.

Your problem with 10.04 sounds like Linux isn't liking your graphics card. If possible, I'd boot with the 10.04 installer CD and check for different installer options at boot. At the boot: prompt, hit the tab key and you'll get a list of different installers/options. Look for one that says something like "ofboot" or "ofvideo". I believe there may also be some options you can pass the kernel to boot with Open Firmware video, though they escape me at the moment.

Good luck!

---

### Post by rrrrob on 2010-07-25
Hello imrazor

Thanks for the response.

I gave up on the 6.06 install because the installer was giving me troubles.  I reformatted, wiped the drive, and started over with the 10.04 installer as follows.

The system has two hard drives.

One drive (SCSI id 1) has the OSX system on it.

The second drive (SCSI id 0) was formatted with 2 partitions in the mac "Disk Utility".

One of the partitions is a very small Mac OSX (Journeld) partition which is completely empty.

The other partition was actually unformatted empty space.

I booted from the Ubuntu 10.04 server install cd.  At the boot: prompt I typed (this is from my memory I'm pretty sure this is what I typed)
boot: installer-powerpc Mem=1024m video=ofonly

The installer ran threw all the steps in the instructions asking things like language, key board, etc. When it came to the formatting/partitioning section I did use the guided/automatic partitioning on the free space which seemed to format the empty partition.  Please understand the installer seemed to work fine.  It completed, ejected the disk, and rebooted the system.

When the computer came up in what the documentation called "The Moment of Truth" or "Smoke Test" What I got was the before mentioned screens which ended with a white screen.  When I first tried to install 10.04 I had a bright white to black screen issue but this seems to have been fixed by adding the "Mem=1024m video=ofonly" comments to the install command.

I believe the system is trying to boot the linux drive and system because otherwise I don't believe the drive would be recognized as a start up drive when depressing the option key at boot.

Understand I'm still very unclear as to how this all should work.  If it truly is a drive capable of booting the system my mind tells me that if I go into the "system preferences > startup disk" when booted in OSX, I should see the linux drive.  I do not.  Is this right?  Is it wrong?  Hard for someone who has zero experience to know what's right and what's wrong.

I hope I'm explaining my process and results clearly.  If I'm not tell me what else I need to submit in order to help clear it up.  I'm looking for what ever suggestion at this point.  I'm lost….

Thanks for the help
Rob

---

### Post by imrazor on 2010-07-25
Rob-

I think I understand what you're describing. Right now, after you hear the startup bong, what do you see on the screen? The first thing you should see is some text asking you whether you want to boot OS X, Linux or a CD. If you select Linux, it should take you to a second screen that ends with a prompt that says "boot:". If you make it that far, try typing ```
Linux Mem=1024m video=ofonly
```You can also try hitting the tab key to see what other boot options are available. Usually there's also some kind of recovery mode that might at least get you to a root shell.

If the above kernel options work (ie, the "Mem=1024m video=ofonly" bit), then that can theoretically be added to your /etc/yaboot.conf file, though I've had problems getting options in that file to actually work.

---

### Post by rrrrob on 2010-07-26
Hello imrazor,

From power off, I press the power button and the start chime is herd.  The monitor turns grey and the mac os folder denoting that the system is looking for a startup drive is flashing ? and mac logo.  After a short period of time (10-20 sec) the screen goes black and the following is shown as white text on the black screen…


First stage Ubuntu bootstrap

Press l for GNU/Linux
x for Mac OSX
c for CDROM

Stage 1 Boot:



if I press l or wait the following line of copy appears just below the above copy…


Loading second stage bootstrap…



And what I have to believe is a Ubuntu folder with the same ? and mac logo begins flashing for a few more seconds. (10-20 sec)  Finally the screen flashes to all white and nothing seems to be happening.  I don't hear a drive spinning and the screen doesn't change.


You mention the  /etc/yaboot.conf file, I read somewhere that I could not edit this file within the mac os.  That the act of changing it and saving it somehow changed the file in such a way that the Linux system would no longer recognize it.  Understand I have not tried this myself and have no first hand knowledge, it is something I read somewhere in the forums.  Thus I've been hesitant to edit it.

Thanks for the help
Rob

---

### Post by rrrrob on 2010-07-26
Well I just booted into the mac os to see what I could on the ubutnu drive.  What I found was that the Ubutnu drive was no mounted, sort of.  What I mean is there were two drives on the desktop.  One was the mac os drive, the other was the mac partition of the second drive.  Sense I didn't see a drive representing the Ubutnu system I decided to open disk utility to see what I could.

What I see is as follows

34.2 GB QUANTUM 
    MacPart
    disk0s11
    disk0s12
34.2 GB QUANTUM
    MacHardDrive

Now MacPart is formatted as Mac OS Extended (Journaled).
disk0s11 and disk0s12 are formatted as Apple_UNIX_SVR2
disk0s11 says it has a capacity of 29.7 GB
disk0s12 says it has a capacity of 1.3 GB

Neither of the two UNIX disks will mount and they are greyed out in the list.  Is it that I didn't initially format and partition the drive correctly? Shouldn't the drives mount on the desktop?  Shouldn't I be able to browse the files on the Ubuntu drives from within the mac os?

---

### Post by imrazor on 2010-07-26
> **rrrrob said:**
> Well I just booted into the mac os to see what I could on the ubutnu drive.  What I found was that the Ubutnu drive was no mounted, sort of.  What I mean is there were two drives on the desktop.  One was the mac os drive, the other was the mac partition of the second drive.  Sense I didn't see a drive representing the Ubutnu system I decided to open disk utility to see what I could.

What I see is as follows

34.2 GB QUANTUM 
    MacPart
    disk0s11
    disk0s12
34.2 GB QUANTUM
    MacHardDrive

Now MacPart is formatted as Mac OS Extended (Journaled).
disk0s11 and disk0s12 are formatted as Apple_UNIX_SVR2
disk0s11 says it has a capacity of 29.7 GB
disk0s12 says it has a capacity of 1.3 GB

Neither of the two UNIX disks will mount and they are greyed out in the list.  Is it that I didn't initially format and partition the drive correctly? Shouldn't the drives mount on the desktop?  Shouldn't I be able to browse the files on the Ubuntu drives from within the mac os?

It sounds like the bootloader is installed correctly, but yaboot.conf is pointing to the wrong root partition. This might be correctable by booting off the Ubuntu CD, mounting the boot/root partition and editing the yaboot.conf file. But that would probably be an unproductive use of time, as I'm not sure that would really work.

Why do you have the small OS X partition ("MacPart") on the first  drive? Move any data off it that you need, and reinstall Ubuntu, but use Guided partitioning on the whole drive, instead of selecting the free space option. I'm not an expert on this, but I think your odds of success will be better that way. I think that small OS X partition may be  confusing the installer, though you'd think it'd be bright enough to deal with that.

Good luck!

---

### Post by rrrrob on 2010-07-27
The reason for the small mac partition was that I was having trouble with the installer.  Due to the "no mac bootstrap" message that the installer kept giving me, and a message I had read, I thought I had to put a small mac partition on the drive in order to get the installer to work.

I've now reformatted and repartitioned the drive without the mMac partition.  This time as follows.

Open Mac disk-utility.
Selected drive (not partition on drive).
Chose the partition tab.
Chose the Options button, and had the following to choose from.

GUID Partition Table (use for startup on intel based macs)
Apple Partition Map (use as startup for powerpc based macs and mount on all macs)
Master Boot Record (for use with DOS and Windows based systems)

This time I'm going to choose
Apple Partition Map
Free Space
and no OS 9 Drivers

Done there are no Partitions/Volumes

Now Erase tab, 
choose UNIX File System,
No Mac OS 9 Drivers and chose Erase.

This should remove files that were left behind. Doing this creates a UNIX volume so I'm going to Partition the drive one more time using

Apple Partition Map
Free Space
and no OS 9 Drivers

This should leave a clean drive.
Next
Reinstalling the Ubuntu Server 10.04 again. Using the guided/use largest free space.

Attempt to boot into Ubuntu…..  Still getting this error

************* From the screen ****************

First stage Ubuntu bootstrap

Press l for GNU/Linux
x for Mac OSX
c for CDROM

Stage 1 Boot:

************************************************
******  If I type "l" or simply let it continue on its own I see the following  ******
************* From the screen ****************

Loading second stage bootstrap…

"little flashing folder icon"

************************************************
After a short period of time the screen flashes to solid white and nothing more happens.


Now when I boot into the Mac OS I'm receiving this message
Disk Insertion
The disk you inserted was not readable by this computer

I did not get this error when I had a Mac Partition on the drive.  I'm reading all sorts of old messages on the net that say not to use disk-utility to format the disk.  That I should be using some shell scripts.  I thought this was not necessary with the new 10.04.  I'm back to feeling that I have two issues.

First I don't feel I have the drive formatted correctly

Second I think the Ubuntu software is loading because the system sees the Linux drive as a startup drive.  If it didn't the drive wouldn't show up as a choice when I start with the option key held down.  So my guess is that I'm having a memory and/or video issue.  This is because I can't run the installer if I leave either comment out of the commend.

This sounds exactly like what I'm running into
[http://guide.ubuntuforums.org/showthread.php?p=4974387](http://guide.ubuntuforums.org/showthread.php?p=4974387)
but I never get to the second stage.  I get the loading second stage and can't do anything at this point but wait for it to fail.

Thanks for the help
Rob

---

### Post by imrazor on 2010-07-27
> **rrrrob said:**
> The reason for the small mac partition was that I was having trouble with the installer.  Due to the "no mac bootstrap" message that the installer kept giving me, and a message I had read, I thought I had to put a small mac partition on the drive in order to get the installer to work.

I've now reformatted and repartitioned the drive without the mMac partition.  This time as follows.

Open Mac disk-utility.
Selected drive (not partition on drive).
Chose the partition tab.
Chose the Options button, and had the following to choose from.

GUID Partition Table (use for startup on intel based macs)
Apple Partition Map (use as startup for powerpc based macs and mount on all macs)
Master Boot Record (for use with DOS and Windows based systems)

This time I'm going to choose
Apple Partition Map
Free Space
and no OS 9 Drivers

Done there are no Partitions/Volumes

Now Erase tab, 
choose UNIX File System,
No Mac OS 9 Drivers and chose Erase.

This should remove files that were left behind. Doing this creates a UNIX volume so I'm going to Partition the drive one more time using

Apple Partition Map
Free Space
and no OS 9 Drivers

This should leave a clean drive.
Next
Reinstalling the Ubuntu Server 10.04 again. Using the guided/use largest free space.

Attempt to boot into Ubuntu…..  Still getting this error

************* From the screen ****************

First stage Ubuntu bootstrap

Press l for GNU/Linux
x for Mac OSX
c for CDROM

Stage 1 Boot:

************************************************
******  If I type "l" or simply let it continue on its own I see the following  ******
************* From the screen ****************

Loading second stage bootstrap…

"little flashing folder icon"

************************************************
After a short period of time the screen flashes to solid white and nothing more happens.


Now when I boot into the Mac OS I'm receiving this message
Disk Insertion
The disk you inserted was not readable by this computer

I did not get this error when I had a Mac Partition on the drive.  I'm reading all sorts of old messages on the net that say not to use disk-utility to format the disk.  That I should be using some shell scripts.  I thought this was not necessary with the new 10.04.  I'm back to feeling that I have two issues.

First I don't feel I have the drive formatted correctly

Second I think the Ubuntu software is loading because the system sees the Linux drive as a startup drive.  If it didn't the drive wouldn't show up as a choice when I start with the option key held down.  So my guess is that I'm having a memory and/or video issue.  This is because I can't run the installer if I leave either comment out of the commend.

This sounds exactly like what I'm running into
[http://guide.ubuntuforums.org/showthread.php?p=4974387](http://guide.ubuntuforums.org/showthread.php?p=4974387)
but I never get to the second stage.  I get the loading second stage and can't do anything at this point but wait for it to fail.

Thanks for the help
Rob
OK, I'm going to ask some important questions. How much do you need OS X on this machine? Do you have installation disks for OS X or MacOS 9? Do you have a way to backup your data? Is this machine an experiment, or are you trying to put into some sort of production use? I seem to recall you saying something about a server, but I don't think you specified what kind of server (file, print, database, web, etc.)

In the meantime, let me describe how I installed Linux on my G5. First of all, I had two disks. A 500gb sata drive with OS X, and an 80GB SATA drive with a stale OS X install on it. I wiped the 80GB clean with the Ubuntu installer (the OS X disk utility never touched it) and used guided partitioning on the entire disk. This got me a dual boot system. I also get the message from OS X at boot about an unrecognizable disk, but I just click ignore.

I initially tried to partition manually, but I didn't know exactly what was required for PowerPC Linux and yaboot to start up, so it didn't work at first. I then just went with a guided partitioning of the entire disk, and that seemed to work well.

Here's a dump of my G5's partition structure from the command pdisk. The first disk is dedicated to OS X, the second to Ubuntu.

[FONT="Fixedsys"]Partition map (with 512 byte blocks) on '/dev/rdisk0'
 #:                type name        length   base      ( size )
 1: Apple_partition_map Apple           63 @ 1        
 2:          Apple_Free             262144 @ 64        (128.0M)
 3:           Apple_HFS Untitled 976510944 @ 262208    (465.6G)
 4:          Apple_Free                 16 @ 976773152

Device block size=512, Number of Blocks=976773168 (465.8G)
DeviceType=0x0, DeviceId=0x0


Partition map (with 512 byte blocks) on '/dev/rdisk1'
 #:                type name        length   base      ( size )
 1: Apple_partition_map Apple           63 @ 1        
 2:     Apple_Bootstrap untitled      2048 @ 2048      (  1.0M)
 3:     Apple_UNIX_SVR2 untitled 150456320 @ 4096      ( 71.7G)
 4:     Apple_UNIX_SVR2 swap       5851136 @ 150460416 (  2.8G)
 5:          Apple_Free Extra         1984 @ 64       
 6:          Apple_Free Extra         1024 @ 156311552
[/FONT]

As you can see, the partition map created by the guided partitioner on the Ubuntu install CD is rather complicated. If I get a chance tonight, I'll repost how the 2nd hard drive looks from Ubuntu.

---

### Post by rrrrob on 2010-07-27
No I do not need the Mac drive.  I can unplug it at any time.

Yes I do intend to use it as a web server, locally, for testing purposes.  I want to be able to experiment with code locally on a server with a similar OS as possible to those I use for for live sites.  Figure I'd rather crash this system than the live one.

I've found some threads on the forum that say I should add the video=ofonly and a nosplash command to the .conf file.  My guess is that I should also add the Mem=1024m as well.  Thing is I don't seem to be able to get to a place where I can do this.

I've also been looking at it for so long that the obvious could be staring me in the face and I'm not seeing it.

Thanks again for the help
Rob

---

### Post by rrrrob on 2010-07-28
imrazor,

thanks for the help…  after reading your last post I decided to remove the Mac OS drive from the system to see what happens.  No white screen!!!  Thats the good news.  Bad news is that I don't think the systems is seeing the install correctly.  At boot I'm getting the mac looking for system flashing folder icon.  Then the screen goes black, changes color of black and goes to the following

************* From the screen ****************
First stage Ubuntu bootstrap

Press l for GNU/Linux
x for Mac OSX
c for CDROM

Stage 1 Boot:

************************************************


If I type "l" or simply let it continue on its own I see the following


************* From the screen ****************
Loading second stage bootstrap…

"little flashing folder icon"

************************************************


Now after a short period of time instead of going to a white screen it is repeating this process


************* From the screen ****************
First stage Ubuntu bootstrap

Press l for GNU/Linux
x for Mac OSX
c for CDROM

Stage 1 Boot:

************************************************


If I type "l" or simply let it continue on its own I see the following


************* From the screen ****************
Loading second stage bootstrap…

"little flashing folder icon"

************************************************

So…  I'm going to try a clean install from the Server disk without having the Mac drive in the system and see what happens.  Guess it can't hurt

Rob

---

### Post by rrrrob on 2010-07-28
Ok,

I reinstalled the Ubuntu 10.04 Server Using the Guided Entire Disk setting and am still getting the same error.  It is like the computer can't find the system on the drive.

The CD boots the system just fine
the installer seems to complete just fine

do I need to bless the system some how?

---

### Post by rrrrob on 2010-07-28
Amazing how well the forum search works if one actually searches for the right thing. ;)

I have found these which describe the same difficulties I'm having and may very well be the answer I'm looking for.

[http://ubuntuforums.org/showthread.php?t=833570](http://ubuntuforums.org/showthread.php?t=833570)

[http://ubuntuforums.org/showthread.php?t=800041&highlight=loading+stage+bootstrap](http://ubuntuforums.org/showthread.php?t=800041&highlight=loading+stage+bootstrap)

But

I'm not exactly sure how to access all the information that they are talking about. The sudo fdisk command is used in the terminal, it doesn't work booted on the install cd at the boot: prompt.

when I plug the mac drive back in and run

sudo fdisk -l /dev/sda

I get an error that there is no l command.  There are several others listed but not l.

Also sense the drive that contains the Ubuntu files doesn't mount on my system how am I to access the yaboot.conf file?

---

### Post by rrrrob on 2010-07-28
I'm realizing what the thing staring me in the face is, the thing that I'm finding so confusing, it is the syntax/commands.  The few syntax/commands that I know, and much that I'm reading are all just a little bit different.  Thus most of the time I'm not typing in the correct syntax/commands and I'm getting errors.  I thought these commands were being typed in to the terminal in Mac OS X because I haven't been able to get much to work at the boot: command prompt.



So stepping back a bit I typed help at the boot: command prompt and found this

**************** FROM SCREEN ***************
To boot a kernel image that is not defined in the yaboot configuration file enter the kernel image name as [[device:][partno], ]/path, where "device:" is the OpenFirmware device path to the disk the image resides on, and "partno" is the partition number the image resides on.  Note that the comma (,) is only required if you specify an OpenFirmware device, if you only specify a filename you should not start it with a ","

If you omit "device:" and "partno" yaboot will use the values of "device=" and "partition=" in yaboot.conf, right now those are set to: device=/pci@f2000000/@d/mac-io@7/ata-3@20000/disk@0
partition=2
*********************************************

Also I know I'm confused on the syntax for the drive.  I've seen /dev/hd* and /dev/sd*.  I understand that my system has SCSI-2 drives and thus I believe I should be using /dev/sd*, but I know that when I had the Mac OS booted and I looked at the drive partitions in disk=utility I saw that their names were disk0s1 and disk0s2.  I also know that if a CD was in the drive at boot that those names changed to disk1s1 and disk1s2.  I'm not sure why that is, I only know what I saw and was able to repeat.

So

I'm not sure what to type in at the boot: command prompt to check what my drive partition information is

and

I'm not sure what to type in at the boot: command prompt to view/edit the yaboot.conf file information.

So could someone please either tell me or help me determine what I need to enter for each of these.

No matter how long or how hard you look at something, you may still not see it.

Rob

---

### Post by svtguy88 on 2010-07-28
I just sort of skimmed everything you've typed, as I'm sitting in a Finance lecture right now and am still *half* paying attention to my professor.

Anyway, what I would do is remove OS X completely if you do not need it.  Yaboot doesn't like booting to OS X, and Apple's bootloader (the option key that brings up the available disks) is too slow/finicky for my liking.  

You said the drives are SCSI, are they truly SCSI or just recognized as one?  Only reason I ask is because my G4 has two SATA drives (running off of a PCI SATA controller) that are recognized as SCSI.


Alright, which version of Ubuntu are you using?  I've heard/had nothing but problems with getting the current LiveCD to boot properly.  It sounds like you are doing a text-based install (I think that's what the server install disk uses).  I would try that install again, and let it use the whole drive (guided partitioning).  Take note of what the drive is called (sdb1, sda1, etc).  Do not use OS X to format the drive.  OS X doesn't natively support ext2/3/4 filesystems--this is the reason that your drives weren't mounting to your desktop before (Macfuse with ext2fs lets you rear/write ext filesystems from OS X).

Let the install run, and let it reboot.  To be safe, you may want to even remove the other drive when you install it.  This will hopefully keep the system from trying to boot the wrong drive...but it should automatically configure yaboot to boot your Linux partition.

Hopefully it will boot.  Do you get any sort of terminal output (anything that looks like Linux loading--white text/black screen).  

If you still get the white screen problem (which you may...I don't think this is too different from what you've been attempting), I would download the latest Debian PPC image and install from that.  Ubuntu doesn't seem to support PPC Macs (and their graphics cards) very well.  Which graphics card do you have, anyway?

---

### Post by svtguy88 on 2010-07-28
> **rrrrob said:**
> I thought these commands were being typed in to the terminal in Mac OS X because I haven't been able to get much to work at the boot: command prompt.


Also I know I'm confused on the syntax for the drive.  I've seen /dev/hd* and /dev/sd*.  I understand that my system has SCSI-2 drives and thus I believe I should be using /dev/sd*, but I know that when I had the Mac OS booted and I looked at the drive partitions in disk=utility I saw that their names were disk0s1 and disk0s2.  



Rob

The reason the commands haven't worked is because most of the commands aren't going to be recognized by OS X, and the boot: prompt you have in yaboot is VERY primitive at best.  

What you can do to edit the yaboot.conf file is to boot from a live CD that gives you a Linux terminal to work at.  For example, Finnix, is a lightweight PPC distribution that you can burn to a CD and boot, leaving you in a Linux shell.  From here, you can execute some basic commands, such as editing the yaboot.conf file.

Now, the reason that OS X labels your disk as disk0s1 or whatever is because OS X uses a different naming scheme that Linux.  According to the [this]("http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/ch6.en.shtml"), SCSI drives will be located at sda or sdb (so your drives will most likely be sda1 or sdb1 or something similar).  

Once you have the Finnix (or whatever LiveCD you use) booted, you need to mount your drives with the following:

```
sudo mkdir /mnt/Linux
```

```
sudo mount -t ext3 /dev/<LOCATION_OF_DRIVE> /mnt/Linux
```

The first command creates a folder called "Linux" in the "mnt" directory.  The second mounts the ext3 filesystem that is located at <LOCATION_OF_DRIVE> to the newly created /mnt/Linux folder.  This means that navigating to the /mnt/Linux folder will display the filesystem located on your drive.  Note that where it says <LOCATION_OF_DRIVE> you need to type in the drive location.  If you don't know it, you can just try until you find it.  It's going to be at sda0, sda1, sdb0 or sdb1 more than likely.  Once it mounts, you can navigate to the yaboot.conf file with the following:

```
cd /mnt/Linux/etc
```

Now you are in the /etc directory of your Linux drive.  If you type "ls" it will display a list of directories and files in the /etc folder.  To open/edit the yaboot.conf file:

```
sudo nano yaboot.conf
```

Make your changes, use ctrl+x to exit (say "Y" to whether or not to save).  And then run:

```
sudo ybin -v
```

This takes the changes you made in yaboot.conf and writes them to your bootstrap (yaboot) partition.

---

### Post by rrrrob on 2010-07-28
Thanks for the reply

Using Ubuntu 10.04 Server and you are correct it is the text based install.

I have removed the Mac OS drive which has ended the white screen of death.

When booting to the Ubuntu System I get the mac os system folder for a few flashes like it is looking for a system then a black screen followed by a black screen with the following white text.



First stage Ubuntu bootstrap

Press l for GNU/Linux
x for Mac OSX
c for CDROM

Stage 1 Boot:


*then*

Loading second stage bootstrap…

"little flashing folder icon - ? <-> MacOS"


after a while the mac os symbol stays on the folder, the screen flashes and goes black, followed by a repeat of the white text and the entire process starts over.  It never seems to find the Ubuntu system. 

Below you can see information I captured from the mac system last week.  The only thing that has changed is that the Ubuntu system is now at SCSI id0 and has been formatted from/by the installer disk in the same way that you mentioned.

Your right I had all sorts of troubles with getting the system to boot from the CD until I found that if I type "install-powerpc Mem=1024m video=ofonly" it works every time.

My guess is that I need to add these same commands to the yaboot.conf and probably the nosplash as well.  Thing is I can't get far enough to do that.

and I forgot to write down the drive info you were talking about.  There is nothing left on the drive so I'm not opposed to blowing it away again if need be.  I do know that if I use 

/pci@f2000000/@d/mac-io@7/ata-3@20000/disk@0:2,

at the boot command in replace of [device:][partno] it seems to like it if that helps

I really don't think the yaboot.conf file is correct.  I think it cant find the drive and I think it has issues with the memory and the video.

I don't know how to view it or change it at this point.

As I said the following is all the information I have on the internals.  The drive is attached to a card, not directly to the mother board.  This was a mac server at one time and the two drives were set as a raid.  The drives are Quantum Atlas SCSI wide units part no 655-0862.

Thanks for the Help
Rob



Hardware:
Hardware Overview:
Machine Name: Power Mac G4
Machine Model: PowerMac3,3
CPU Type: PowerPC G4 (2.9)
Number Of CPUs: 2
CPU Speed: 500 MHz
L2 Cache (per CPU): 1 MB
Memory: 1 GB
Bus Speed: 100 MHz
Boot ROM Version: 4.2.8f1

Graphics/Displays:
ATY,Rage128Pro:
Chipset Model: ATY,Rage128Pro
Type: Display
Bus: AGP
Slot: SLOT-A
VRAM (Total): 16 MB
Vendor: ATI (0x1002)
Device ID: 0x5046
Revision ID: 0x0000
ROM Revision: 113-72701-125
Displays:
Apple Studio Display:
Display Type: LCD
Resolution: 1280 x 1024
Depth: 16-bit Color
Built-In: Yes
Core Image: Not Supported
Main Display: Yes
Mirror: Off
Online: Yes
Quartz Extreme: Not Supported

PCI Cards:
ATTO,ExpressPCIProUL3D:
Type: scsi-2
Bus: PCI
Slot: SLOT-D
Vendor ID: 0x1000
Device ID: 0x0020
ROM Revision: 1.6.1f1
Revision ID: 0x0001
ATTO,ExpressPCIProUL3D:
Type: scsi-2
Bus: PCI
Slot: SLOT-D
Vendor ID: 0x1000
Device ID: 0x0020
ROM Revision: 1.6.1f1
Revision ID: 0x0001

Parallel SCSI:
SCSI Parallel Domain 0:
Initiator Identifier: 7
SCSI Target Device @ 0:
Manufacturer: QUANTUM
Model: ATLAS10K2-TY367L
Revision: DD20
SCSI Target Identifier: 0
SCSI Device Features: Wide, Sync, DT
SCSI Initiator/Target Features: Wide, Sync, DT
Peripheral Device Type: 0
SCSI Logical Unit @ 0:
Capacity: 34.2 GB
Manufacturer: QUANTUM
Model: ATLAS10K2-TY367L
Revision: DD20
Removable Media: Yes
Detachable Drive: No
BSD Name: disk0
OS9 Drivers: Yes
SCSI Logical Unit Identifier: 0
S.M.A.R.T. status: Not Supported
Volumes:
MacHD:
Capacity: 34.2 GB
Available: 27.24 GB
Writable: Yes
File System: Journaled HFS+
BSD Name: disk0s6
Mount Point: /
SCSI Target Device @ 1:
Manufacturer: QUANTUM
Model: ATLAS10K2-TY367L
Revision: DD20
SCSI Target Identifier: 1
SCSI Device Features: Wide, Sync, DT
SCSI Initiator/Target Features: Wide, Sync, DT
Peripheral Device Type: 0
SCSI Logical Unit @ 0:
Capacity: 34.2 GB
Manufacturer: QUANTUM
Model: ATLAS10K2-TY367L
Revision: DD20
Removable Media: Yes
Detachable Drive: No
BSD Name: disk1
OS9 Drivers: No
SCSI Logical Unit Identifier: 0
S.M.A.R.T. status: Not Supported
Volumes:
Linux:
Capacity: 34.07 GB
Available: 34.05 GB
Writable: Yes
File System: HFS+
BSD Name: disk1s3
Mount Point: /Volumes/Linux

---

### Post by rrrrob on 2010-07-28
pkmgarf Thanks so much for the reply

I have the live cd and I am booted into Finnix,  command line is "root@tty1:~#"

I believe I understand and follow the majority of what you have said, but I'm not following
"you need to mount your drives with"

"sudo mkdir /mnt/Linux"

I don't believe you intend I type this 

"root@tty1:~# sudo mkdir /mnt/Linux"

Because that gets this

"sudo: unable to resolve host finnix"

Thus I must not be grasping the first step.

I do however now have the following information after running "sudo fdisk -l /dev/sda"

sudo: unable to resolve host finnix
/dev/sda
#                    type                              name               length         base                size          system
/dev/sda1    Apple_partitio_map   Apple                    63   @   1                      (31.5k)      Partition Map
/dev/sda2    Apple_Bootstrap        Untitled            2048   @   2048               (1.0m)       NewWorld bootblock
/dev/sda3    Apple_UNIX_SVR2      Untitled   68679680   @   4096              (32.7G)      Linux Native
/dev/sda4    Apple_UNIX_SVR2      swap          3037184   @   68683776     (1.4G)        Linux Swap
/dev/sda5    Apple_free                  extra                 1984   @   64                   (992.0k)    Free
/dev/sda6    Apple_free                  extra                   860   @   71720960     (430.0k)    Free

So my guess is that the drive would be sda3?

Now can you explain the first 2 steps where you say "you need to mount your drives with"?  That is still confusing me for some reason.

Thanks for the help
Rob

---

### Post by rrrrob on 2010-07-29
Did some more reading and realized I was having another terminology issue.  Have to admit the more I'm understanding this system the more interesting I'm finding it.

As for sudo: unable to resolve host finnix

I found this link [http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

my guess is that if I fix this first and then go back and try the steps you provided it should work.

Thanks again for the help
Rob

---

### Post by rrrrob on 2010-07-29
Well that didn't work so well, here is watt I ended up with,

root@tty1;~# cat /etc/hosts
cat: /etc/hosts: No such file or directory
root@tty1;~# sudo mkdir /mnt/Linux
sudo: unable to resolve host finnix
root@tty1;~# sudo mount -t ext3 /dev/sda3 /mnt/Linux
sudo: unable to resolve host finnix
[   384.991697] EXT3-fs: sda3: couldn't mount because of unsupported optional features (240).
mount: wrong fs type, bad option, bad super block on /dev/sda3,
missing codepage or helper program, or other error
In some cases useful info is found in sys log - try
dmsg : tail or so
root@tty1;~#

---

### Post by rrrrob on 2010-07-29
Ok, update

Please understand My Linux experience will be One Week Tomorrow.  I'm really new at this.....

First I don't think I mentioned that in order to get Finnix Live CD to run I have to use the following command

finnix Mem=1024m video=ofonly

in a sense that is a good thing, consistency between the two makes me believe I'm on the right path.

Now for what I'm finding once I try to edit the yaboot.conf file.

To review this is my partition structure shown when running "sudo fdisk -l /dev/sda"

sudo fdisk -l /dev/sda
sudo: unable to resolve host finnix
/dev/sda
# type name length base size system
/dev/sda1 Apple_partitio_map Apple 63 @ 1 (31.5k) Partition map
/dev/sda2 Apple_Bootstrap untitled 2048 @ 2048 (1.0m) NewWorld bootblock
/dev/sda3 Apple_UNIX_SVR2 untitled 68679680 @ 4096 (32.7G) Linux native
/dev/sda4 Apple_UNIX_SVR2 swap 3037184 @ 68683776 (1.4G) Linux swap
/dev/sda5 Apple_free Extra 1984 @ 64 (992.0k) Free space
/dev/sda6 Apple_free Extra 860 @ 71720960 (430.0k) Free space

Block size=512, Number of Blocks=71721820
DeviceType=0x0, DeviceId=0x0

I have also located my ofpath incase there may be an issue with it in the yaboot.conf file,  Figured I needed to check after reading this " [http://ubuntuforums.org/showthread.php?t=800041&highlight=loading+stage+bootstrap&page=2](http://ubuntuforums.org/showthread.php?t=800041&highlight=loading+stage+bootstrap&page=2) "

device=/pci@f2000000/@d/mac-io@7/ata-3@20000/disk@0
partition=2

alright, so now I am booted into Finnix and I enter
root@tty1;~# sudo mkdir /mnt/Linux

and get back this
sudo: unable to resolve host finnix

This threw me, I thought I was entering the wrong thing until I found the following thread, but it is a couple years old.  After reading the thread I'm wondering if I need the sudo command because the command line I'm getting from Finnix is root@tty1:~# sense it is root does this mean I don't need sudo, thus why sudo is unable to resolve?
" [http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361) "

I'm thinking part of what I'm seeing is because I'm booted using the Live CD. This link I found in the above thread makes me suspect I'm still not on the right path. That I need to do something a bit different because I'm booted from the Live CD.
" [http://www.kubuntuforums.net/forums/index.php?topic=3092772](http://www.kubuntuforums.net/forums/index.php?topic=3092772) "

If I try to run
root@tty1;~# cat /etc/hosts

I get ( My guess is that this response is due to my being booted from Live CD instead of the System )
cat: /etc/hosts: No such file or directory


Moving on, I noticed that the before mentioned threads seemed to indicate that even though the system was displaying "sudo: unable to resolve host finnix" that the command was still processing sucessfully. So, following the steps pkmgarf laid out I have the following 

root@tty1;~# sudo mkdir /mnt/Linux
sudo: unable to resolve host finnix
root@tty1;~# sudo mount -t ext3 /dev/sda1 /mnt/Linux
sudo: unable to resolve host finnix
[ 5026.299251] VFS: Can't find ext3 filesystem on dev sda1.
mount: wrong fs type, bad option, bad super block on /dev/sda1,
missing codepage or helper program, or other error
In some cases useful info is found in sys log - try
dmsg : tail or so

root@tty1;~# sudo mount -t ext3 /dev/sda2 /mnt/Linux
sudo: unable to resolve host finnix
[ 5277.352880] VFS: Can't find ext3 filesystem on dev sda2.
mount: wrong fs type, bad option, bad super block on /dev/sda2,
missing codepage or helper program, or other error
In some cases useful info is found in sys log - try
dmsg : tail or so

root@tty1;~# sudo mount -t ext3 /dev/sda3 /mnt/Linux
sudo: unable to resolve host finnix
[ 5392.050360] EXT3-fs: sda3: couldn't mount because of unsupported optional features (240).
mount: wrong fs type, bad option, bad super block on /dev/sda3,
missing codepage or helper program, or other error
In some cases useful info is found in sys log - try
dmsg : tail or so

root@tty1;~# sudo mount -t ext3 /dev/sda4 /mnt/Linux
sudo: unable to resolve host finnix
mount: /dev/sda4 already mounted or /mnt/Linux busy
root@tty1;~# sudo mount -t ext3 /dev/sda5 /mnt/Linux
sudo: unable to resolve host finnix
[ 5729.776570] VFS: Can't find ext3 filesystem on dev sda5.
mount: wrong fs type, bad option, bad super block on /dev/sda5,
missing codepage or helper program, or other error
In some cases useful info is found in sys log - try
dmsg : tail or so

root@tty1;~# sudo mount -t ext3 /dev/sda6 /mnt/Linux
sudo: unable to resolve host finnix
[ 5729.776570] VFS: Can't find ext3 filesystem on dev sda6.
mount: wrong fs type, bad option, bad super block on /dev/sda6,
missing codepage or helper program, or other error
In some cases useful info is found in sys log - try
dmsg : tail or so


Ok, so that is what I got back when I entered those commands.  I'm going to halt and reboot from the Live CD and see what happens if I don't use the sudo command.


root@tty1;~# mkdir /mnt/Linux
root@tty1;~# mount -t ext3 /dev/sda3 /mnt/Linux
[ 142.788478] EXT3-fs: sda3: couldn't mount because of unsupported optional features (240).
mount: wrong fs type, bad option, bad super block on /dev/sda3,
missing codepage or helper program, or other error
In some cases useful info is found in sys log - try
dmsg : tail or so

root@tty1;~# mount -t ext3 /dev/sda4 /mnt/Linux
mount: /dev/sda4 already mounted or /mnt/Linux busy
root@tty1:~# cd /mnt/Linux/etc
-bash: cd: /mnt/Live/etc: No such file or directory
root@tty1:~#


Well thats where I'm at and what I'm getting
any help you can give is extremely appreciated
Thanks for the time
Rob

---

### Post by svtguy88 on 2010-07-29
Try running the commands I gave you without "sudo."  Sudo is a method of executing commands with higher priveledges.  It makes your standard user account into a temporary "superuser" (think: administrator) for a given command or set of commands.  

It looks like Finnix logs you in as "root," as you can see at your command prompt (root@tty1).  The user "root" IS the superuser, meaning you are always running commands with elevated priveldges.  

I forgot Finnix logs you in that way.  Usually logging in as "root" is dangerous, as it can lead to executing commands that you shouldn't and just causing havoc in general.  However, the nature of Finnix is to rescue a broken system (at least that's what I've use dit for), so being logged in as "root" keeps you from having to type "sudo" in front of commands.


**edit**
On a side note, where are you in Wisconsin?  Just curious...

---

### Post by rrrrob on 2010-07-29
root@tty1;~# mkdir /mnt/Linux
root@tty1;~# mount -t ext3 /dev/sda3 /mnt/Linux
[ 142.788478] EXT3-fs: sda3: couldn't mount because of unsupported optional features (240).
mount: wrong fs type, bad option, bad super block on /dev/sda3,
missing codepage or helper program, or other error
In some cases useful info is found in sys log - try
dmsg : tail or so

root@tty1;~# mount -t ext3 /dev/sda4 /mnt/Linux
mount: /dev/sda4 already mounted or /mnt/Linux busy
root@tty1:~# cd /mnt/Linux/etc
-bash: cd: /mnt/Live/etc: No such file or directory
root@tty1:~#


I don't think it is working because of this message above
[ 142.788478] EXT3-fs: sda3: couldn't mount because of unsupported optional features (240)

after I got to this point I stopped because I didn't want to mess any thing up.

Thanks for the response

*******off topic*******
western racine county

---

### Post by svtguy88 on 2010-07-29
Alright.  Try the mount command ("mount -t ext3....") again but instead of ext3 use ext2.  Or even try ext4.  I don't know what the default filesystem is when you install from the ubuntu server cd.

Don't bother mounting sda4.  It looks like it was already done, and it's just the swap space.  You don't need to do anything there.

---

### Post by rrrrob on 2010-07-29
ok here is what I have so far

root@tty1;~# mkdir /mnt/Linux
root@tty1;~# mount -t ext3 /dev/sda2 /mnt/Linux
[ 6411.200669] VFS: Can't find ext3 filesystem on dev sda2.
mount: wrong fs type, bad option, bad super block on /dev/sda2,
missing codepage or helper program, or other error
In some cases useful info is found in sys log - try
dmsg : tail or so

root@tty1;~#

understand that I had run the halt command and rebooted the system sense the last attempt.  Thus this is a new clean attempt at this.

Thanks again for the help

Rob

---

### Post by rrrrob on 2010-07-29
Just dawned on me I read your message wrong trying the others now...

---

### Post by rrrrob on 2010-07-29
Rock On!!

## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf for details. Do not make changes until you have!!
## see also: /use/share/doc/yaboot/examples for example configurations.
##
## For  dual -boot menu, add one or more of:
## bed=/dev/hdaX, macos=/dev/hdaZ

boot=/dev/sda2
device=/pci@f2000000/pci-bridge@d/ATTO,ExpressPCIProUL3D@4,1/@0:
partition=3
root=/dev/sda3
timeout=50
install=/use/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
label=Linux
read-only
initrd=/boot/initrd.img
append="quiet splash Mem=1024m video=ofonly"

image=/boot/vmlinux.old
label=old
read-only
initrd=/boot/initrd.img.old
append="quiet splash Mem=1024m video=ofonly"


Ok, and that is what I see in the yaboot.conf when I open it.

---

### Post by rrrrob on 2010-07-29
After review it looks like device and partition are not correct

What I have in my notes
device=/pci@f2000000/@d/mac-io@7/ata-3@20000/disk@0
partition=2

What is in the yaboot.conf
device=/pci@f2000000/pci-bridge@d/ATTO,ExpressPCIProUL3D@4,1/@0:
partition=3


As for adding "Mem=1024m video=ofonly" it seems to already be there but I'm under the understanding that the line should read like this in both instances?
append="nosplash Mem=1024m video=ofonly"

Am I correct?

Thanks again for all the help
Rob

---

### Post by rrrrob on 2010-07-29
Ok, made changes

control+x and the Y and then return
Ran ybin -v

Got back this following message

ybin: Warning: no /etc.yaboot.conf, running yabootconfig to make one
yabootconfig: Could not determine root partition, aborting...
ybin: yabootconfig failed, please supply a valid /etc/yaboot.conf
ybin: You may also use ybin's --boot, --image, --partition, and --device switches
ybin: These switches will cause ybin to generate a basic yaboot.conf on the fly
root@tty1:/mnt/Linux/etc


Ok????

---

### Post by svtguy88 on 2010-07-29
> **rrrrob said:**
> Rock On!!

## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf for details. Do not make changes until you have!!
## see also: /use/share/doc/yaboot/examples for example configurations.
##
## For  dual -boot menu, add one or more of:
## bed=/dev/hdaX, macos=/dev/hdaZ
[B]
boot=/dev/sda2[/B]
device=/pci@f2000000/pci-bridge@d/ATTO,ExpressPCIProUL3D@4,1/@0:
partition=3
root=/dev/sda3
timeout=50
install=/use/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot



This line should be boot=/dev/sda3 because if you look at your fdisk -l output:

> **rrrrob said:**
> 
sudo fdisk -l /dev/sda
sudo: unable to resolve host finnix
/dev/sda
# type name length base size system
/dev/sda1 Apple_partitio_map Apple 63 @ 1 (31.5k) Partition map
/dev/sda2 Apple_Bootstrap untitled 2048 @ 2048 (1.0m) NewWorld bootblock
**/dev/sda3 Apple_UNIX_SVR2 untitled 68679680 @ 4096 (32.7G) Linux native**
/dev/sda4 Apple_UNIX_SVR2 swap 3037184 @ 68683776 (1.4G) Linux swap
/dev/sda5 Apple_free Extra 1984 @ 64 (992.0k) Free space
/dev/sda6 Apple_free Extra 860 @ 71720960 (430.0k) Free space

Block size=512, Number of Blocks=71721820
DeviceType=0x0, DeviceId=0x0



/dev/sda3 is the location of your Linux install ("linux native" it is labeled).

> **rrrrob said:**
> After review it looks like device and partition are not correct

What I have in my notes
[B]device=/pci@f2000000/@d/mac-io@7/ata-3@20000/disk@0
partition=2[/B]

What is in the yaboot.conf
[B]device=/pci@f2000000/pci-bridge@d/ATTO,ExpressPCIProUL3D@4,1/@0:
partition=3[/B]


Where did you get the value that you have in your notes?  What command/program/operating system did it come from?  It looks like it's probablyt out of OS X?  I suspect the line that was in yaboot.conf is correct, as Linux will want to know what SCSI controller card your drives are attaced to.  In your case, it is apparently the UL3D by ATTO.


> **rrrrob said:**
> 
As for adding "Mem=1024m video=ofonly" it seems to already be there but I'm under the understanding that the line should read like this in both instances?
append="nosplash Mem=1024m video=ofonly"
Rob

I don't think changing quietsplash to nosplash will do anything for you. All that entry does is change the splash screen ("Ubuntu" loading screen). 

Go ahead and edit your yaboot.conf to point to /dev/sda3.  The only thing I'm not sure about is the root=/dev/sda3.  On my machine, yaboot.conf reads "boot:/dev/hda2" and "root:/dev/hda3."  I guess following the pattern of the number on "hda" increasing by one, you could change yours to "root:/dev/hda4" and see what happens.

**edit**

I just saw your post on ybin not working.  This is because it is trying to edit the yaboot.conf for the device you are booted off of, which is the Finnix live CD, and there is no yaboot.conf to edit there.  This means we need to point ybin to the boot device.  I'll get you the correct command in a few minutes...I don't remember ybin's options off hand.

---

### Post by svtguy88 on 2010-07-29
Alright, after a quick glance at the man page for ybin, I think I've got it all sorted out.  Let's look back at your "fdisk -l" output:


> **rrrrob said:**
> 
sudo fdisk -l /dev/sda
sudo: unable to resolve host finnix
/dev/sda
# type name length base size system
/dev/sda1 Apple_partitio_map Apple 63 @ 1 (31.5k) Partition map
**/dev/sda2 Apple_Bootstrap untitled 2048 @ 2048 (1.0m) NewWorld bootblock**
/dev/sda3 Apple_UNIX_SVR2 untitled 68679680 @ 4096 (32.7G) Linux native
/dev/sda4 Apple_UNIX_SVR2 swap 3037184 @ 68683776 (1.4G) Linux swap
/dev/sda5 Apple_free Extra 1984 @ 64 (992.0k) Free space
/dev/sda6 Apple_free Extra 860 @ 71720960 (430.0k) Free space

Block size=512, Number of Blocks=71721820
DeviceType=0x0, DeviceId=0x0


The man page for ybin says that you can run it with the option "b" to install/update the yaboot boot loader on a specified boot device.  In your case, this device is "sda2" as you can see by the "NewWorld bootblock" label on it.  After editing the yaboot.conf file, run this command to update your boot drive:

```
ybin -b --boot /dev/sda2 -v
```

Let's see what that does.  In case you are wondering, the "-v" on the end of the ybin command just runs it in verbose mode, meaning it will print more information on screen than it would regularly--helpful for pinpointing problems.

---

### Post by rrrrob on 2010-07-30
First thanks for the reply,

I've switched everything in the yaboot.conf back to original except for the line
"boot=/dev/sda3"

The following is what happened when I tried to run ybin
root@tty1:/mnt/Linux/etc# ybin -b --boot /dev/sda2 -v
ybin: unrecognized option '/dev/sda2'
Try 'ybin --help' for more information.

So out of curiosity I tried the following
root@tty1: /mnt/Linux/etc# cd 
root@tty1:~# ybin -b --boot /dev/sda2 -v
ybin: unrecognized option '/dev/sda2'
Try 'ybin --help' for more information
root@tty1:~#

Same result

After looking into the ybin --help......  should I be using "ybin -b /dev/sda2
Looking at the sample code at the end of the definition hda2 is sda2 in my case and they do not have the
"--boot" listed.  Or, could it be "ybin -b, --boot /dev/sda2" because they show a coma in the --help?

Thanks again for all the help
Rob

---

### Post by rrrrob on 2010-08-01
I can't seem to get around this error

root@tty1:/mnt/Linux/etc# ybin -b --boot /dev/sda2 -v
ybin: unrecognized option '/dev/sda2'
Try 'ybin --help' for more information.

and to review the drive is partitioned like such

sudo fdisk -l /dev/sda
sudo: unable to resolve host finnix
/dev/sda
# type name length base size system
/dev/sda1 Apple_partitio_map Apple 63 @ 1 (31.5k) Partition map
/dev/sda2 Apple_Bootstrap untitled 2048 @ 2048 (1.0m) NewWorld bootblock
/dev/sda3 Apple_UNIX_SVR2 untitled 68679680 @ 4096 (32.7G) Linux native
/dev/sda4 Apple_UNIX_SVR2 swap 3037184 @ 68683776 (1.4G) Linux swap
/dev/sda5 Apple_free Extra 1984 @ 64 (992.0k) Free space
/dev/sda6 Apple_free Extra 860 @ 71720960 (430.0k) Free space

Block size=512, Number of Blocks=71721820
DeviceType=0x0, DeviceId=0x0

After reading the -help and the man for ybin I think I understand what pkmgarf was heaving me do but for some reason it still isn't working. Is it possible that I need to reformat the drive from the command line of the live cd?  If so I don't know how.  I don't know the commands and steps to do format using the command line.  My guess is starting from the purest clean install would be a good idea at this point sense this yin step  is not working?

---

### Post by svtguy88 on 2010-08-02
Sorry for the delay.  I've been working a whole bunch lately.  I found a post on a YDL forum that had the ybin command like this "ybin -b boot=<device patch>"  So, make sure your yaboot.conf file is how it should be and try this....

```
***correct code below***
```

Let's give that a go.  I can't really try and figure out the syntax myself, as I'm actually trying to rescue my own linux install right now (kernel install gone bad)...



****EDIT***

Alright, I've got my Linux install back.  Funny enought, it involved me using the ybin command we need here.  Run this, and you should have yaboot installed and updated on your boot partition:

```
ybin -b /dev/sda2 -v
```

---

### Post by rrrrob on 2010-08-02
pkmgarf, thanks for the response,

I believe that is one of the command strings I tried, but I can't remember the error I got when I used it.  I'm pretty sure it was different than the one above, but I can't remember what it was.  I won't have access to that machine until next sunday.  I'll give it a try try then.  I do know that all the different error messages were either telling me one of two things.  Either it didn't recognize the command or it didn't recognize the drive.  Thus why I'm afraid there may still be another issue.  I'll give it a try and respond back Sunday when I have access back to the system.

Thanks again
Rob

---

### Post by imrazor on 2010-08-02
> **rrrrob said:**
> pkmgarf, thanks for the response,
 
I believe that is one of the command strings I tried, but I can't remember the error I got when I used it. I'm pretty sure it was different than the one above, but I can't remember what it was. I won't have access to that machine until next sunday. I'll give it a try try then. I do know that all the different error messages were either telling me one of two things. Either it didn't recognize the command or it didn't recognize the drive. Thus why I'm afraid there may still be another issue. I'll give it a try and respond back Sunday when I have access back to the system.
 
Thanks again
Rob
 
Sorry I've been gone for a while, but it's been a busy few days. I've skimmed over the conversation so far, and it *seems* like you're going to need to chroot your Ubuntu environment while rescuing it from Finnix. In fact, it would probably work better if you booted off the Ubuntu server CD and tried to rescue it from there, but I'm not familiar with the Ubuntu server LiveCD environment.
 
Forgive me if I'm not precise in this discussion, but I don't have a Linux environment handy. What you'll want to do is boot off your Finnix CD, and mount your Linux partition as /mnt/linux, as has been already discussed. Once you've done that you'll need to:
 
# mount --bind /dev /mnt/linux/dev
# chroot /mnt/linux
 
This will then give you a root prompt as if you were logged into a live Ubuntu server environment with a basic shell. At that point you should be able to run the basic ybin command that pkmgarf gave you earlier. It may not work though, since you trying to load Ubuntu's ybin in a Finnix environment. Let us know how it goes.

---

### Post by svtguy88 on 2010-08-04
chroot was to by my next suggestion.  I don't see why running ybin from Finnix shouldn't work though, as the Finnix live CD uses yaboot (you get the familiar "boot:" prompt when booting the disc).

---

### Post by rrrrob on 2010-08-09
Hello,  sorry it took so long to reply back,  just got access back to the system.

The following are the steps I just completed and their results.

Start system from the Finnix LiveCD
result-  boot:
type-   finnix Mem=1024m video=ofonly
result- root@tty1~#
type-   mkdir /mnt/Linux
result- root@tty1~#
type-   mount -t ext4 /dev/sda3 /mnt/Linux
result- root@tty1~#
type-   cd /mnt/Linux/etc
result- root@tty1:/mnt/Linux/etc#
type-   nano yaboot.conf
result-   GNU 2.0.9 file:yaboot.conf
(Make necessary changes)
type-   control-x
type-   y (to save changes)
result-   root@tty1:/mnt/Linux/etc#
type-   ybin -b /dev/sda2 -v
result-   (the following error)


ybin: Warning: no /etc/yaboot.conf, running yabootconfig to make one
yabootconfig: Could not determine root partition, aborting…
ybin: yabootconfig failed, please supply a valid /etc/yaboot.conf
ybin: You may also use yin's --boot, --image, --partition, and --device switches
ybin: These switches will cause ybin to generate a base yaboot.conf on the fly
root@tt1:/mnt/Linux/etc#


My first reaction was ?????

I thought I should post these results and see if the next steps should be those suggested by imrazor or if these results pointed to something else.  I'm grateful for both of your help, and I'm not questioning any of the steps.  It's obvious your knowledge of this is far greater than mine.  I just don't want to jump ahead and leave out important information, which might cause additional challenges.

Thanks again for your help
Rob

---

### Post by svtguy88 on 2010-08-09
Alright, it looks like everything is going as planned right up until the ybin command.  You are editing the configuration file for the yaboot bootloader (with the command "nano /etc/yaboot.conf").  However, in order for your changes to take place, the bootloader image needs to be re-written to the boot partition.  Running the ybin command does this.

Usually, you run ybin from a running sytem, and it updates the bootloader no problem.  The reason you can't simply run "ybin" without any additional options or parameters and have everything work out is because you are booted of of the Finnix live CD.  The Finnix live CD environment doesn't know where you have your yaboot.conf file stored, so it doesn't know what image to write to the boot partition that you specified in your command ("dev/sda2/").  This is why you are getting the error that complains about not having a yaboot.conf file, and eventually dumps you back to the Finnix command line.

Now, to fix this, there are two solutions.  You can either simply add another parameter to the ybin command we are issuing, specifying where the yaboot.conf file is located.  Or, you can use a command called "chroot," to essentially switch from the Finnix live CD environment into your own (installed) system that we are trying to rescue.


I *think* that both of the solutions I give here should work, rewriting your bootloader with the necessary changes.  Pick one of the following codes, and try it (after booting to Finnix and mounting your Linux partition as described earlier).  If it doesn't work, let me know the output and try the other...let's get your system up and running!

By adding the "C" flag after the "ybin" command, you can specify where your yaboot.conf file is located.  Here is the extended ybin command:
```
ybin -b /dev/sda2 -C /mnt/Linux/etc/yaboot.conf -v
```

Otherwise, you can try "chroot" to run the "ybin" command as if you were logged in to your installed system (and not the Finnix CD).  This would looks something like this:

```
chroot /mnt/Linux ybin -b /dev/sda2 -v
```

As I think I said before, the "v" flag on the "ybin" command just makes it run in verbose mode, outputting more/helpful errors.

By the way, sorry for the long reply.  I just think it's more helpful to explain to new users what is going on and why they are getting errors rather than handing out a string of commands to fix their problem.

---

### Post by rrrrob on 2010-08-09
Hello and thank you for the reply

Long explanations are fine with me, I'm trying to understand and learn what is going on with this system.  That was the point of doing this in the first place.

My lack of experience with Linux is far far greater than my over all experience.  My first system was a ti99.  It's hard to believe this is my first Linux system install.  Until now I never bothered to take the time.  So I greatly appreciate your helping an old dog learn a new trick as they say.

Ok…  this is what happened

command prompt-   root@tty1:/mnt/Linux/etc#
typed-   ybin -b /dev/sda2 -c /mnt/Linux/etc/yaboot.conf -v
returned-
ybin: unrecognized option `-c`
Try `ybin --help` for more information.
root@tty1:/mnt/Linux/etc#

Should it be
typed-   ybin -b /dev/sda2 -cd /mnt/Linux/etc/yaboot.conf -v

for change directory?

---

### Post by rrrrob on 2010-08-09
Never mind about the -c or -cd.  Figured out it was lowercase c upper case C issue

---

### Post by svtguy88 on 2010-08-09
^^^Yep..."C" not "c"

Welcome to linux.  So...does it boot is the question...?

---

### Post by rrrrob on 2010-08-09
Ok after entering
ybin -b /dev/sda2 -C /mnt/Linux/etc/yaboot.conf -v

I received the following in return
ybin:  Finding OpenFirmware device path to `/dev/sda2`&#8230;
ofpath:  /proc/scsi/scsi does not exist
ofpath:  Make sure you compiled your kernel with CONFIG_SCSI_PROC_FS=y
ybin:  Unable to find OpenFirmware path for boot=/dev/sda2
ybin:  Please add ofboot=<path> where <path> is the OpenFirmware path to /dev/sda2 to /mnt/Linux/etc/yaboot.conf
root@tty1:/mnt/Linux/etc#

---

### Post by svtguy88 on 2010-08-09
Hmmm...I just reread the thread and realized that you are using SCSI hard drives that are attached to some sort of a PCI SCSI controller.  

The error is saying that the ybin command cannot find the OF (Open Firmware) path to the boot device.  This is most likely because the kernel that Finnix uses doesn't really support your SCSI hard drive or its PCI controller card.  I don't really get that though, as you are able to mount, access and write your Linux partition, which would imply that the kernel DOES support your hard drive...

Okay, let's try the other method---use the "chroot" command I gave you after mounting /dev/sda2 to /mnt/Linux.  I don't know if you will be able to update the bootloader using that method either, as if this is an issue with the kernel (--if the kernel that Finnix boots does not support your SCSI drive, I don't think that even chroot'ing will make the command work)...but it's worth a try.

Otherwise, your options are to find the OF path to the device and add it to the "ybin" command as another parameter, or boot from a kernel that supports your SCSI device.  If you want to do the second, you could try booting the Ubuntu LiveCD (if it works for you) or a rescue CD (I think Ubuntu has one, and so does Debian...just make sure you download a semi-recent PPC one).  The rescue CD will give you a Finnix-like prompt, but will likely use an updated kernel that supports your SCSI drive.  Just retry the steps we've been doing (saving the edited yaboot.conf to the bootloader using "ybin -b [device] -C [path-to-yaboot.conf] -v") using the rescue CD.

---

### Post by rrrrob on 2010-08-10
The following are the steps I took and their results...  

boot:
boot: finnix Mem=1024m video=ofonly
root@tty1:~#
root@tty1:~# mkdir /mnt/Linux
root@tty1:~# mount -t ext4 /dev/sda3 /mnt/Linux
cd /mnt/Linux/etc
root@tty1:/mnt/Linux/etc#
root@tty1:/mnt/Linux/etc# nano yaboot.conf
**** GNU 2.0.9 file:yaboot.conf  ****
(make changes)
*******************  GNU 2.0.9  file: yaboot.conf  *******************
boot=/dev/sda3
device=/pci@f2000000/pci-bridge@d/ATTO,ExpressPCIProUL3D@4,1/@0:
partition=3
root=/dev/sda3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/yaboot
enablecdboot

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash Mem=1024m video=ofonly"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash Mem=1024m video=ofonly"

************************************************************************
control-x
Y (save changes)
root@tty1:/mnt/Linux/etc# chroot /mnt/Linux/ ybin -b /dev/sda2 -v
ybin:  /dev/sda2:  No such file or directory
ybin:  /proc filesystem is not mounted, nvram will not be updated
root@tty1:/mnt/Linux/etc#


I've also searched for an Ubuntu 10.4 LTS (Lucid Lynx) LiveCD that works with this system and I didn't see one that I thought would work.  This is what I found 
[http://mirror.mcs.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/lucid/release/](http://mirror.mcs.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/lucid/release/)

Just to clarify my thoughts.  The finnix system is seeing /dev/sda3 because it is showing the yaboot.conf file from that partition, correct?

but for some reason it can not see the /dev/sda2 partition, is that correct?

also, aren't the lines in the yaboot.conf file "boot=", "device=", "partition=", and "root=" all pointing to the area of the yaboot.conf file of the /dev/sad3 partition?

Is there any way to view the contents of the /dev/sda2 partition in order to verify that the files we're assuming are there actually are?

---

### Post by imrazor on 2010-08-10
> **rrrrob said:**
> The following are the steps I took and their results... 
root@tty1:/mnt/Linux/etc# chroot /mnt/Linux/ ybin -b /dev/sda2 -v
ybin: /dev/sda2: No such file or directory
ybin: /proc filesystem is not mounted, nvram will not be updated
root@tty1:/mnt/Linux/etc#

Before you run "chroot" you need to mount the /dev filesystem, otherwise ybin will not be able to locate your hard drives. It should look like this, though pkmgarf may have a better suggestion:
 
# mount --bind /dev /mnt/Linux/dev 
 
Given the error message about the /proc filesystem it's also possible you might have to run this before chroot:
 
# mount --bind /proc /mnt/Linux/proc
 
However, I'd try running the mount --bind /dev /mnt/Linux/dev first. Running it for /proc may or may not be necessary.

---

### Post by linuxopjemac on 2010-08-10
chroot:
[http://mac.linux.be/content/chroot-system-livecd](http://mac.linux.be/content/chroot-system-livecd)

---

### Post by svtguy88 on 2010-08-10
Ooops, yeah try the other chroot commands.  I was able to run ybin from the Finnix prompt on my system (without chroot), so I wasn't too sure on those commands.

---

### Post by rrrrob on 2010-08-10
I'm going to let my NewB-ness show again, because I'm a bit confused.

Sense the yaboot.conf file in /dev/sda3 is already modified and comes up with the changes I made correctly every time I no longer have to go threw all the steps leading up to making changes to the yaboot.conf file do I?

thus steps should now be?
root@tty1~# mount --bind /dev /mnt/Linux/proc

or do I need to follow all of the steps and thus the command line should be?
root@tty1:/mnt/Linux/etc# mount --bind /dev /mnt/Linux/proc

also doesn't /dev need some sort of direction like?
root@tty1:/mnt/Linux/etc# mount --bind /dev/sda2 /mnt/Linux/proc

From linuxopjemac's message, this really has me confused

ubuntu@ubuntu:~$ sudo mkdir /mnt/root
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda4 /mnt/root
ubuntu@ubuntu:~$ sudo mount -t proc none /mnt/root/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/root/dev
ubuntu@ubuntu:~$ sudo chroot /mnt/root /bin/bash

I'm asking because I'm making the assumption that I could really screw things up if I just enter commands that aren't correct.

currently the system has the following command line

root@tty1:/mnt/Linux/etc# chroot /mnt/Linux/ ybin -b /dev/sda2 -v
ybin: /dev/sda2: No such file or directory
ybin: /proc filesystem is not mounted, nvram will not be updated
root@tty1:/mnt/Linux/etc#

---

### Post by svtguy88 on 2010-08-10
You are correct, partially.  You do not need to edit the yaboot.conf file any more.  The .conf file has been changed, and now we are simply trying to write those changes to the bootloader (sda2).  

You need to mount your system (using the mount command you should know and love by now--"mkdir /mnt/Linux" "mount -t blahblahblahblah"), which is equivalent to linuxopjemac's "sudo mkdir /mnt/root" command on the page he linked.  

Then you need to issue these commands (same commands linuxopjemac listed, just with folder names specific to your setup--/mnt/Linux instead of /mnt/root) after mounting your system:

```
mount -t proc none /mnt/Linux/proc
mount -o bind /dev /mnt/Linux/dev
```

This basically populates the /mnt/Linux/proc and /mnt/Linux/dev (your installed system's folders)   with the data from /proc and /dev (the system folders being used by the Finnix CD).

From here, you should be able to run the ybin command we have been working with:

```
chroot /mnt/Linux/ ybin -b /dev/sda2 -v
```

---

### Post by rrrrob on 2010-08-10
I think I'm following...

Here is what I typed and the results

boot: fin nix Mem=1024m video=ofonly
root@tty1:~# mkdir /mnt/Linux
root@tty1:~# mount -t ext4 /dev/sda3 /mnt/Linux
root@tty1:~# mount -t proc none /mnt/Linux/proc
root@tty1:~# mount -o bind /dev /mnt/Linux/dev
root@tty1:~# chroot /mnt/Linux/ ybin -b /dev/sda2 -v
ybin:  Finding OpenFirmware device path to '/dev/sda2'...
ofpath:  /dev/sda:  Decice not configured
ybin:  Unable to find OpenFirmware path for boot=/dev/sda2
ybin:  Please add ofboot=<path> where <path> is the OpenFirmware path to /dev/sda2 to /etc/yaboot.conf
root@tty1:~#

?  I get from this that I have edit the yaboot.conf file?

---

### Post by svtguy88 on 2010-08-11
Well, the chroot command ran correctly, but the system still can't find the ofpath of your drive.  I really don't know why...I thought Finnix had SCSI support for pretty much everything.

The only thing I can think of trying is booting off of a Debian installer DVD, as long as the machine has a DVD drive.  You can download it [here]("http://www.debian.org/CD/http-ftp/#stable").  

Once you are booted off the DVD, it will look like it is installing (or about to install) Debian on your computer, but don't worry, it's not doing anything to your system yet.  Go through the first few steps of the installer.  I think it's when you get to the screen asking about partitioning disks and whatnot that you can press "ESC" and it will give you a menu that lets you pick different parts of the installer to go to.  Go down to "drop to shell" or something like that.  Basically it gives you a command prompt.

Now, mount your drive again, run the chroot commands and see what happens.  Fingers crossed...

**edit**

Just for laughs, give this command a go.  You can add the open firmware path to the ybin command, specifying the exact location to install the bootloader.  I looked at your earlier post, and yaboot.conf lists your drive as (device=/pci@f2000000/pci-bridge@d/ATTO,ExpressPCIProUL3D@4,1/@0:
partition=3).  I think "/pci@f2000000/pci-bridge@d/ATTO,ExpressPCIProUL3D@4,1" is the ofpath to your drive.  However, it points to partition number 1, which is essentially the drive itself.  I believe that changing that 1 to a 2 will specify the boot partition.  So, this command (after mounting your drive and running the /proc and /dev chroot commands) may be just the tickiet....

```
chroot /mnt/Linux/ ybin -o /pci@f2000000/pci-bridge@d/ATTO,ExpressPCIProUL3D@4,2 -v
```

---

### Post by rrrrob on 2010-08-11
This has to be close...

Here is what I typed and the results

boot: finnix Mem=1024m video=ofonly
root@tty1:~# mkdir /mnt/Linux
root@tty1:~# mount -t ext4 /dev/sda3 /mnt/Linux
root@tty1:~# mount -t proc none /mnt/Linux/proc
root@tty1:~# mount -o bind /dev /mnt/Linu/dev
root@tty1~# chroot /mnt/Linux ybin -o /pci@f2000000/pci-bridge@d/ATTO,ExpressPCIProUL3D@4,2 -v
ybin:  /dev/sda3 appears to be mounted! Aborting.
root@tty1:~#

So we're now seeing the drive, but not the correct partition?

---

### Post by svtguy88 on 2010-08-11
I'm not sure where to go from there.  The ofpath looks like it points to partition 2, but the error says otherwise...

---

### Post by svtguy88 on 2010-08-12
Your two choices, as I see them, are to either try booting a Debian (or other) disc, dropping to a shell (command prompt) and trying to mount your drive and update yaboot with the chroot ybin command....


Or you can try booting to open firmware (cmd + opt + O + F on bootup) and looking for the open firmware device path there.   This would invlovlve something like issuing the command "ls /" and looking for your SCSI controller and its discs in the list that the terminal will output.  Somewhere in there will be the device address you need...

I still don't see why the one you tried won't work.

---

### Post by rrrrob on 2010-08-13
First I'm not giving up on this....  but I am going to try something else.  This unit will support ATA drives as well from a connection port on the mother board.  So I'm going to get one and see if I use that configuration to get this to work.  This will eliminate the special ATTO card all together.

---

### Post by svtguy88 on 2010-08-14
Booting off of a ATA drive (using the standard connector on the motherboard) will alleviate your problems, more than likely.  Everything appears to be configured correctly.  We just need ybin to update the boot partition.  If you reinstall to an ATA drive, I wouldn't be surprised if it simply boots as expected, or just requires some xorg.conf tweaking.  

The Debian CD is still an option.  Why not utilize the hard disk space you already have, if possible?  I can chroot from my Debian net install disc (small enough to fit on a CD).  You could download that, or the DVD I listed earlier and run the chroot command and see what happens.

---


---
title: "Dual Boot Xubuntu and OS 9?"
date: 2008-07-10
forum: Apple Hardware Users
---

### Post by Jitanjafora on 2008-07-10
Hi all,

I'm a Linux newbie, and I have been trying different flavors of it. I want to set up a G3 Lombard to dual boot Xubuntu Hardy and OS 9.2.2. I can install either program, but I cannot switch between the two of them. Yaboot does not recognize my OS 9 partition as a bootable system: it's either Xubuntu or a CD.

Xubuntu 8.0.4 runs really sweet with all the upgrades, so that's not a problem.

Any help will be appreciated.

---

### Post by tiresia on 2008-07-10
Have you tried pressing the option key when the computer starts?

---

### Post by Jitanjafora on 2008-07-10
> **tiresia said:**
> Have you tried pressing the option key when the computer starts?

Hi tiresia,

Yes, to no avail. For what I have found out, although the Lombard is the first NewWorld PowerBook, does not support Startup Manager.

Thanks!

---

### Post by tiresia on 2008-07-10
Sorry for my stupid question: are you sure, that you didn't erase the macos9 partition?
What do you get if you type in a terminal```
df -h
```

---

### Post by Jitanjafora on 2008-07-10
> **tiresia said:**
> Sorry for my stupid question: are you sure, that you didn't erase the macos9 partition?
What do you get if you type in a terminal```
df -h
```

Hey, thanks for the prompt response.

I ended up reformatting the whole drive and installing Panther and OS 9, so I cannot try that right now. But no, the OS 9 partition wasn't erased then. First I formatted the drive, and allocated free space for Xubuntu (I'm told is the easiest way) and installed it there, and ran all the upgrades. Then I booted from the OS 9 CD and installed OS 9 in the designated partition.

---

### Post by spencercarran on 2008-07-10
I didn't know OS9 still existed. Is it possible for you justto go to Xubuntu exclusively?

---

### Post by Jitanjafora on 2008-07-11
> **spencercarran said:**
> I didn't know OS9 still existed. Is it possible for you justto go to Xubuntu exclusively?

Believe it or not, OS 9 is alive and well, and still productive. Going to Xubuntu exclusively is always a possibility, but that would be a different project, and besides I like challenges.

My 17" G4 PowerBook (which I got for a song after selling my 15.4" Santa Rosa MacBook Pro --call me crazy) dual boots Leopard and Ubuntu Hardy Heron without missing a blink. My Pismo dual boots Tiger and OS 9, and used to boot Xubuntu Dapper as well, but I didn't like Dapper that much, and I always got a scrambled screen when upgrading it to Hardy...

---

### Post by tiresia on 2008-07-11
> **Jitanjafora said:**
>  Then I booted from the OS 9 CD and installed OS 9 in the designated partition.

If you install OS 9 after the installation of Xubuntu, yaboot can't know that you have another OS!
Either you install OS 9 *before* Xubuntu, or you must edit the configuration of Yaboot (/etc/yaboot.conf)

---

### Post by Jitanjafora on 2008-07-11
> **tiresia said:**
> If you install OS 9 after the installation of Xubuntu, yaboot can't know that you have another OS!
Either you install OS 9 *before* Xubuntu, or you must edit the configuration of Yaboot (/etc/yaboot.conf)

Hey, thanks for the tip. How can I edit Yaboot? (Please bear with me. I'm a newbie.)

---

### Post by tiresia on 2008-07-11
Can you please post what you see when you type

```
cat /etc/yaboot.conf
```

---

### Post by Jitanjafora on 2008-07-11
> **tiresia said:**
> Can you please post what you see when you type

```
cat /etc/yaboot.conf
```

Hi tiresia,

I have not gotten around to reinstall Xubuntu yet.

There's a caveat: the DVD drives I have do not boot the Lombard from pressing C at startup, only from software, so I cannot install OS 9 before Xubuntu. Yaboot will let me boot from the OS 9 CD (or any other system CD or DVD), but I cannot boot a Xubuntu CD from OS 9.

If you could give me some general pointers, I would be even more grateful. 

Thanks!

---

### Post by tiresia on 2008-07-11
Sorry, but I do not understand what you mean. 

I guess, that you can start your Lombard with your OS 9 CD Installer by pressing C. 
Before you install OS9 you can make with the Apple Disk Utility two Partitions, the first one must be unformatted.
You should format only the second partition with HFS+, in order to install OS9.
When your are finished with the OS9 Installation, you can boot Xubuntu (again pressing C).
Here you can choose to install with the Option "Guided - Use free space"
The Xubuntu Installation will end up by detecting the other OSs you have on your computer and installing Yaboot.

I don't understant why you tell that you cannot install OS9 before Xubuntu. Or am I missing anything?

---

### Post by Jitanjafora on 2008-07-11
OK. Let me go back again. The 333MHZ Lombard, which is the model I have, did not have DVD capabilities originally, so it shipped with a CD, and could be booted from it via keyboard. Later, aftermarket DVD decoder cards (PCMCIA interface) and DVD drives were made available, but these DVD drives are not bootable by pressing C, only if you chose to boot from them using software (Startup Disk or Yaboot).

I only have DVD drives (3 of them, in fact). 2 of them boot my Pismo by pressing C, but none of them boot in the Lombard.

If I install Mac OS 9 first, I won't be able to boot a Xubuntu CD. If I install Xubuntu first, I'll be able to install Mac OS 9 --since yaboot lets me boot from CD--, but my Xubuntu installation won't recognize my Mac OS 9 installation.

Of course I could save myself the trouble and install Xubuntu in my Pismo, but I already did. I had a perfectly set up triple boot system, but for some mysterious reason the Pismo won't go past Dapper. Any attempt to upgrade to Hardy Heron resulted in a scrambled screen (which might be fixable, but I don't have the know-how, either).

Uf! That was long-winded, but I just wanted you to get a clearer view of the conundrum I'm facing...:)

---

### Post by Jitanjafora on 2008-07-11
> **spencercarran said:**
> I didn't know OS9 still existed. Is it possible for you justto go to Xubuntu exclusively?

By the way, I just got what you meant. I have not been referring to OS9, but to Mac OS 9, which is a completely different operating system. I highly doubt OS9 is still around, too...

---

### Post by tiresia on 2008-07-11
Ok, thanks for your explanation, I see now where is the problem
You have two ways:

1. Can you start Xubuntu installer from the Apple Startup Disk? - I guess you can, otherwise how did you install Xubuntu? If so, then install OS9 as I explained before (two Partitions, the first unformatted for Xubuntu). When you are finished with the OS9-Installation, you can start Xubuntu and install it with the option "Guided- free space"
(you don't even need to restart in OS9: in the OS9-Installer you have the Startup Disk)

2. If you install Xubuntu first, then you must edit your /etc/yaboot.conf - as I told you in my first post. You must know where is your MacOS9. If you follow what I suggested, your partition table will look like this:

/dev/hda1	Apple_partition_map
/dev/hda2	Apple_Bootstrap
/dev/hda3	Xubuntu (Linux native)
/dev/hda4	swap
/dev/hda5	MacOS9 (hfs+)

In doubt you can check with:

```
sudo fdisk -l
```

Now you must tell to yaboot, in which partition is your MacOS9

```
sudo nano /etc/yaboot.conf
```

You will see a line: 'enablecdboot'
After that line, if OS9 is in /dev/hda5 you can add:

```
macos=/dev/hda5
```

You can exit (^X) and say yes to save.

Now update the yaboot bootloader onto your bootstrap partion

```
sudo ybin
```


(You could also try to start from CD with an OpenFirmware command, but it is not so easy...)

---

### Post by Jitanjafora on 2008-07-11
Hi tiresia,

Thanks a lot for the walkthrough. It was very thorough.

The way I installed Xubuntu, I wiped the hard drive, and partitioned it using Disk Utility in the Panther OS install CD. The Lombard looks for an operating system in the HD first; if it does not find any, then it boots from the CD. That's how I got the Xubuntu CD to load. It does not load from the Apple Startup Disk menu.

I have a newbie question, though. How do you get the "^" symbol in Terminal?  What key(s) you have to use?

Thanks so much again! You're the greatest! :-)

---

### Post by tiresia on 2008-07-11
Sorry, this "^" symbol is just "Control"

Note:
"In nano's help texts the Ctrl-key is represented by a caret (^), so Ctrl+W is shown as ^W, and so on. The Alt-key is represented by an M (from "Meta"), so Alt+W is shown as M-W."

"If you want to save the changes you've made, press Ctrl+O. To exit nano, type Ctrl+X. If you ask nano to exit from a modified file, it will ask you if you want to save it. Just press N in case you don't, or Y in case you do. It will then ask you for a filename. Just type it in and press Enter."

---

### Post by Jitanjafora on 2008-07-12
Hi tiresia,

Just a follow-up to let you know that, instead of wiping the HDD once more and starting from scratch, I picked up your suggestion of starting from OF (which, in my encyclopedic ignorance, I hadn't thought of before). I looked it up, followed the instructions, and it worked! (Using an external USB keyboard, mind you, not the Lombard's, but that's a mystery to solve later.) I'm installing Xubuntu even as we speak.

Thanks a lot again!

---

### Post by tiresia on 2008-07-13
I'm glad, that you are able to configure your computer with dual boot
May be you will find this document interesting. 
[https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot](https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot)
It explains also, why it is better to have the Bootstrap Partition at the beginning of the Partition Map

---

### Post by Jitanjafora on 2008-07-14
Hi tiresia,

You're my hero! I cannot thank you enough for all the useful info. 

Now that I'm triple-booting the Lombard, I'm going to try using what you have taught me to set up MacOs as one of the options in yaboot. I'll keep you posted, or I'll holler for help.

Thanks!

---

### Post by wsteffen on 2009-11-29
I have been trying to get a iMac g3 to be used as a triple boot system.
(OS9,OSX & Xubuntu linux for PowerPC) The problem is that the install
process for Xubuntu calls a partitioner program I could not get around.
This partioner program for some reason distroys somthing in the first
eight partitions which the Apple OSs need. The install process should
not require this if there correct partitions are setup with the OS9
"Drive Setup" program! I proved that this the case with the procedure
outlined here.

In doing some research on line I found the link I thought was what
I needed:

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
                      YabootConfigurationForMacintoshPowerPCsDualBoot

In which I found the following:
"To fix this, start up from the Mac OS 9 install CD and open
/Utilities/Drive Setup. Select the hard drive where your Mac OS 9
partition is, and select "Update Driver" from the "Functions" menu."

Well my OS9 cd has a version of Disk Setup that does not have a
"functions" menu.

Below is my partition map that I set up for testing a triple boot
setup. It is the output of the mac-fdisk program found in the Xubuntu
distribution of Linux for the PowerPC. (use the p option) It is what
I set up using my version of the "Drive Setup" program, that comes
in OS9.

        #                      name             length   base      ( size ) system
/dev/hda1  Apple_partition_map Apple                63 @ 1         ( 31.5k) Partition map
/dev/hda2  Apple_Driver43      Macintosh            54 @ 64        ( 27.0k) Driver 4.3
/dev/hda3  Apple_Driver43      Macintosh            74 @ 118       ( 37.0k) Driver 4.3
/dev/hda4  Apple_Driver_ATA    Macintosh            54 @ 192       ( 27.0k) Unknown
/dev/hda5  Apple_Driver_ATA    Macintosh            74 @ 246       ( 37.0k) Unknown
/dev/hda6  Apple_FWDriver      Macintosh           200 @ 320       (100.0k) Unknown
/dev/hda7  Apple_Driver_IOKit  Macintosh           512 @ 520       (256.0k) Unknown
/dev/hda8  Apple_Patches       Patch Partition     512 @ 1032      (256.0k) Unknown
/dev/hda9  Apple_HFS           untitled        5406490 @ 1544      (  2.6G) HFS
/dev/hda10 Apple_HFS           untitled 2     30978660 @ 5408034   ( 14.8G) HFS
/dev/hda11 Apple_HFS           untitled 3     30978660 @ 36386694  ( 14.8G) HFS
/dev/hda12 Apple_UNIX_SVR2     A/UX Root      41207530 @ 67365354  ( 19.6G) Linux native
/dev/hda13 Apple_UNIX_SVR2     Swap            4383598 @ 108572884 (  2.1G) Linux swap
/dev/hda14 Apple_UNIX_SVR2     Unreserved 1   60642383 @ 112956482 ( 28.9G) Linux native
/dev/hda15 Apple_HFS           untitled 7     20749790 @ 173598865 (  9.9G) HFS
/dev/hda16             Apple_Free Extra                1022913 @ 194348655 (499.5M)  Free space

Block size=512, Number of Blocks=195371567
DeviceType=0x0, DeviceId=0x0
Drivers-
1: @ 64 for 23, type=0x1
2: @ 118 for 36, type=0xffff
3: @ 192 for 21, type=0x701
4: @ 246 for 34, type=0xf8ff

Partitions 14, 15, & 16 I created for additional testing. (MsDos file
exchange partition, an install of NetBSD, or what ever.)

My procedure is as follows:

I booted the iMac with the OS9 cd that came with the system and went to
utilities/Drive Setup.  There I setup the partitions as shown above. The
utility allows you to set the number of partitions (in addition to the first
eight required by OS9 ) as well as size, name and usage of each partition.
I then installed OS9 on partition /dev/hda10 (untilted 2 ). When it
completed, I  tested booting from that installation. It booted OK.
I then booted from the Xubuntu desktop ppc disk. While running from the cd
& before starting the install, I did a copy of the first 1550 blocks of the
disk to a USB flash drive for safe keeping. This saved the first 8
partitions plus a few extra blocks. The command I used was:

      dd if=/dev/hda of=/media/disk/mac-image count=1550

/media/disk is the USB flash drive. I presume I could have used /dev/hda16,
but I have not yet tried that.
Next I did the install, which started up "the disk partitioner" in which
the "use" & mount points are required. Also the boot partition needs to be
specified, which partition 9 was reserved for when I did the original
"Drive Setup" in OS9. It will also allows for resizing and other things
that I avoided. I used partitions 12 & 13 for what their names imply in
the table above. I then completed the install and booted Xubuntu from the
hard disk. It booted OK. I then tried booting OS9 again - it would not boot.
It started but ended with the floppy image with the flashing question mark.
Sooo... I booted Xubuntu from the hard disk again and started a terminal
window. I did a "sudo su" to to get admin privileges (root user) and
inserted ths USB flash drive (it mounts automatically). I then did the
following:

  dd if=/media/disk/mac-image of=/dev/hda count=1543

The count I used should have gotten all of the first eight partitions.
After that I was able to boot both OS9 and Xubuntu from the hard disk.
I have the open firmware parameters set on my system to go to a command
prompt when starting up, so I use the following commands to boot manually:

        OS9 = boot hd:10,\\:tbxi
        Xubuntu = boot hd:9,\yaboot  (hd9 is the boot partition )

I then loaded OSX from the cd and installed on partition hda11 (untitled 3).
After that I could triple boot using the following:

        OS9 = boot hd:10,\\:tbxi
        Xubuntu = boot hd:9,\yaboot  (hd9 is the boot partition )
        OSX = boot hd:11,\\:tbxi

---

### Post by wsteffen on 2009-11-29
Sorry for the bad formating of the partition table in the last reply - it did not copy well, there should be well formated columns.

---


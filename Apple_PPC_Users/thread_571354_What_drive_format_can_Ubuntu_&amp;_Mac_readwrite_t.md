---
title: "What drive format can Ubuntu &amp; Mac read/write to?"
date: 2007-10-09
forum: Apple PPC Users
---

### Post by benerivo on 2007-10-09
Hi, I have Mac OS X and Ubuntu dual booting, and now want to make a partition in some free space that both OS's can read write to. I actually did this when I installed Ubuntu, and chose FAT32, but Mac OS X does not seem to recognise it.

What can I format this partition to? I tried formatting it as hfs, as i think this would work, but GParted would only allow the partition to be up to 2GB.

---

### Post by frog_pilot on 2007-10-09
I did it like this:

I booted into OS X. With the diskutility I created a HFS+Volume **without Journal**. I think, its called "macintosh extended" (without the add "Journaled"). On this volume writing from both OSes is safe.

To mount it in Ubuntu I added the following line to my /etc/fstab ```
# /dev/hdXX
UUID=xxxxxxxxxxxxxxxx /media/data     hfsplus    user,rw,auto,uid=0,gid=46,umask=002,nls=utf8        0       0

```

If you can change the userID in OSX to 1000 it will recognise both (the linux-user and the OSX user as one and you will have the same rights from both OSes). This procedure was too strange for me (you never know what will happen until you did it :confused: ). From Linux I created - with root privileges -  a folder on the drive. With ```
sudo chown <user>:<user> /media/<hfsvolume>/<newfolder>
``` I transferred it to my user, so I can write to this folder with actual privileges. The whole drive has the owner 501 (the default-userID in OSX). From within OS X you can ignore ownership.

Thats it!

---

### Post by benerivo on 2007-10-09
Thanks frog-pilot. Is this the volume you created with the above method, that you now have problems accessing when using MOL - in [this thread]("http://ubuntuforums.org/showthread.php?t=571355")?

---

### Post by frog_pilot on 2007-10-09
Yes exactly it is.

But I think the problems with mounting under MOL are because the drive is busy. It's already mounted in Linux. I havn't started yet MOL in a Terminal to see the output. But I think, when I unmount one of the Data-Sharing-Volumes in Linux they will come up after starting MOL when they are added to /etc/mol/molrc.osx. I will try it later.

I'm actually writing out of OS X, which I booted for the first time since about a week :KS to work on some things which do not run under ubuntu or even MOL.

Besides I have only good experiences with sharing data as described. I have one Volume for storing my music and one for video. The only problem I have is [this]("http://ubuntuforums.org/showthread.php?t=567995")! Thats why I plan to convert the music-volume to ext3 and will see if iTunes can work with this. If Amarok and iTunes could work together on a vfat-volume, I can't say. But I don't want to have vfat at all, except for 256 MB memory-sticks :lolflag: 

I have also good experiences with [http://sourceforge.net/projects/ext2fsx/]("http://sourceforge.net/projects/ext2fsx/"). With this tool I have access to my home- and root-partition. But I mounted my home-partition read only and never tried to write to it and for my boot-partition I prevented automounting on startup. You can configure this in OSX System-Properties. There will be added a new Icon in the others-section (like Adobe Version Cue).

But if I change my music-volume to ext3 I have to try it. I will report my progress :)

---

### Post by not.robb on 2007-10-11
I just got an external hard drive that I want to use for Music and Movies on OS/X and Ubuntu. Read/Writable from both OSes. 

I am not a hardware guy though, and the number of file systems is blowing my mind. If i read this correctly, it seems that ext3 might be the way to go --- yes?

---

### Post by frog_pilot on 2007-10-11
It might be a way.

More easier to handle might be FAT32/vfat. If you don't have files bigger than 2 GB, you could use this. You don't have to care about file  rights and this whole stuff.

But as you read, it's possible to  manage data for sharing with a more progressive file system. It's on you. Do you prefer the complex right management and journaled file storing, ext3 is your choice.

If you need this drive to share files with many people. Some using windows, some mac, some linux maybe vfat is more comfortable for your needs.

---

### Post by not.robb on 2007-10-11
Thanks Frog Pilot,
vfat sounds like it has everything i need. 

however: i formated the drive as Fat32 using GParted. When I plug the drive into the iBook, it says it's a volume that Mac OSX can't read. I'm sure there's something obvious that I'm missing... 

I'm running 10.3.9 on a PowerPC G4.
Thanks for helping out a filesystem newb.

---

### Post by frog_pilot on 2007-10-12
Try to format the drive with diskutility from OSX. There is am menue-entry lik "msdos-filesystem" or something similar. If you do so, the mac will recognize the drive and ubuntu will shurely do the same.

btw: do you have your ubuntu-installation on this G4 PowerMac you mentioned? I'm running ubuntu on a PowerMac G4 MDD (2x1.25 GHz, 2GB Ram + additional SUNIX USB 2.0 PCI-Card).

And I have a problem with the sound output. The signal from the internal sound card is very quiet (when I'm running ubuntu) in relation to the volume level when im running OS X.
It seems that the volume from the internal speaker is nearly equal in both OSes. But when I'm starting ubuntu I have to pump up the volume of my amp. The MAC-startup sound is loud but after it the volume will decrease extremely. Maybe its from the linux sound driver.

Did you mention similar problems?

---

### Post by not.robb on 2007-10-12
It worked! 

I formatted as fat32 in OS X and it now works properly under Ubuntu too. 

Sorry, I'm not running Ubuntu on a PPC, it's a separate pentium based desktop and I've never had a problem with volume...

Thanks again for your help!

---

### Post by myo on 2007-10-12
> **frog_pilot said:**
> 
...The signal from the internal sound card is very quiet (when I'm running ubuntu) in relation to the volume level when im running OS X.


might be a silly question, but have you set the volumes at all with any kind of mixer app? I know on my Powerbook, I need to use alsamixergui to set the DRC to 50%, PCM 1 to 90%, and master almost 100%, to get about the same levels as OS X. 

back on topic; if I just turn off the journaling on an hfs+ filesystem, is that the same as making a new partition in "macintosh extended" with the OS X disk utility? 

also, is there a way to make my ext3 partition bigger without effing anything up?

---

### Post by frog_pilot on 2007-10-13
> **myo said:**
>  I need to use alsamixergui to set the DRC to 50%, PCM 1 to 90%, and master almost 100%, to get about the same levels as OS X. 

I played with all alsamixer levels. When I set DRC to mere than about 65% it sounds overloaded - this means the sound-signal don't sounds clear, it sounds distorted as if it were to loud. But the signal on the output-jack is still very quiet. But thanks for your assistance. I will play with the mixer settings once more.

> **myo said:**
> back on topic; if I just turn off the journaling on an hfs+ filesystem, is that the same as making a new partition in "macintosh extended" with the OS X disk utility? 

also, is there a way to make my ext3 partition bigger without effing anything up? 

If you turn off journaling on hfs+ manually, it should work like formatted without journal. To turn journaling off, open a terminal in OS X and execute```
sudo diskutil disableJournal <mountpoint>
``` for Systemvolume "/". Any other drive is typically mounted in /Volumes/. For these drives you have to choose the name of the drive as shown on your desktop if mounted. Since volume-labels on Mac often contain space characters as in "Macintosh HD". I don't know the exact syntax for these cases. May be the, the diskutil command can understand these space characters. Somewhere I have seen that the space character can be replaced with "\ " backslash+space charakter, e.g. ```
sudo dikutil disableJournal Macintosh\ HD
```. But I don't even know how to create backslash with macintosh keyboard :).

AFAIK you can incrase ext3 volumes with gparted without any risk. But they have to be unmounted. Most suitable for this need will be a live-cd.

---

### Post by guidop on 2007-10-13
No backslash key?  What language is your keyboard?

In the above situation, if typing a backslash is inconvenient, you can also use quotes to make a space behave as a space, and not as a file separator.

The following commands would all be equivalent, in most shells:

```
sudo diskutil disableJournal Macintosh\ HD

sudo diskutil disableJournal "Macintosh HD"

sudo diskutil disableJournal 'Macintosh HD'

sudo diskutil disableJournal Macintosh" "HD

```

---

### Post by frog_pilot on 2007-10-14
My keyboard is german and I didn't found out how to create a backslash in OS X yet. :( embarrassing:lolflag:
But in ubuntu I got it working with "right alt"+?

---


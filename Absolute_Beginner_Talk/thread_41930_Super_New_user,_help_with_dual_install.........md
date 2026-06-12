---
title: "Super New user, help with dual install........"
date: 2005-06-15
forum: Absolute Beginner Talk
---

### Post by TristanMike on 2005-06-15
Hello all, thanks for viewing.  I am very new to Linux as in this is the first time I have ever seen it, but I'd like to give it a shot.  
System:  
AMD 2200+XP
1GB ram Dual Channel
80 GB HD IDE

Recently I reformated my computer and in preperation for the Ubuntu install I seperated the two drives during the XP install.  The first, listed as primary is about 60 GB, that's for XP, and the second 20GB, I left and did nothing, to install Ubuntu on.  After I was ready, I restarted my computer and changed to boot from CD and began the boot process.  I have gotten through the main menu up untill the point after Detect Hardware - the Partition Disks section, after which follows is Install the Base System.  It's the Partition Disks section that is giving me the issue.

When I choose this option, I get 4 choices and below that it says

IDE1 Master (hda*) - 80.1 GB Samsung.....
     #1 primary     62.9 GB (little shock arrow)   ntfs
     #2 logical       17.1 GB   
          pri/log         8.2 MB                                  Free Space

I want to install it on the 17.1GB sector but I don't want skip this step and proceed and have it over-write my XP installation.  Am I to put a file system on this drive and use THAT?  If so, which out of the list they give me?  Is FAT32 fine for this Ubuntu.  As you can see I am very new to this and if someone could help guide me through up to the point where the installation ACTUALLY happens or direct me somewhere that tells me how to do this it would be very appreciated.  I have have searched the fourms but nothing I have found has told me this.  

I also read, when I get the option to install the GRUB loader for the dual boot, but if is incorrect let me know as well please.

---

### Post by newbie_ubuntu on 2005-06-15
Hi,

U will need to format the remaining 20 GB into parts like / , /home, /usr, /local and others.
And the shock arrow u see is the bootable icon. U need to make root directory / the bootable one by clicking on the "bootable flag" option that comes when u are formatting a particular part of the drive. 
Also u need to specify a swap area.
ext3 is the format that u will need for all the linux parts. fat32 can be for a part of memory that u want both windows and linux to read.

I forgot exactly what I did when the grub install happened. I just used the default option and clicked "ok". Worked well for me.

---

### Post by TristanMike on 2005-06-15
That's awsome :-) , it's helping to clarify alot combined with the readings I've been doing.  I can't thank you enough, I so happy with my experience within this fourm and others :smile: .  Glad to see people really helping each other.  I guess I jumped the gun, I thought it was a little more "noob" friendly.  Oh well, good to learn new stuff.  You see, I am typing this on another comp in my house while trying to install Ubuntu on MY computer.

What's bootable flag?  What needs to have bootable flag set to yes? and what to no?

Just to clarify, mount point are the different "linux parts" you said I need to create? 

Ok, so that has opened a can of so called worms for me.  I plan on using it as a desktop and all things associated with that, downloading, watching movies, playing music, games(just a little).  I want to get away from XP slowly but surely.  With that said, how would I know what file systems I should make?  Should I make 1 of each that appears on the list?  How should I know their relative sizes?  I have 1 GB RAM should the Swap file be 2 GB of that 17 and be in ext3 as well?  

When you said that creating the FAT32 file system would be read both by linux and windows, was that for XP formated in NTFS?

Thanks
TristanMike

---

### Post by avdp on 2005-06-15
Hi all, just thought I'd post my problem under this thread, cos it's sortof the same:

I have Windows XP on a SATA drive. I've made a partition of 75 Gb for Linux (XP has 80Gb).  I ran the install of Ubuntu, and all went well, including making the partition for ubuntu a nice ext3 filesystem (dunno what that is yet  :-)  colleague recommended it to me), all copies fine and then... it has to make some boot record for dual booting.

2 things happened:
1st time it choose Lilo, i accepted all the standard things, and some Fatal error occured (error 1 i believe), and after that Win XP wouldn't boot anymore either. (tried all i could think of)

Now tonight, reinstalled XP, tried installing ubuntu again, same setup, but now with GRUB, and again 'fatal error'. Tried again and again that same error. Now thank goodness Windows still boots, otherwise I wouldn't be posting this now...

What am i doing wrong? I am really looking forward in playing with Ubuntu...

My setup:
amd3200 64bit (have 64 bit version of ubuntu)
1x 160 GB sata drive, via raid, 2 partitions (one for XP, one for ubuntu)
1x 200GB sata drive, promise raid (just WoW and Doom3  :-))

if u need more info, let me know...

---

### Post by TristanMike on 2005-06-15
That's a completely different problem than mine.  Plus you're running 64 bit system.  I haven't even gotten to the installation yet, I'm trying to find out how to create my directories and what sizes they should be.  I have no need of using Partition Magic as I already have space put aside but this creating directories is confusing for a noob.

---

### Post by avdp on 2005-06-15
Hmm.. I'm sorry :???: ... should i start a new thread then?

---

### Post by TristanMike on 2005-06-15
Well I should let you know that in the small amount I've read here, the 64 bit archetecture does change certin things, what those are I don't know.

---

### Post by poofyhairguy on 2005-06-15
[QUOTE=TristanMike]
What's bootable flag?  What needs to have bootable flag set to yes? and what to no?[/QUOTE]

I don't know, but the root partition (the one called "/") needs it,

> Ok, so that has opened a can of so called worms for me.  I plan on using it as a desktop and all things associated with that, downloading, watching movies, playing music, games(just a little).  I want to get away from XP slowly but surely.  With that said, how would I know what file systems I should make?  Should I make 1 of each that appears on the list?  How should I know their relative sizes?  I have 1 GB RAM should the Swap file be 2 GB of that 17 and be in ext3 as well?  

I would say only a half gig of swap. Make the rest (that you want Ubuntu on) to be ext3.

> When you said that creating the FAT32 file system would be read both by linux and windows, was that for XP formated in NTFS?

The thing is that Ubuntu can read, but not write to NTFS. The other poster was suggesting you make a fat32 parition for your files (movies, docs, whatever) so both Windows and Ubuntu can read and write to them. If you olny need to read the files on the windows side (or play them, whatever) then this is not needed.

---

### Post by Seth on 2005-06-15
The bootable flag should only be set if you are not installing GRUB to the master partition table.

Rule for swap is 2x your memory up to a maximum of 2GB of swap. 2GB should be fine but might be overkill; you could get away with 512MB or 1GB.

---

### Post by TristanMike on 2005-06-16
Thank You Very Much All. :)   I have now installed Ubuntu and am on it now typing this. :smile:   The installation did go smoothly in the end but what was catching me at first was the #2 logical drive as I listed above.  What I had to do, for anyone else confused, was to go into the options of that #2 and delete it so it ended up with the "Free Space" below it.  Then I only had the two.  I Partitioned the Free Space into a FAT32 drive, so that I can transfer files between Umbuntu and XP(NTFS) and with the remaining Free Space, I set it to Automatically Partition.  Doing this created The FAT32 system, the Swap and Root file systems.  During the rest of the install, it created all of the other folders which "newbie_ubuntu" spoke of.  I thought I had to create them manually, this is where alot of my confusion was and perhaps a little confidence.

NOTE:  My problem/install covers when installing XP fresh and allocating "X" ammount of space to it and leaving some space left over for my FAT32 Drive and my Umbuntu Drive.  I don't know how it differs when using Partition Magic and resizing a written drive.

---

### Post by poofyhairguy on 2005-06-16
[QUOTE=TristanMike]Thank You Very Much All. :)   I have now installed Umbuntu and am on it now typing this. :smile:  [/QUOTE]


Welcome.

---


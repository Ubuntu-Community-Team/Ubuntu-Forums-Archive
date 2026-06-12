---
title: "[SOLVED] Screwed up partition, help!"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by skaldicpoet9 on 2007-12-31
I just installed Ubuntu on my girlfriend's laptop. There is only one pretty big problem: I created the partitions backwards. I meant to have Windows on a 37gb partition and to have Ubuntu on a 12gb partition. So now I have Windows on a 12gb part and Ubuntu on a 37gb part and I have absolutely no clue what to do. I need to somehow go back and time and tell myself that I am actually putting Windows on a smaller part...but alas I have no flux capacitor. Please help! (With the partition not a flux capacitor lol)

---

### Post by forestpixie on 2007-12-31
instead of using a flux capacitor - try a gparted livecd - [http://gparted-livecd.tuxfamily.org/download.php](http://gparted-livecd.tuxfamily.org/download.php)

burn it as an iso and boot with it.

Resize the ubuntu to the size you want then resize windows into it

as always make sure you have suitabel backups when you're playing with partitions

---

### Post by skaldicpoet9 on 2007-12-31
Awesome! I'll go do that now...

---

### Post by forestpixie on 2007-12-31
be back in time :D

---

### Post by skaldicpoet9 on 2007-12-31
btw...I am guessing this is pretty self explanatory to use?

---

### Post by rockinlinux on 2007-12-31
gparted is a great program, it is very easy to use. To resixe the pariton just click on it and theneither drag the border on thpicture to make it smaller to type in the sixe you want. depending on how you have the two partitions you may also have to move one. to do this you just click the partition you want to move and al click the resize/move and drag it to where you want it.

good luck....

---

### Post by rockinlinux on 2007-12-31
oh and when you burn the boot cd be sure to burn it slow! :)

and when booting the cd if you have problem booting the GUI then try one of the HP setting at the main menu (you will see what im talking about). i have a toshiba nad i have to use a HP setting....go figure.
:)

---

### Post by Sef on 2007-12-31
If you have a back up, I would recommend downloading Clonezilla-GParted.  This way you can make a back up of your partitions.

Yes, GParted is fairly easy to use.  However, **back up** any data you can't afford to lose.

---

### Post by skaldicpoet9 on 2007-12-31
Ok, so I resized Ubuntu down to 10gb but I have a problem. When I go to resize the ntfs part it says I can only resize it to 12gb (which is how big it is already). I looked at the ext3 part and it will allow me to resize it back to 34gb so why can't Ido that for the Windows part? It says I now have 25gb left of unallocated space, what gives?

---

### Post by skaldicpoet9 on 2007-12-31
btw this is how my memory is divided up now:
ntfs-12.65gb
ext3-9.79gb
fat32-6.84gb
extended-1.54gb
unallocated-25.06

---

### Post by forestpixie on 2007-12-31
if it's in that order on the disc I think you need to move it next to the ntfs partition before you can resize - although not completely sure on that point

---

### Post by kvonb on 2007-12-31
-

---

### Post by skaldicpoet9 on 2007-12-31
This is the exact order:

fat32
ntfs
ext3
unallocated
extended

How do I move the unallocated space next to the ntfs space so I can use this space?

---

### Post by forestpixie on 2007-12-31
you need to move the unallocated between the ext3 and ntfs and then resize

alternatively you could in fact format it to ntfs and you would have a separate partition that you could use for win and linux

---

### Post by skaldicpoet9 on 2007-12-31
This is what I get when I type that into the console:


Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

Man, I gotta tell ya this is really frustrating lol

I wish I would have just did things right the first time :(

---

### Post by skaldicpoet9 on 2007-12-31
How do I move the unallocated space between ntfs and ext3? I tried dragging but that didn't work. Hmm formatting it sounds easy...

---

### Post by kvonb on 2007-12-31
-

---

### Post by forestpixie on 2007-12-31
you need to paste in the command you were given by kvonb - otherwise it tells you what it's expecting 

and of course if everybody did everthing right first time - what could we do here :D

---

### Post by skaldicpoet9 on 2007-12-31
BUt if I delete EXT3 won't I have to install UBuntu again?

---

### Post by skaldicpoet9 on 2007-12-31
> **forestpixie said:**
> you need to paste in the command you were given by kvonb - 

Usage: fdisk [-b SSZ] [-u] DISK Change partition table
fdisk -l [-b SSZ] [-u] DISK List partition table(s)
fdisk -s PARTITION Give partition size(s) in blocks
fdisk -v Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

You mean the fdisk -1 cmd?

Because the above is what I got when I typed it into the console.

> **forestpixie said:**
> and of course if everybody did everthing right first time - what could we do here :) 

:) Well I do appreciate the fact that this is by far the most helpful forum that I have ever been on. I look forward to coming here with all of my noobtastic Linux questions lol

---

### Post by forestpixie on 2007-12-31
if you pasted it - it would of worked - because the 1 is in fact a lowercase L :)

and yes if you delet the ext3 you'd be needing to reinstall 

but do the fdisk -l and then we can see what's inside the extended partition

---

### Post by kvonb on 2007-12-31
-

---

### Post by skaldicpoet9 on 2007-12-31
](*,)

Oops, damnit

Here it is:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe8dbe8d

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         894        2545    13269690    7  HPFS/NTFS
/dev/hda2               1         893     7172991    b  W95 FAT32
/dev/hda3            2546        3823    10265535   83  Linux
/dev/hda4            7096        7296     1614532+   5  Extended
/dev/hda5            7096        7296     1614501   82  Linux swap / Solaris

Partition table entries are not in disk order

Yeah, there isn't anything I can't lose in Ubuntu...

---

### Post by kvonb on 2007-12-31
-

---

### Post by forestpixie on 2007-12-31
I'd do the reinstall then as suggested - use gparted to get the partitions how you want them and reboot with the livecd and use manual partitioning when you get there

Edit - and please make sure you've got backups - or you'll be sorry :D

good luck

---

### Post by skaldicpoet9 on 2007-12-31
OK so then delete these?

/dev/hda3 2546 3823 10265535 83 Linux
/dev/hda4 7096 7296 1614532+ 5 Extended
/dev/hda5 7096 7296 1614501 82 Linux swap / Solaris

And then install Ubuntu again? 

If this is what I am supposed to do...just for future reference (so I dont have to do this again lol) when you are doing the guided partition during the UBuntu install I need to move the slider to the left to make the part bigger on the windows side? (last time I went almost all the way to the right because it said 12.6gb part but obviously the part was created on the win side and not linux).

---

### Post by skaldicpoet9 on 2007-12-31
Hmm, it lets me delete the ext3 part and the swap but it won't let me delete the extended part

---

### Post by kvonb on 2007-12-31
-

---

### Post by forestpixie on 2007-12-31
that would be right - use gparted again before you do the install you should end up with the ntfs and fat32 partitions left - 

while you're in there once you've done that make the linux partitions - make an extended partition and put the 3 linux partitions inside that - /, /home and swap - you can format them there

kvonb will be able to explain the difference between reiser and ext3 - I've no idea 

then insert your ubuntu disc and when you get to the partitioning - go manual - then you edit the partitions and pick the corresponding mount points

sounds confusing - but it'll be self explanatory once you're doing it

good luck

---

### Post by skaldicpoet9 on 2007-12-31
Why can't I delete the extended part? Or is it needed?

---

### Post by forestpixie on 2007-12-31
I expect you have to delete the partition inside the extended and apply first - then delete the extended - but surely once you've got an empty extended you just need to resize it

---

### Post by kvonb on 2007-12-31
-

---

### Post by kvonb on 2007-12-31
-

---

### Post by forestpixie on 2007-12-31
oh I see thanks for that - I just changed the check frequency on all my partitions to more sensible numbers - although I left root as it was

but as you say it can be extremely annoying - before I changed it about - I was doing some reinstallation and partition and got caught in between reboots and the rest of it 5 times - grrr

---

### Post by skaldicpoet9 on 2007-12-31
Ok, that worked :)

edit  

why did I just get an error22?

It is sttill trying to load the grub booter

---

### Post by forestpixie on 2007-12-31
ok if you've done the partitioning and you've not got a bootable disc in it's trying to run the ubuntu you've killed off


put the disc in and boot with that

---

### Post by argie on 2007-12-31
Just for the record, at the stage when you were able to resize just the ext3 partition and not the ntfs partition, you would be able to resize both if you reduced the ext3 partition from the other side. 
```

Originally:
<---ntfs---><-------------ext3--------------->
After resizing ext3:
<---ntfs---><--ext3--><--unallocated space--->
What would have solved everything:
<---ntfs----><--unallocated space--><--ext3-->

```
I remember doing this on the LiveCD but I do not recall if it was the Installer or GParted that I had to use, you just had to drag the left resize handle (it appears on the top of the Resize Partition dialog when you choose to edit it).

I suppose you've mostly fixed your problem, but just in case you get in the situation later.

As to why you can't delete the extended partition:
A single drive can only have four primary partitions. To have more, you have to make logical partitions in an extended partition.

---

### Post by kvonb on 2007-12-31
_-_

---

### Post by skaldicpoet9 on 2007-12-31
Awesome :) 

I can't thank you guys enough.

On an unrelated note: I am getting pretty damn good at using my Wiimote to type lol

---

### Post by forestpixie on 2007-12-31
glad you're happy - it's nice to have a bit of patience on the other end, sometimes there's a bit less ;)

---

### Post by skaldicpoet9 on 2007-12-31
lol

I got too much patience sometimes.

But when it comes to getting aquainted with Linux I am adamant. I love the idea behind Linux and open source software in general. I am getting involved at a layman's level but eventually hope to contribute to the community with open source software of my own and to eventually (hopefully) work on Linux distros as well. My only complaint is the lack of games (I play a lot of games) if game support was more fleshed out I would definitely switch completely over to using Linux. But my theory is that it won't be long before games on Linux get a lot better. Anyways, I thank you guys very much for the help and look forward to being active here :)

---

### Post by forestpixie on 2007-12-31
I don't do games - so that's not a worry to me, still get someothing out of learning new things though

once you're happy here - can you mark thread solved - helps others searching for answers

happy new year

---

### Post by skaldicpoet9 on 2007-12-31
I have one last question:

In the restricted drivers console my graphics card is there. Whenever I try to enable it pops out with a error message that says it couldn't be enabled. How do I enable my graphics card? btw I have an ATI Radeon XPRESS 200M.

---

### Post by kvonb on 2007-12-31
-

---

### Post by skaldicpoet9 on 2007-12-31
Hmm, it says on the Envy page that ATI cards are supported but when I go to install the package it says "Error: Dependency is not satisfiable: xserver-xorg-dev"
what does that mean?

---

### Post by skaldicpoet9 on 2007-12-31
OK nvm I figured out that obviously I am missing a dependency, however, whenever I try to install libxi-dev it says I need libxi6 as a dependency but when I go to install libxi6 it says I already have a later version installed. Any clue why it would say this?

---

### Post by kvonb on 2007-12-31
-

---

### Post by skaldicpoet9 on 2007-12-31
Just did all of that but unfortunately it didn't solve the problem. I was getting stuck on libxi6 before but now it appears that that dependency has been taken care of only to be replaced by another dependency (libxau6) that I already have as well (when I go to install it it says that I already have a later version).

---

### Post by skaldicpoet9 on 2007-12-31
Is there maybe another way to do this? I don't think that this is working. I keep trying to install the dependencies for Envy but when I get to libxau-dev it says I need libxau6 but when I go to install that the installer says I already have it! This is slightly frustrating...

---

### Post by kvonb on 2008-01-01
-

---


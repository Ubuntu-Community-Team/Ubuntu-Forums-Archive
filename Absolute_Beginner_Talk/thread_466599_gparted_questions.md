---
title: "gparted questions"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by matious on 2007-06-06
i was looking at my gparted and i was just wondering a few things

what exactly is /dev/hda1 "linux swap"? its taking 44.84 gib, and it says its not active, is that okay?

im just wondering if there is any way of recovering my long lost xp off of this. When i installed ubuntu off the live cd i heard it automatically partitioned my hardrive, doesnt seem so.

So i though mabey thats my xp there, and that would explain the non-activeness.

excuse the complete noobiness, im starting to feel a little lost in this linux world im in o_0

---

### Post by Brightbelt on 2007-06-06
Hi,
From what I understand in my experience, a swap partition is usually a much smaller partition on your hard drive - anywhere from 256 MB to 5 GB - that helps facilitate a double-boot setup between 2 different operating systems. Thus a swap would at the very least be the third and smallest  partition on your main hard drive.

   If your Swap partition drive is indeed 44 GB as you say it is, that is most certainly a waste of space, since I believe only 256 mb is required to set up a swap between Ubuntu and Vista or XP. (I would suggest setting a swap partition at 3 to 4 GB, just to be careful).

I can't tell for sure without more information and/or seeing your computer, but if your 44 GB partition is named 'Swap' by Gparted, I seriously doubt that your XP Operating system is still on there. But I can't say for sure without more info. 

I hope this helps, Frank B.

---

### Post by ryanVickers on 2007-06-06
not to be rude, but the swap is actually just ram that's stored on disk when there's no ram left.  Yes, only 256Mb to 2Gb is really plenty.  I would have used the manual partition, because automatic does some strange things I've heard, and I don't really trust it - you've found this out :p

I don't believe that there is a way to recover your xp if it's been formatted, sorry
I would go back and re-install ubuntu using manual partitioning and make a 1Gb swap and then everything else ubuntu (unless you still need xp, then give it a partition too (NTFS) and there's not more need for FAT32 because ubuntu can now safely write to NTFS Hooray!)

---

### Post by Brightbelt on 2007-06-06
I was just told when I first installed Ubuntu in a double-boot that a Swap partition was necessary to facilitate it, that's all.

;) Frank B.

---

### Post by ryanVickers on 2007-06-06
Interesting.  Well, what does that is the MBR or Master Boot Record that holds the info on which OS goes where, what it is, how to boot it, etc.

But in the old days (about 3 months ago :)) you would have needed a FAT32 partition for Linux to give files to windows because of this:

Linux reads:
Linux
NTFS
FAT32

windows reads:
NTFS
FAT32
**NOT Linux**

so clearly this was necessary, and it might have been nicknames "swap" because you could swap files back and forth, but it could confuse some people this way ;)...

---

### Post by antoz on 2007-06-07
Windows can read and write to ext 3, check link
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Inxsible on 2007-06-07
matious,

put in a liveCD and run GParted. When it shows you the partitions in your disk, take a screenshot and post it here. That way we can find out more about your partitions and help you out

---

### Post by matious on 2007-06-07
is this what you are talking about inxsible?

[IMG]http://i134.photobucket.com/albums/q111/matious1/Screenshot-1.png[/IMG]

---

### Post by ryanVickers on 2007-06-07
Yes, I think the "automatic" turned your windows into swap, made a linux partition, and then more resonable sized swap at the end.  I say blow it all away and re-install using manual stup so it looks like this, or this! (attached at bottom)
(the FAT32 could of course (and shoudl! :)) be NTFS)

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

> Windows can read and write to ext 3, check link
well, that's another story; I mean just out of the box (or no special software like that!)

My point was though that a FAT32 is no longer necessary because linux can read/write windows. :)

---

### Post by matious on 2007-06-07
do i have to re-install xp before doing that though?

can you link me to a tutorial telling me what to do for the manual setup?

---

### Post by ryanVickers on 2007-06-07
Ok, if you want xp, then I would recommend doing that first, yes.

I would do this:
A. Install Windows XP
1. boot from live ubuntu CD
2. remove all partitions from HD (backup important files first)
3. make a FAT32 the size you want XP to be (make it at the right side of the HD)
4. Boot from XP disk
5. install into FAT32, but durring install, re-format that one section as NTFS

B. Installing Ubuntu 7.04
1. boot from the live CD again
2. you now have a partition on the right side with xp, so...
3. in the empty space, make a 512Mb swap on the right side (to the left to xp)
4. then, you should be left with the desired space for ubuntu (minus 512Mb :))
5. make a ext3 here and install into it

Your done!  It will automatically setup a duel boot GRUB screen so every boot, you can choose your working copies of xp or ubuntu!

It would look like this: (please wait, creating image of HD, this may take several minutes :))

---

### Post by matious on 2007-06-07
okay, to remove everything when putting the xp disc back in i go to manual and type "fixmbr" right?

then it completely erases everything and i start off fresh?

---

### Post by Gwasanaethau on 2007-06-07
> **matious said:**
> do i have to re-install xp before doing that though?

can you link me to a tutorial telling me what to do for the manual setup?

I'd say Windows XP probably has to go on first because when it is installing it overwrites the boot sector without looking for other operating systems first. Thus when you restart after installing Windows it will boot straight into XP without asking. I believe it is possible to rectify this but from what I've heard it's a pain in the neck! :D It's just easier all round to install XP and then Ubuntu afterwards.

As for the manual setup, I'm afraid I can't help you there. Sorry. :(

---EDIT: Oops, didn't realise there were two pages to this topic. My bad&#8230;

> **matious said:**
> okay, to remove everything when putting the xp disc back in i go to manual and type "fixmbr" right?

then it completely erases everything and i start off fresh?

If you put the XP disc at the start of the boot, I think it comes up with "press any key to boot from disc" - though it might be just certain ones that do it.

---

### Post by ryanVickers on 2007-06-07
I thought these ware good instructions (up)! :p

to remove everything, boot from ubuntu live CD and delete all partitions.

the command you've got there just fixes the MBR, which is irrelevent and unnecessary, not to be rude.  But if you put in xp, then ubuntu like my instrctions, ubuntu will build a MBR so you can choose on boot xp or ubuntu!

---

### Post by bren on 2007-06-07
woah guys ..... based on my recent experience i reckon that XP might still be there.

if the partition table is corrupted then the data isnt recognised properly hence it look empty.

But it is not.

If the partition table is corrupted it could show the hda1 as swap when it is not 

It is really NTFS

It is really easy (once you have done it once) to repair the partition table.

You need a utility called testdisk.

The best way is to use a live cd which has both gparted and testdisk on it

You get this here [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

When you run the livecd type startx

Then when you get the GUI desktop rightclick and select testdisk

xp will be back in seconds!  (i think)
instead of hours for xp install

bren

---


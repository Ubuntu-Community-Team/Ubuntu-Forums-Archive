---
title: "Need a hand with 2nd hard drive....AAUUUGGHHH!!"
date: 2006-01-18
forum: Absolute Beginner Talk
---

### Post by darkwings on 2006-01-18
Hey everyone, this is my first post. Please be patient with me, I've been away from the bliss of Ubuntu since I met my g/f with her *shudders* XP laptop.  I have just picked up a second HD 160 gigs woohoo.  Sadly though I cant find the tips and or tricks I need to make it usuable.  I do have bios set up properly. I have tried fstab. It tells me I am denied permission even through a root terminal?? Most of the help questions posted are for setting up a pre-existing windows drive. Mine is shiny new, waiting for some well deserved love.  Im not stupid, just a slow learner.  I have checked out at least a half dozen links.  too much jargin, not enough point by point instruction. sighs....help im lost

---

### Post by dueY on 2006-01-18
What kind of file system do you want on the new drive?  You have to format the drive before you can do anything with it.

---

### Post by darkwings on 2006-01-18
I would like to stay with what I have, I just realized though that im on 5.04 not 4.10 my bad...I dont even know how to format the drive

---

### Post by kont.raen on 2006-01-18
[QUOTE=darkwings]Hey everyone, this is my first post. Please be patient with me, I've been away from the bliss of Ubuntu since I met my g/f with her *shudders* XP laptop.  I have just picked up a second HD 160 gigs woohoo.  Sadly though I cant find the tips and or tricks I need to make it usuable.  I do have bios set up properly. I have tried fstab. It tells me I am denied permission even through a root terminal?? Most of the help questions posted are for setting up a pre-existing windows drive. Mine is shiny new, waiting for some well deserved love.  Im not stupid, just a slow learner.  I have checked out at least a half dozen links.  too much jargin, not enough point by point instruction. sighs....help im lost[/QUOTE]

Hi Darkwings,

first of all you should get the package named gparted :

sudo apt-get install gparted

This app (which has a starter created in the Gnome-Menu) will provide you with a GUI to create the desired partition on your new disk and "format" it with a filesystem of you choice afterwards.

Therefore select the new disk in gparted. Depending on where you installed it, it is found as :

/dev/hda  == primary master
/dev/hdb  == primary slave
/dev/hdc  == secondary master
/dev/hdd  == secondary slave

Just to be sure - in your case it should be the disk with no partitions around ;)

Now right-click on the line saying something like unallocated and size 160 GB and then left-click on "New" in the context-menu that pops up. After you have done this, the "create new partition" dialogue will appear - and iirc it already should have guessed the new partition's size - e.g. the maximum of available space. Now all you have to do is selecting a filesystem to use (I would suggest xfs, reiserfs or ext3 here) and click on "add". The dialogue will disappear and if you click on the Apply-button/icon in the menu, gparted will do as you told it. When it's done, you can exit the app and edit your /etc/fstab, so that you can actually _use_ the partition. To understand how this is done, I suggest that you take a look at [this]("http://www.ubuntuforums.org/showthread.php?t=113014") thread, where I discussed that problem with another user.

Ok, hope I could help

---

### Post by darkwings on 2006-01-20
WOOOOHOOOO thanks Kont.  its working now...formatted and ready to be filled with all the love I can muster...\\:D/

---


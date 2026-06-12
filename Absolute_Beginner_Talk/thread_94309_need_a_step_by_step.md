---
title: "need a step by step"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by albino_smurf on 2005-11-23
i have just got my free ubuntu discs in the mail:D i was so excited!

i found a how-to guide on one of the forums here and decided it was simple enough to jump on into a whole new sea of linux programs. but someone has tied a concrete block to my ankle (windows XP). 

my mom and brother are not so adventerous when it comes to OS packages so i will need to keep windows on my pc.

is there anyway to do this without wiping out my hard drive (which i have already done once:mad: ) or effecting the windows system?

i need to have both on my system and need to be able to transfer files to and from both OS. 

any help is greatly appreciated!!

---

### Post by Kapre on 2005-11-23
[QUOTE=albino_smurf]i have just got my free ubuntu discs in the mail:D i was so excited!

i found a how-to guide on one of the forums here and decided it was simple enough to jump on into a whole new sea of linux programs. but someone has tied a concrete block to my ankle (windows XP). 

my mom and brother are not so adventerous when it comes to OS packages so i will need to keep windows on my pc.

is there anyway to do this without wiping out my hard drive (which i have already done once:mad: ) or effecting the windows system?

i need to have both on my system and need to be able to transfer files to and from both OS. 

any help is greatly appreciated!![/QUOTE]


albinosmurf - congratulations on getting your Ubuntu CD. I would suggest for you to read the 1st 2 post on this forum (Absolute Beginners Forum) before installing linux. There is a "How to" already of this but I dont have time to find it for you.  I suggest to take this steps to make (for you to dual boot with XP):

a. check if you have enough room for a dual boot (Ubuntu w/ Gnome desktop - would need at least 2 Gigs).
b. back-up your files on the harddrive
c. defrag the drive with xp on it, for at least 2 times
d. use a drive partitioner (gparted or QTparted or any partitioning software - livecd i think comes with gparted)
e. after partitioning, make sure that you will install on the newly created partition (not on the xp partition)
f. read all the details that will be shown on the screen (before pressing enter).

K

---

### Post by aysiu on 2005-11-23
Back up your files and visit this link:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by ikki_72 on 2005-11-23
the 1st time i installed ubuntu, it's frustrating since i dunno enough stuff about linux, just the curiosity:) but then i tried n tried. too bad i don't have internet at home or it'll be much fun for me since i'm a gamer.

---

### Post by d1337 on 2005-11-24
Excellent advice and links from both Kapre and Aysiu...so I'll just add some confidence.  Nowadays practically every new machine you buy will have MS something on it.  I've been hard pressed to totally demolish an MS OS, so I typically dual boot.  I have done so with Libranet, Vanilla Debian, and most recently Ubuntu (both Hoary and Breezy).  IMHO, Breezy makes this easy as cake.  During install, Breezy asks if you want to shrink a partition and use the free space.  The GUI installer for this option is awesome.  Make sure you heed Kapre's advice on defrag at least twice.  I have 5 boxes now dual booting with windows and haven't lost anything on the windows side, Linux side works fine.  I must say, though, if you have room and a few bucks, adding a second harddrive to house the Linux distro of your choice (mine being Ubuntu) usually allows much more play space...or work space.  Once you start, you won't stop.

** NOTE ** the backup of anything existing (that you want) is a really nice security blanket...don't take that shortcut in thinking everything will be fine...we all gotta sleep sometime.

d1337

---

### Post by aysiu on 2005-11-24
[QUOTE=d1337]
** NOTE ** the backup of anything existing (that you want) is a really nice security blanket...don't take that shortcut in thinking everything will be fine...we all gotta sleep sometime.[/QUOTE] I liken it to riding a motorcycle to work without a helmet on. Odds are you won't get into an accident. If you do, though... there go your brains on the pavement...

---

### Post by albino_smurf on 2005-11-24
> originally posted by **d1337**
I must say, though, if you have room and a few bucks, adding a second harddrive to house the Linux distro of your choice (mine being Ubuntu) usually allows much more play space...or work space. Once you start, you won't stop.

i have an extra hard drive laying around, how can i use it to dual boot with windows?

would i still be able to transfer files between the two OS?

---

### Post by uPilot on 2005-11-24
You can dual boot.  But as far as I know, you have to install Windows first, and then Linux.  And install either grub or lilo.  I'd recommend Grub since it is a GUI.

You'd then have to create a new entry in Grub for Windows.  How, I have no idea :D

As well, Linux will be able to read Windows, but Windows will not be able to read Linux... That is, unless you make your Linux partition FAT32.  But I wouldnt recommend it due to lack of permissions.  I dont even know that Linux would accept FAT32.  I used reiserFS.

Pilot

---

### Post by spiderbatdad on 2005-11-30
I installed ubuntu after making a cd from the iso download. I booted my system and began hiting enter, like the instructions said to do. When it came time to format the disk, Microsoft had a warning that all data would be lost. Oh well, I says. Unbuntu installed easily, and upon rebooting, I had the option of choosing which os to load. I selected Ubuntu first...it was awesome. A couple days later I decided to load up windows xp to see what was there. Everything! Every upgrade (sp2), every picture, song, etc. Haven't been back to windows in a week. Trying to learn how to use the new os. I understand at some point I should be able to move files from windows to Ubuntu.

---


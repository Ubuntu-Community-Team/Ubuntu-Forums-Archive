---
title: "Windows Master"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by rawlz on 2006-05-08
Okay, serious noob here, but I'm trying...

I have Windows XP set up as the master drive (I was hesitant to give it up) and Ubuntu as the slave.  I have lots of files I'd love to get ahold of in Ubuntu, but I can't figure out how to access them without burning everything to a cd and doing it the hard way.  Anyway for me to get ahold of the master drive without completely reinstalling everything?

---

### Post by ComplexNumber on 2006-05-08
just to make clear for everyone, are you wanting to take files from ubuntu and place them on your windows installation, or the other way round?
also, are you using gnome or kde?

---

### Post by jimrz on 2006-05-08
it's not quite clear, but think you are wanting to access files on your windows partitions from ubuntu. If this is correct, look at [[COLOR="Sienna"]**_this_**[/COLOR]]("http://www.ubuntuguide.org/#automountntfs") for instructions on mounting your win partition(s) and be sure to scroll down the page to the section on how to make them auto-mount each time you boot ubuntu. Since linux can read a  ntfs partition but not safely write to it, you may want to set up a vfat (FAT32) partition, if you do not already have one, that can be used read/write from both ubuntu and win.

Welcome aboard.

---

### Post by catlett on 2006-05-08
Follow the link in my signature. It will get you to a site for ext2 drivers. This will allow you to get into ubuntu from windows.

---

### Post by joshrobinson on 2006-05-08
[QUOTE=catlett]Follow the link in my signature. It will get you to a site for ext2 drivers. This will allow you to get into ubuntu from windows.[/QUOTE]

is there ext3 drivers too?
also the links in your sig are broken or just not there at all

---

### Post by catlett on 2006-05-08
I was editing my signature to add (ubuntu partition) because I realised people might not realise that is what ext2/3 was talking about. That must have temporarily broken the links.
It works for ext3. It just technically views them as ext2 type of journaling. What this means is that you can't benefit from the things in ext3 that aren't in ext2 (what those are I don't know. That is just what the faq says on the ext2 driver web site)
I haven't had any problems. Someone else had a problem that on reboot the partitions didn't come up in windows again. This didn't occur with me but if it does you just go into the application again. 
It is an easy application. When installed, it is in the XP control panel as an option. When you hit on it you get a view of your hard drive. Each ext or 3 partition will have a drop down box in it. You hit on the box and it will give you a list of drive letters to choose from ( G,H,I,J,K,L etc) You pick one and the disk is in My Computer with that drive letter.

---

### Post by rawlz on 2006-05-08
All my good stuff is on my Windows Master drive and I want to access it through Ubuntu.  

I'll give the Unofficial Ubuntu Starter Guide a shot and see if that solves everything for me.  Thanks!

---


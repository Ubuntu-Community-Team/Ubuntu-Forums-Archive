---
title: "need a bit of help"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by tikki on 2007-12-07
I saw this tutorial: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
and was wondering, will this completely remove my WindowsXP?

if not, do i need the CD in to run ubuntu? I took the CD out without fallowing the guide and i got a screen "choose your operating system" and when i chose "ubuntu" i got a B/W command prompt type window that said "type help for a list of commands"

thanks for the help.

---

### Post by Shinbu-Otaku on 2007-12-07
you can dual-boot ubuntu with XP, but for this you would need 2 seperate partitions on the same hard drive (one solely for Ubuntu, the other for XP), or 2 hard drives (with 1 drive per OS). This will not delete XP, unless you choose to install it on the drive with XP on, but it is very hard to not realise which one that is (XP has a hard drive format of NTFS or FAT32, whereas linux uses ext3 or ext2 mainly)

---

### Post by subs on 2007-12-07
no... ubuntu is able to edit the partition table of ur hdd so that u can run windows xp as a dual boot....

you do not need the live cd to run the OS.... u r installing it on ur hdd!!!!

as for the second bit.... how far did you go with the installation before u remove the cd???

---

### Post by tikki on 2007-12-07
the second part doesnt matter to me, i was testing stuff.

i only have 1 hdd, and xp is installed on it in C:\ drive. if so, is it possible to create a new drive so i can install ubuntu on that one? 
so if i install ubuntu on the C, it would overwrite XP?

---

### Post by tikki on 2007-12-07
please help, i don't want to remove Windows, and judging by the 1st reply it seems i will replace windows.

---

### Post by gcrussell1 on 2007-12-07
> **tikki said:**
> please help, i don't want to remove Windows, and judging by the 1st reply it seems i will replace windows.

The partition editor in the graphical installer from the Live CD will allow you to shrink the XP partition and use the freed space, leaving you with both OSes - I did it with no trouble a month and a half ago. The interface is pretty intuitive, so you should be able to do it yourself, but if not, I'm sure you could find a how-to easily enough.

Cheers.

---

### Post by tikki on 2007-12-07
well, i guess i'll try it.
if i mess up, it will be an excuse for me to get a new pc (this=junk). then this could be my linux pc :)

---

### Post by tikki on 2007-12-07
got some good news and some bad news
good:
windows isn't screwed up :)
still got all my applications

bad:
ubuntu isn't working, when i insert the CD and select the 1st option it loads up (good). then after that i hear a sound (possibly the ubuntu startup sound [jungle-ish theme]). after that the screen turns tan and a bunch of weird/random line strokes appear, then my screen shuts down. so I'm guessing my graphics card isn't good enough. i tried safe-mode, no go. i ran the memtest, i passed with no errors.

I'll uninstall/reinstall ubuntu, if it doesn't work, i wasted 50cents (CD) and 1/2 a day :(
unless you guys can help fix it.

edit:
uninstalled/reinstalled, same thing
tried ctrl+alt+bckspc, did nothing

---

### Post by gcrussell1 on 2007-12-08
What's your graphics processor? I suppose it might not be compatible; you should search the forum for the name of your GPU and see if other people have had any luck with it.

Additionally, and probably more likely, it could easily be a problem with the Live CD - that could be related to a download error or a burning error, and either one could leave you with a non-fully-functional disc (I've got two discs from the same ISO - one has one small buffer error every time it loads up, and one won't run at all, but is fine for some Synaptic stuff that comes directly off the CD). If the forums don't indicate that your GPU is screwed for Ubuntu, then you should try burning a second copy - burn it at the minimum speed to minimize errors and try not to multitask the computer while doing so. If that doesn't work out, try downloading a new copy of the Live CD ISO (from the official servers) and give it another go. 

Question - did the Live CD work before or not? I assumed from the first post that you had run from the Live CD before, but I could have assumed too much.

---


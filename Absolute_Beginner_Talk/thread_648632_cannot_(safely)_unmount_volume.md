---
title: "cannot (safely) unmount volume?"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by 99bluefoxx on 2007-12-23
so after a small disaster with my first sansa e260, in which it claimed to be 'read only' even though i owned it and had read/write permissions to it, and it bricked, i finally replaced it, plugged the new one in, dumped a few hundred tracks onto it, and tried to unmount it.
only to be hit as the same problem that i encountered the first time i plugged the old one in.
"cannot Unmount volume: cannot remove entire directory."
im pretty sure this is the root of my troubles with the last one bricking, and if i keep bricking them, im pretty sure futureshop and sandisk will start to suspect something [like my computer is "incompatible" with it]
so i was wondering, has anyone else had this problem, and how did you solve it?
i am using USB 2.0, like specified, MSC mode, and linux ubuntu 7.04, with the gnome desktop enviroment.
additionally, after i click the first error dialog box, i get a second one, that says "Unmount error" as the title, but nothing else.
then i sometimes see something saying "kio media" or something like that.
any help is great thanks, i really dont want to brick a second e2xx, and this is my fourth[or is it fifth] sandisk digital media player
EDIT: i should probally mention that i am aware that if an application is using a device it can prevent it from being unmounted, but i make sure to exit all media applications i have running beforehand, the error still shows up
for a while it only appeared if i tried whilst running rhythmbox, but even after quitting that it started doing this

---

### Post by p_quarles on 2007-12-23
Based on my experience, the error message in the second screenshot is telling you that it's still writing to the disk. This can keep going on for a bit after you've closed the media program, because it's really the file manager (e.g. Nautilus) that's handling the transfer. So, how long does this go on? Does it eventually allow you to unmount it?

Anyway, you can try to find out what application is holding it up by typing this:
```
lsof /media/Sansa\ e260
```
This is assuming that the mount point is, in fact, in the /media directory, which is the default.

---

### Post by 99bluefoxx on 2007-12-23
ok, i tried your command with rhythmbox running and it showed up like so:
```
bluefoxx@azurE-prIDE:~$ lsof /media/Sansa\ e260
COMMAND     PID     USER   FD   TYPE DEVICE  SIZE NODE NAME
rhythmbox 17747 bluefoxx   18r   DIR   8,65  4096    1 /media/Sansa e260
rhythmbox 17747 bluefoxx   24r   DIR   8,65 94208  963 /media/Sansa e260/MUSIC

```
and then i quit rhythmbox, hit the command again, and nothing came up, so i tried to unmount, but it said 'the device cannot be unmounted because an application is using it', i clicked 'OK' and another of the blank dialog boxxes came up
also, i removed it before, after it said 'cannot remove entire directory' and it worked more or less ok, a few files were missing, and it froze twice on me, once while accessing a video that came with it, and again while rating a song. it also runs slow when on the 'info' screen under settings, i think i need to upgrade the firmware or something?

---

### Post by p_quarles on 2007-12-23
Okay, that just means that Rhythmbox isn't finished transferring files when you quit it, so the application is still running in the background. 

What happens if you attempt to transfer music files to the Sansa using the file manager? Same thing?

Btw, removing a USB drive in the middle of an ongoing file transfer *is *going to lead to data corruption. Just so you know.

---

### Post by 99bluefoxx on 2007-12-23
well thats all i use for putting music on it, is nautilus
i quit rhythmbox when it comes up usually, and it doesnt keep running in the background
i have tried MTP mode, but i can't seem to figure it out...
and as for data corruption, i am all too farmilliar with that, i have lost 12 others computers in the past 5 years[this being computer 13.9.5], and about 20 harddrives, the sata controller on my current mobo is gone, as i discovered when i connected a seagate sata 80 gig and the bios read it as 270gigs, lol
data corruption is my worst and sworn enemy, :lolflag:

---

### Post by p_quarles on 2007-12-23
Yeesh. That's some bad luck there. ;)

Anyway, it appears that Rhythmbox *is* in fact running in the background, but here's how you can stop it from doing so. After quitting the graphical portion of the app, open a terminal and type this:
```
killall rhythmbox
```
That will terminate the process altogether. Now that I know that you were using Nautilus, I suspect that this is probably the main issue: Rhythmbox is auto-detecting the media device, and trying to do something with it. I don't use Gnome, so can't give you exact directions, but look around and try to find a way to turn off that auto-detection.

---

### Post by 99bluefoxx on 2007-12-24
ok, so after much fiddling around, a few breaks to eat pie, and make wallpapers for friends, and a few feeze-ups and crashes, i found that this code is working perfectly for removing a USB device
```
bluefoxx@azurE-prIDE:~$ sudo eject "/media/Sansa e260"
```
simply replace the stuff in the quotes with your device you want to remove.
i used this back when i restored some junk form an apt-on-cd disk, and root mounted the CD, making it impussible to eject it from my precious dvd drive and through the power of lurking, i found the "sudo eject <device/drive>" command
please excuse my insanity, its 2:30 in the morning here, i woke up at 7:00 yesterday, and ive been running all over the cities today trying to get my sansa replaced[obviously i did find a store that wasnt sold out, lol]. also, i probally shouldnt mix coffee with energy drinks and lots of sugar, and nothing much else[maybe thats why im hyper?]

---


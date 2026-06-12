---
title: "iPod mount problem PPC Feisty"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by leoos on 2007-05-21
Installed Feisty on a MacMini last week and initially it was mounting my firewire drive and iPod ok. Unknowingly i must have done something to change this situation as I now get the following error in gtkpod when I try to mount my iPod ***(Error initialising iPod: Problem creating iPod directory or file: '/media/ipod/iPod_Control'***.) and neither iPod or firewire drive appear on desktop now when plugged in either. Is there a reference I shoudl be going to that could help me here. I un and re installed gtkpod top no effect but Im thinking the problem is more in depth than that right now as they are not showing up on the desktop

---

### Post by AzraelUK on 2007-05-21
I'm having about the same problem, but I'm not on a Mac. I upgraded from Edgy to Feisty a couple of days ago and now my iPod doesn't get recognised when I plug it in - /media/ doesn't have any ipod dirs in it either. 

It's rather annoying me now :/.


**EDIT:** That's strange. I loaded up the file browser and pressed F9 to open the side panel, because I vaguely remember there being a shortcut to fstab in it there as root, and I wanted to checked the configuration. I saw listed an 'Apple Video Music Player' or something - when I clicked on it, it turned into 'IPOD' and the logo changed to the ipod's logo. Unfortunately my upgrade to feisty makes gtkpod segfault whenever you start it. Feisty's caused plenty more problems for me than it has fixed problems.

---

### Post by leoos on 2007-05-22
This is the filesystem error I get when I attach my iPod if that helps

[IMG]http://i2.photobucket.com/albums/y24/leoos11/error.jpg[/IMG]

Im also getting this error when I try to load the iPod from gtkpod

[IMG]http://i2.photobucket.com/albums/y24/leoos11/Screenshot-Warning.png[/IMG]

Im seeing similar errors for non PPC users but any of the fixes I try from there dont seem to help me out

---

### Post by leoos on 2007-05-22
I managed to get my iPod to mount onto the desktop using this advice from another thread

> Well it turns out I had accidentally changed some of my iPod's settings. What I did was go into Nautilus and go to "Computer" then right click on the iPod icon, then tab over to "Drive" and "Volume" and erase all the mount options, etc. in both tabs. Worked fine after that!

I still have the problem with gtkpod though :(

EDIT: Scratch that, my gtkpod is working now too, now to get my firewire drive mounted

---


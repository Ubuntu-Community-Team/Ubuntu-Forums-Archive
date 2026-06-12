---
title: "Impossible to partition"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Nitro2985 on 2007-07-15
I've tried running the installer in the live CD of Ubutnu, I got an error saying that it was unable to make an EXT3 partition.  This was done on a clean hard drive, devoid of even a file system (though that hard drive was not a primary partition, if that matters at all, I don't know if you can have two hard drives as primary partitions, but whatever)

Anyway, I then tried to resize my windows partition on my main hard drive.  I went into the gparted app while running Ubuntu via the live cd and attempted to resize it and then create a new ext3 partition in the opened space.  This too failed, it was unable to resize the windows partition and failed before even starting that.

I'm honestly getting really frustrated.  I can't run gparted from it's own live cd because I have an Nvidia graphics card, and the cd doesn't have the drivers needed to use the card, so I can't see what I'm doing in the prompt.  Is there anything I can do to get Ubuntu up on one of my hard drives?  Or would i be best served simply returning to windows for lack of support for my hardware?

---

### Post by wolfen69 on 2007-07-15
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) has drive management tools. great cd. and its free.

---

### Post by mikewhatever on 2007-07-16
Which version of gparted do you use? I have an nvidia card and the cd works very well.

---

### Post by Nitro2985 on 2007-07-16
The most recent one, I just downloaded it tonight off their sourceforge page.

Regardless, I finally got Ubuntu to install by making a small EXT3 partition on my empty hard drive and then telling Ubuntu to install using that whole disk (oddly enough, after checking my partitions upon reentering windows, I found that it had only used the space I provided for it in my manual 10 gig partition of that disk)

Anyway, that leads me to my next problem, I can't seem to start up Ubuntu from that hard drive.  I switched my primary startup drive to a hard disk and windows started up right away, it didn't enter Grub at all.

I then switched the order of my harddrives to check for boot info to have the one with Ubuntu on it first.  It said "failed to load operating system" or something of the sort when I restarted again after that.

Do I need to install Grub manually?  I thought it overwrote the MBR when it installed Ubuntu.

---

### Post by Nitro2985 on 2007-07-16
bump

---

### Post by bren on 2007-07-16
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---


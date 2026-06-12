---
title: "Cleaning and reinstalling ubuntu"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by Dylock on 2007-09-09
Alright here is the scoop, my night started with an xserver crash as a result of something going fubar with an nvidia driver or module.  In the process of fixing that it seemed the only thing to do was upgrade from edgy to fiesty ( the upgrade was foobared as well and it wont boot into the new kernel)

however i can still tell grub to go into my old kernel ( and using the nv driver instead of nvidia for X)
now i could be content with this but by not having the nvidia driver i lose all the gaming capabilities for my computer

so i think ive decided to redo ubuntu to get it clean and away from the nvidia problems and botched upgrade ( i dont want to keep building on a system that might not be stable)

So now to the point, im going to be reinstalling ubuntu

Now I have two hard drives. The primary hard drive is what ubuntu is installed on and my /home directory is located at. I also have a second harddrive that has a link in /home which contains all my data in it (music movies, pictures, important stuff).  I can part with all my old applications and games, they can be replaced, but the data cannot. My goal is to reinstall and format the primary harddrive, but keep the second harddrive intact. Is this as easy as just adding an entry in my fstab when i finish the install on the primary?

Or is there more that needs to be done.

I'm going to make a copy of my /home to the data harddrive incase I can restore it on the new install later on, but before I do any of this I want to get the opinion of some other people. The thing I hate most about operating systems is that they always seem to fubar on me when i upgrade.  It happened with XP which caused me to switch to ubuntu in the first place. 

Lessons ive learned: NEVER upgrade :D (just kidding of course, i either botched something or just have bad luck)

---

### Post by ts51 on 2007-09-09
Go into the Ubuntu 7.10 Feisty Fawn live CD.


>>Go to the Partition Manager

>>Format the HD w/ Ubuntu on it

>>Reformat it so that it is the 'ext3 filesystem' (without quotes) and save changes.

>>Go to desktop and hit install...


There you are, reinstalled Ubuntu while keeping your HD the same....

---

### Post by Dylock on 2007-09-09
alright then i just have to add the harddrive back into the fstab to access it again?

also i dont know if this matters in the formatting process, but i have a hardlink in my home directory to my second hardrive, will this caus it to delete any info on the second hardrive when its formating?

---

### Post by Dylock on 2007-09-09
nevermind it isn't a hardlink just the point that it was mounted too,

im copying all important folders form my home to the second harddrive, live CD is almost done downloading

if i can get this done in 1 day i would be pretty thrilled, then i have more time to get other applications back up

---


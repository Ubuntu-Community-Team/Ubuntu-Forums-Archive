---
title: "Unable to install from Live CD"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by andrewlinn957 on 2007-02-27
today i tried to install Ubuntu 6.10 from the liveCD. The comp im trying to install it on is has a fairly crappy old Windows Me installation. Before trying to install Ubuntu i did the usual and scanned the HD for errors and then did a defragment. This told me that some disk clusters (a handful) were corrupted and couldn't be written to. 

So, to the installation.

I ran the disk and checked it to make sure there were no errors on it. There were none. Then i chose 'start or install ubuntu.' After the Ubentu loading bar came up some text appeared

> 
Activating Swop..
mount: function not implemented 

checking file system...
fsck 1.39


then it continued to run. Eventually i got to a part of the GUI - a pointer came up as the a small window which said ubuntu on it. These eventually dissappeared and the pointer stopped working, so i restarted. On one occasion i got an error saying that GNOME didn't implement.

I then looked at the help section, and decided to run
> boot: noapic noalpic
because it seemed kinda relevent

subsequently i got:

> 
Buffer I/O error on device hcd logical block
Buffer I/O error on device hcd logical block
squashFS error:sb_bread failed reading block
squashFS error:Unable to read fragment cache block (some numbers)
                      : unable to read page, block (some numbers)

 

Are the errors on the drive causing this? Would either using an alternate install CD or installing on first disk help?

Also, i ran mem test and the % pass was quite low but i didnt finish the whole thing. don't know if that matters. i have 256 MB ram, 1.1 Ghz Celeron. 

thanks

---

### Post by nudnik on 2007-02-27
> **andrewlinn957 said:**
> today i tried to install Ubuntu 6.10 from the liveCD. The comp im trying to install it on is has a fairly crappy old Windows Me installation. Before trying to install Ubuntu i did the usual and scanned the HD for errors and then did a defragment. This told me that some disk clusters (a handful) were corrupted and couldn't be written to. 

So, to the installation.

I ran the disk and checked it to make sure there were no errors on it. There were none. Then i chose 'start or install ubuntu.' After the Ubentu loading bar came up some text appeared



then it continued to run. Eventually i got to a part of the GUI - a pointer came up as the a small window which said ubuntu on it. These eventually dissappeared and the pointer stopped working, so i restarted. On one occasion i got an error saying that GNOME didn't implement.

I then looked at the help section, and decided to run

because it seemed kinda relevent

subsequently i got:



Are the errors on the drive causing this? Would either using an alternate install CD or installing on first disk help?

Also, i ran mem test and the % pass was quite low but i didnt finish the whole thing. don't know if that matters. i have 256 MB ram, 1.1 Ghz Celeron. 

thanks


If you mean to say that memtest showed errors, perhaps many errors, then, yes, that is very important indeed. If the former is the case, then you likely have bad memory, although a fault in the motherboard does sometimes cause errors. 

Additionally, it sounds as if you need a new HD drive as well. You may want to consider a new PC. 

If a new PC is not an option, try some new memory (if there are errors from memtest), and clean your optical drive (cd or dvd drive) using a cleaning kit by a major manufacturer. If you still get HD drive errors, replace the HD as well. You should be able to find one on Ebay for about $30.

---

### Post by Quillz on 2007-02-27
Try a 6.06 Live CD. I have never been able to boot up 6.10 on a Live CD, nor have a lot of people. There's something wrong with them, I would assume. Also, did you try to boot up in safe graphics mode?

---

### Post by amaroKer on 2007-02-27
If I understand correctly, you're having problems loading the LiveCD environment?  I'm not sure if there is a lot you can do.  Yesterday, I was barely patient enough to load Live Ubuntu 6.10 on an old Pentium 4 2GHz, so I'm sure your Celeron is having a pretty hard time with all the data.  I think the alternate CD is for situations where the Live environment is unnecessary and/or impractical.  G'head and try the alternate CD, or maybe even give xubuntu a shot.  It is a lot more minimalistic and therefore suited for more "experienced" hardware if you get my drift.  Good luck either way, and I'm sure there are a billion other ideas out there from more linux savvy people than myself.

Logan

---


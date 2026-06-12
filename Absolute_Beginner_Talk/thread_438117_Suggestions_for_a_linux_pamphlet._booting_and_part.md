---
title: "Suggestions for a linux pamphlet. booting and partitioning"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Limitlesschannels on 2007-05-09
So, I have been working on a new zine (like a pamphlet; a magazine, but cheaper and more DIY.  wiki it if you still aren't getting it) to introduce people to linux.  I figured i would just download, burn, and tape a installation disk into the back of each issue and have various parts on installing pretty basic software, basic commands, basic windows/mac comparisons, and all that other usual intro to ubuntu stuff.  But the one issue that I find the hardest to explain to someone who i am not directly talking to is the booting and installation of the cd.  Sure i can suggest the live cd, but there isn't a very simple way of making sure that their computer automatically boots to their cd-drive before hardrives.  If i were to tell them to just stick it in and boot, not all are set up for that first and considering the widespread types of BIOSes (plural?), i doubt i could simply say "press Delete" or "press F8" to enter the BIOS and tell it to boot from a disk.  Any suggestiosn on that?

And in the case of partitioning, I figured i could just give a brief explanation on what it is and probably just slap a URL in to offload the task to their own self-discovery.  I really like partition magic, but I doubt they want to pay/crack it to use it, plus the complexity is again far higher than i would wish to present.  What are some free and super-user friendly partitioning software available?  I doubt GPartition is ported, but honestly haven't looked.  Unless it is on the live cd, then maybe it would make this task a whole lot easier... hm, if not future suggestion: PUT GPARTED ON LIVE CD FOR EASY PARTITIONING. but i doubt it is that simple.  

comments/questions/suggestions?

---

### Post by nanotube on 2007-05-10
gparted is on the livecd. :)
and, even if it weren't, one could simply apt-get gparted, qtparted, or whatever other partition editor one prefers, while booted to the livecd, and use it to partition.

---

### Post by Sef on 2007-05-10
> PUT GPARTED ON LIVE CD FOR EASY PARTITIONING

Go to [Gparted's]("http://gparted.sourceforge.net") website to download the latest Live CD version.

---

### Post by Limitlesschannels on 2007-05-10
Yay, thanks guys, that's good news.  Do i need to download the liveCD off Gparted's site then, or is it on the standard disk?

---


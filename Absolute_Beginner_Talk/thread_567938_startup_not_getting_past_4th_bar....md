---
title: "startup not getting past 4th bar..."
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by addict on 2007-10-05
I have been running ubuntu on my windows laptop from wubi the last day, and everything has been going pretty well (might get wireless working today), however, when i went to turn on my computer today, and selected ubuntu from the operating system list, ubuntu go to its screen with the black and orange progress bar. It got bast like the 4th little block, so it was like 4 blocks full and just a slit, like 1/5th of the 5th block, and it just hangs there. I turned off, turned back on, tried it again, same thing. 

What should I do? If i need to run something at that initial DOS prompt, could you give me specific directions on how to do so, because although I am good with computers, I am new to linux and never used dos prompts or anything like it very much.

---

### Post by skymera on 2007-10-05
can u go into recovery mode and try?

then

/etc/init.d/gdm start

---

### Post by addict on 2007-10-05
ok, but how do i get into recovery mode?

---

### Post by LowSky on 2007-10-05
at bootup you should see something that says

" Starting Grub"  press delete i think will get you into the menu... i think... im at work and not near my ubuntu machine

---

### Post by philinux on 2007-10-05
On mine its esc key then you will see all the boot options just pick the first recovery one. On mine its the second from the top

---

### Post by addict on 2007-10-05
ok i hit escape and got into the list of kernals, and went into first recovery mode i saw, there were too, .16 and .15, did .16, so it runs something, a lot of things, says "Done." then it goes into checking things for booting up does that and then just stops at what looks like a line of just "=================="

Then i could not type anything and tried hitting escape, was confused. Then i jsut hit the powr button, tried to load up again and see if it worked, nope. Tried again recovery, again, same thing, couldnt type.

ughhh

---

### Post by philinux on 2007-10-05
Sounds like something really messed up. I'd get the live cd have look around see if anything messed up and backup your home folder just in case of worst case - reinstall. Maybe someone else can help

---

### Post by addict on 2007-10-05
and i was really likin ubuntu too. Do you think this is because i was running it using wubi? Also, i have another queston, if you get a live cd, how do you partition your hard drive- does it do it for you or do you have to- with wubi of course, it was real easy. However, with a live cd, how easy is it?

A combination of this and problems getting wireless working, all in one day, really steers me clear of linux.

---

### Post by philinux on 2007-10-05
Never used wubi as you can see from sig am dual boot.

I'd already backed up my home folder following a hard drive failer then I tried livecd it has gparted installed but I used a gparted live cd. Its quicker. mines an old machine. Then used live cd to reinstall. and copy back home folder.

Before giving up all hope, did you install something or uninstall something before this cock up happened

---

### Post by addict on 2007-10-05
yea i was installing a good amount of things in relation to my wireless, and also i think i installed automatix.

[http://ubuntuforums.org/showthread.php?t=567490](http://ubuntuforums.org/showthread.php?t=567490)

---

### Post by philinux on 2007-10-05
automatix is known to break things

---

### Post by addict on 2007-10-09
yea i know... any way to get rid of it through the kernal?

---

### Post by addict on 2007-10-26
> **addict said:**
> yea i know... any way to get rid of it through the kernal?

.....

---


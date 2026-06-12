---
title: "Live install problem"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by femens on 2007-04-29
Trying to get the "Live CD" version of 6.06 to run on my Compaq Presario desktop.
It starts OK and runs through the usual steps, then the screen goes dark, then a single
underline character shows in the upper left corner and nothing else happens. Looks like it may be the dursor for grub, but I ain't Linux-wise enough to be sure and I certainly don't know how to make things go further.

Any suggestions???

---

### Post by bobplano on 2007-04-29
have you tried checking it for errors? it's a big file so burning at a fast speed will make errors. try burning at 4X or less. also check the md5sum of the .iso to make sure it's ok.

---

### Post by femens on 2007-04-29
I'm using the disk shipped to me. Same disk has installed OK on other systems, but the Compaq is the one I want to partition and make a permanent install on. Figure I'd better see a live install work before I go that far with it.

---

### Post by starcraft.man on 2007-04-29
It would be easier to diagnose what is wrong if you knew at which step exactly in the live install you get this blank screen? Is it before or after partition for example... try to locate it precisely.

In this instance though I would recommend going to the alternate, when in doubt it usually works.  [Link]("http://releases.ubuntu.com/")

Just follow the easy steps, when ya get to partitioner make sure to make approx a 10 gb / (root) drive, a 2-4 GB swap file and the rest should be a simple /home ext3 drive. Hope that helps.

---

### Post by bobplano on 2007-04-29
i don't think this is a hardware problem, but go ahead and post your specs here. i had a laptop that was supposedly able to run linux (enough ram, stuff like that) but it didn't.

---

### Post by juantovarm on 2007-04-29
Why not download an alternate cd image, burn it a 4x and install it via TEXT mode?

---

### Post by jerrylamos on 2007-04-29
Have you tried booting CD Live, push F6, then deleting the words "quiet splash"?  You might wind up with some indicative messages at the last before it hangs.  If there's anything just before it stops try posting it here.  

Cheers, Jerry

---

### Post by femens on 2007-04-29
I tried the last suggestion & maybe have some more useful information to offer. The boot seems to proceed normally with the progress messages posted until it reports "Configuring some drivers"

That message stays there for a long time, then the screen goes black, then comes the following sequence (each mesage peceded by "Init:"

Runlevel 2
Id "1" respawning too fast: disabled for 5 minutes
then the same message with Id 2 through 6
 Than Init: No more processes left in this runlevel

Then after 5 minustes it repeats the same 6 messagers and does the same every 5 minutes thereafter.
:

---

### Post by [S|G] on 2007-04-29
Take a look at this thread: [http://ubuntuforums.org/showthread.php?t=18785](http://ubuntuforums.org/showthread.php?t=18785)

---

### Post by femens on 2007-04-30
HooRay!!! YaHoo!!

I think I have it solved. First thing I did was to download the 7.04 desktop version, burned it to a CD, then tried to boot from it. It scrod up in much more spectacular ways than the "official" 6.06 disk.

I next told it to check the disk for errors. It claimed there were 5 files with errors. Unbelieving, I moved to a different machine -- started by asking for an error check on the disk. Reported NO ERRORS. Then tried booting it and it went with no trouble -- all the way. So I went back to the Compaq machine I want to use it on and tried it with one difference. I had been using the machine's CD/DVD-RW drive. It also has a plain old read-only CD drive, so I tried booting from it. Success -- no probllems. Curious, I went back to the 6.06 disk and tried it in the same drive -- no problem. So I'm getting errors on the wondrous CD/DVD-RW drive. 

Anyway, that problem seems to be solved. Now I have another question, but think I'll start a new thread with it and let this one die a peaceful death.

Thanks to everybody who responded!!!

---


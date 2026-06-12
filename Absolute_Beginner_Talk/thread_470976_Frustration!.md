---
title: "Frustration!"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Kitzune on 2007-06-11
I stumbled upon ubuntu a while back, and immediately wanted to try it out. I did some more research, downloaded the live CD, ran it, was really impressed, etc.
However, I needed to have it dual boot with XP, since there are no drivers for my printer (Dell AIO 922) in linux, period (I looked and looked and looked, but everywhere said that lexmark and dell printers just aren't supported)

I looked up various ways to dual boot ubuntu and xp, and of course I didn't check out whether or not ubuntu did this automatically, which could have saved me a bunch of time.

I put the live cd back in, but I just can't get ubuntu to install! I get different errors, or just nothing at all, and I have to admit, it's really frustrating.

I'd love to try out ubuntu, but if I can't get it to install next to windows (they don't even have to share files) I'll just leave it...

I was hoping that someone could explain to me what's going on with the install. The errors I get say that the space on the drive is too small, but its well over 30 gigs, so I don't see the problem...
Thanks for the help

---

### Post by Inxsible on 2007-06-11
Put in the live CD. Open up GParted which will show you all your drives. Take a screenshot and post it here.
 
You are probably trying to install it in a partition thats too small maybe.

---

### Post by Kitzune on 2007-06-11
Okay.
I'll do that, and get back to you soon.

Thanks!

---

### Post by Inxsible on 2007-06-11
As a side note: Did you defrag your XP partition from within XP a few times?
 
If not, I would suggest you do that too while you are at it. Atleast 3-4 times..just to be sure.

---

### Post by Nythain on 2007-06-11
or possibly dont have enough free unpartitioned space... ie the whole hard drive is one big ntfs partition???

if thats the case, i would suggest booting up windows... defragging, then running partition software (partition magic, but its commercial, i dont know any free software off the top of my head) to shrink the ntfs partition opening up enough unpartitioned space to install ubuntu onto
then load the livecd, start the installation, and tell it to automatically partition available FREE space on the drive

---

### Post by johnny4north on 2007-06-11
have you cleaned up your drive(delete unwanted files) and defraged your drive.  if your drive is fragmented and has a large recycle bin and swap file.  this will leave very little room for ubuntu.

---

### Post by indytim on 2007-06-11
I would suggest first to check the integrity of the CD you made from the iso you downloaded.  The easiest way to do that is to boot to the LiveCD and exercise the "check CD" option (or words to that effect).  If you have a bad download/burn of the LiveCD that will only add to your frustration of trying to install.

If that's clean then either load the GParted from the LiveCD or better still get a dedicated copy of GParted Live and burn it to it's own CD.  Then boot to it and do your partition setups before installing Ubuntu.

Report back here on results and subsequent questions.  The community is here to make your transition as easy as possible ok?

IndyTim

---

### Post by Kitzune on 2007-06-11
I'm fairly certain that Nythain is right.
My drive is one big partition, the result of an error trying to install Ubuntu previously.
I believe I tried partition magic, which had a horrible affect on windows' understanding of itself, so after a wipe, I made the drive one big partition.

Is there a way to change the partition size without ruining windows while using the windows install CD?


Edit:

Also, I defragged the disk several times (I think 6) and the result was always the same, everything looked normal aside from one clump of files somewhere in the middle...


and thanks for your help, everyone. It's nice to know that there's a community like this out there

---

### Post by johnny4north on 2007-06-11
when the xp install cd completes it boot to start cd install it will look for a previous windows install[it wont find], then it will continue to a place where it selects an drives partition.  delete partition and resize to the size you want, then continue install.  ubuntu should be installed second.  here is good site for multi OS setups - [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)    good luck :)  yes, oh, im sorry i thought you were reinstalling xp... its best to resize the partition when installing ubuntu. my bad :(.

---

### Post by Kitzune on 2007-06-11
Won't that delete windows?

---

### Post by johnny4north on 2007-06-11
oh, im sorry i thought you were reinstalling xp... its best to resize the partition when installing ubuntu.  my bad.:(

---

### Post by Nythain on 2007-06-11
yeah, dont do it that way... that will nuke your current windows install... unless you dont mind re-installing windows (bah on that).

im not sure if GParted (the partition editor ubuntu installer on the livecd uses) can shrink ntfs partitions or not...

like i recommended, i would seriously try to find a nice piece of partition editing freeware for windows and resize from there... that is if you can boot into windows... i didnt make much sense out of your failed partition editing attempt explanation, all i cought was "created one big partition"

---

### Post by hsweet on 2007-06-11
you need an empty partition to install ubunutu into .  Or easier, a second hard drive.  
Lacking a 2nd drive, you will need to use gparted to re-partition your windows drive.  It's on the live cd or you can download the linux rescue cd.  Make sure you defragment windows first.  (It's worked fine for me, but thats no guarantee, so back up whatever you don't want to lose)
Once you've done that you can install ubuntu into the empty space.
You will get a (grub) menu that will let you choose which os to start.  Ubuntu is first but you can change that.  (another question, but you might like Ununtu better)

---

### Post by bodhi.zazen on 2007-06-11
LOL

1. Back up any data on your windows partition. It is rare for you to "nuke" your windows install, but it is possible, two hard drives or no.

2. You can resize your ntfs partition with gparted.

See these links :

[Basic partitioning](http://ubuntuforums.org/showthread.php?&t=282018) 

[gparted](http://www.howtoforge.com/partitioning_with_gparted)

That link ^^ used gparted the live CD, but it the same with using the ubuntu desktop CD.

IMO the best install guide is here : [Install Ubuntu, Dual Boot](http://www.psychocats.net/ubuntu/installing) ~ That is the psychocats page. The wiki page johnny4north gave you above is good to.

---

### Post by Nythain on 2007-06-11
hehe.. the nuke was in reference to his first post about deleting the partition during the xp installation process and creating a new one... he just corrected himself quicker than i could reply :)

---

### Post by bodhi.zazen on 2007-06-11
> **Nythain said:**
> hehe.. the nuke was in reference to his first post about deleting the partition during the xp installation process and creating a new one... he just corrected himself quicker than i could reply :)

:lolflag:

Anyways, when advising a new user :

1. Defragmenting is necessary. You often will not be able to resize if you do not. However, defragmenting more then twice is probably a waste of time (Windows can only defragment itself so much you know).

2. Don't forget to advise backup. Installation of a new OS is major (transplant) surgery :) Erasure (formatting) of the windows partition is one or two mouse clicks away and new users often do not understand (Linux) partitioning (so it may be easy to format and install into the wrong one).

---


---
title: "Built my own computer sorta but having issues"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by ckc07 on 2007-04-18
I installed a new motherboard. My old (2 months old) HDD is fine ( I was running it in another machine so I know its cool).  When I try to run UBUNTU live it only works in SAFE GRAPHIC MODE. If I try regular it gets jammed on "Loading kernal " thing
So my HDD was setup for my WIN XP machine and has windows on it. I try to stick the Win XP CD in and boot from that and it never gives me the option to format the stupid drive.  It runs setup for awhile then freezes and doesn't finish or ever get to windows .I have a partition in this and only a tiny piece of the drive is accesible by linux (Crap). So I really need to format, repartition and get this so it can be a dual boot. I have to run windows because of the software I use for work.  So now I can get into Ubuntu (yey I guess) but how can I format the drive then reinstall windows and make this a dual booter?
Also if I mostly want to use linux shouldn't I actually install UBUNTU?  How do I do that? I want to be able to do internet, email and Ipod and photo stuff in linux then use Windows for my tax software.

Anyone want to help me?

Hopefully!!
THANK YOU FOR ANY ADVICE...

---

### Post by jordanmthomas on 2007-04-18
Windows will refuse to install on any drive that is not the first master hard drive it can find.  
You should probably make sure your drive is master.  Then, see if the Windows installer will see your drive.

(If you do get Windows installed, you'll need to fix grub)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Grub](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Grub)

**edit** and I'm not sure I understand your problem with Ubuntu.  Have you got it installed or not?

---

### Post by Squeak2 on 2007-04-18
well if its dual booting you need help with check out this video tutorial [http://video.google.com/videoplay?docid=-2369893842637434537&q=ubuntu+dual+boot](http://video.google.com/videoplay?docid=-2369893842637434537&q=ubuntu+dual+boot) it is very in-depth and it worked for me 100% and is real easy to follow.

---

### Post by crispy_420 on 2007-04-18
So are you starting from scratch here?

What I would do is install xp first. Like what was said before, XP must reside on the master drive. But that is only an issue if you install on IDE drives, SATA has no master/slave. So if you have an IDE drive, make sure it is the master if you have two drives. Check the jumpers on back of drive. If it is a single disc system, depending on disc make it could be cable select, master, etc. In that case, check with drive's maker as to setup.

So both OSs on master? You'll need to partition it. I like a little liveCD for this called [GParted]("http://gparted.sourceforge.net/livecd.php"). That way you can partition before OS install. Depending on what you need of each OS, decide how much space you'll need for each. Also keep in mind, the XP install will take a good chunk of space.

This should get you going for now. See if this helps and we'll go from there.

---

### Post by itzpapalotl on 2007-04-18
If I understand the question right, you have a functioning Windows XP system, and you want to install a functioning Ubuntu system, and in order to that you want to use the live CD which is giving you some trouble.

Fist off. If you Downloaded and burned the CD yourself, there is a fair chance that the CD, rather than your machine is borked. Try burning a new one at maybe 2x speed max. It will take a while, but chances are it will come out right. 

Also make sure that you have the right install for your chip set. If you have a standard intel Pentium or Celeron something, you will want the i386 CD if you have an AMD  64 you'll want the AMD64 disc.. etc. 

Before you do your install, make sure you back up your valuable information. It's not unheard of to blow the partitioning, and lose some or all of your data. Just back it all up. For real.

Once you are backed up... DEFRAG your windows drive. In fact defrag it two or three times just to make sure that everything is all pushed over to one side. The UBUNTU disc of your choice will have a partitioning utility. Be careful when you are using it.

There are comprehensive, and easy to follow instructions on installation here:
[https://help.ubuntu.com/](https://help.ubuntu.com/)

If you still have trouble with your live disc after buring it again, report back with the type of graphics card you are running.

Good Luck!

---


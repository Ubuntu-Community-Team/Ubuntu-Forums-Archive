---
title: "Choppy graphics with gutsy"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by ciatsd on 2007-11-16
Hi,

I just recently upgraded from feisty to gutsy and the graphics have become incredibly choppy.  I'm not sure what went wrong, but here was the order of events:

1. I upgraded to gutsy without completely updating feisty - I read that I needed to do this after the fact - oops.
2. The windows manager did not start up initially so I added compiz onto the startup session - this brought the windows back.
3.  The graphics are and have been very choppy since I upgraded.  This was not the case in feisty.  Note it is also choppy when I run metacity instead of compiz.  Beryl used to work fine in feisty, but I never used compiz.

Some information:
lspci says:
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

xorg.conf says:
Section "Device"
        Identifier      "Intel Corporation Mobile Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

I'm not sure what other information would be useful...


Anyway, any help would be GREATLY appreciated.  I really don't have much of an idea of what to do and the current state is bordering unbearable.  Though the 3d graphics would be nice to have, I would be content with just a non-laggy windows manager.


Thanks.

---

### Post by Pixcalcis on 2007-11-16
i had the same problem though it wasnt just choppy graphics, everthing was running slower.  .is your computer a dual core computer?  if so you may want to look under system monitor and see if it is recognizing your second core.  Thats what happened to mine...the upgrade to gutsy used a 386 kernel which i dont think supports dual core..so my computer was running at a very slow rate. Anyways try installing the generic kernel instead through synaptic if this is the case.

---

### Post by ciatsd on 2007-11-16
It seems to recognize and be using both cpus...

I remember this being the case in feisty also.

If there are any other ideas I would be much obliged :\

This window problem is painful..

---

### Post by jaybombalous on 2007-11-16
when u upgrade u need to also reinstall any video drivers u may have had installed. I dunno, but compiz can be a pain, I would turn it off.

---

### Post by ciatsd on 2007-11-16
I have the same experience running metacity...

I've looked around for a driver update, but couldn't find a promising one.  Do you know of any good source for ubuntu drivers?

Thanks.

---

### Post by mooseydoom on 2007-11-16
Have you tried this:

e) Intel cards - clumbsyness and/or slow Desktop respond.
install : libgl1-mesa-dri

taken from the quickguide
[http://ubuntuforums.org/showthread.php?t=583007](http://ubuntuforums.org/showthread.php?t=583007)

---

### Post by ciatsd on 2007-11-16
Hi mooseydoom,

I did try to install that but it appears to already be installed.  I read through the linked thread and it seems that someone else had a similar problem.  It's nice to know I'm not alone with this.  Regardless, it is still unsettled.  I'm going to try some other things and I'll report back if anything works.  I'm still open to any suggestions...

On another note, the response times on this forum are incredible....

Thanks

---

### Post by ciatsd on 2007-11-16
Finally got it to work.......

The solution I eventually found was here:
[http://ubuntuforums.org/showpost.php?p=3416144&postcount=15](http://ubuntuforums.org/showpost.php?p=3416144&postcount=15)

This was apparently a problem with Intel integrated graphics drivers and xgl, at least that was the case for me...

Here's the thread that had the info I was seeking:
[http://ubuntuforums.org/showthread.php?p=3560585](http://ubuntuforums.org/showthread.php?p=3560585)

Thanks for the help!

---

### Post by jaybombalous on 2007-11-16
Mark this thread as solved please!

---


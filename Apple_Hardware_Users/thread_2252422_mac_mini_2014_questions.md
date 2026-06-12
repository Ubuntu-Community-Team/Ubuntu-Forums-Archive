---
title: "mac mini 2014 questions"
date: 2014-11-11
forum: Apple Hardware Users
---

### Post by Rahabib on 2014-11-11
I ran a search but much of the information was either *outdated* or did not address what I needed.

I may be inheriting a new 2014 mac mini.  I already have a macbook pro and a thunderbolt display.  I am thinking I will place an ubuntu partition on the mac mini and will use that as my primary desktop and my macbook as my secondary computer.  That said, I am aware of some of the issues with thunderbolt, but I may be able to work around them, but I have some questions.

1) will the thunderbolt display display at all? - it seems some people say it will, but there is a high CPU cost.  Has this been fixed in 14.04LTS or 14.10? (if it will work at all).
2) if it does work, will the hub work for ethernet and USB hub (keyboard and mouse plugged into it)? - I know it will not have hot plugging (unless this too has been fixed), but this will be plugged in at all times anyway.
3) are there any driver issues I may need to be aware of for the 2014 model? will wifi, etc. work.
4) assuming its not worth the hassle of using thunderbolt, how well does it perform *avoiding thunderbolt* and using HDMI and built on ethernet and using a second HDMI monitor (I am sure theres an HDMI monitor somewhere around that nobody is using).

Thanks for any help!

---

### Post by slickymaster on 2014-11-12
*Moved to the ***Apple Hardware Users*** sub-forum*

---

### Post by Rahabib on 2014-12-16
Ok, I bought the mac mini 2014.  Everything supposedly works, the only issue is that it locks up constantly.  I can't seem to track down the issue.  It will lock up after about 2-5 minutes or sometimes at login.

anyone else have this issue?

I have the 2.8GHz Dual-Core Intel Core i5 (Turbo Boost up to 3.3GHz) 
16 GB 1600 DDR3
Intel Iris 1536 MB
512 SSD version partioned in half with 8gb swap and roughly ~241 GB for /

---

### Post by este.el.paz on 2014-12-17
> **Rahabib said:**
> Ok, I bought the mac mini 2014.  Everything supposedly works, the only issue is that it locks up constantly.  I can't seem to track down the issue.  It will lock up after about 2-5 minutes or sometimes at login.

anyone else have this issue?

I have the 2.8GHz Dual-Core Intel Core i5 (Turbo Boost up to 3.3GHz) 
16 GB 1600 DDR3
Intel Iris 1536 MB
512 SSD version partioned in half with 8gb swap and roughly ~241 GB for /

@Rahabib:

You haven't mentioned which version of Ubuntu you have installed that is locking up . . . and what are the features that are "locking"????  But, I would say that others have had any issue that you are having and searching online or this forum should bring lots of reading that may provide some insight . . . .  I personally have no experience with a Mac Mini . . . just PPC & MBPro . . . .

e.e.p.

---

### Post by mdellertson on 2014-12-19
I've installed Ubuntu 14.04 on a MacMini late 2012 model.  I have two Thunderbolt displays.  The first display, the one plugged directly into the computer, works very well.  No work was needed, it just worked immediately after installing Ubuntu.  But, the second Thunderbolt monitor won't come on at all.  

I read another thread posted 11 ish months ago.  It was suggested installing new Nvidia drivers might solve a similar issue.  But that post was regarding a MacBook pro connecting a Thunderbolt display.  

Does anyone have any ideas regarding getting a 2nd Thunderbolt display to work using Ubuntu 14.04?

---

### Post by Rahabib on 2014-12-19
> **este.el.paz said:**
> @Rahabib:

You haven't mentioned which version of Ubuntu you have installed that is locking up . . . and what are the features that are "locking"????  But, I would say that others have had any issue that you are having and searching online or this forum should bring lots of reading that may provide some insight . . . .  I personally have no experience with a Mac Mini . . . just PPC & MBPro . . . .

e.e.p.

thanks for the reply.

I am using 14.04.  The system locks up by doing anything, even just moving the mouse or not doing anything at all. I can be just letting it idle and then try to move the mouse and find that its already locked up.

Just searching around, I have not found a fix.  the nocq fix doent seem to work, and that was the closest thing I could find to my issue.

Thanks again.

---

### Post by este.el.paz on 2014-12-20
> **Rahabib said:**
> thanks for the reply.

I am using 14.04.  The system locks up by doing anything, even just moving the mouse or not doing anything at all. I can be just letting it idle and then try to move the mouse and find that its already locked up.

Just searching around, I have not found a fix.  the nocq fix doent seem to work, and that was the closest thing I could find to my issue.

Thanks again.

@R:

So, I'm assuming you mean that the GUI locks up or "freezes"??  And if you use the CLI it works OK??  I and other did have this issue with 14.04/10 . . . try to either find or configure an xorg.conf file for your computer . . . .  You should find threads here from me that might offer some help "desktop freezes" or something like that.  Or the wiki, or even the PowerPCFAQ might show you have to use the CLI to make an xorg.conf file.  Or search the web for "linuxjemac" and find his page that has xorg.conf files for your computer and "wget" it and then "mv" it into its proper place . . . .  That should take care of the "freezing" issue . . . .  For my G4 iBook 14.04 still has "jerky" movement when dragging pages around . . . but, use-able for the most part . . . .

e.e.p.

---

### Post by Rahabib on 2015-01-06
In OSX, it does not lock up at all.  However, I can't turn off sleep and when it does go to sleep it just turns off.  I disabled sleep, hibernate, tried a million other things.  After doing some investigation it turns out that it very well may be hardware related, which may explain the issues in Ubuntu as well.  I am going to take it to the Apple store to get it fixed/replaced and then give Ubuntu another whirl.

---

### Post by Rahabib on 2015-01-16
Got the mac mini back, its not hardware.  It seems that it Ubuntu simply won't run well on the mac mini late 2014.

---

### Post by kevdog on 2015-01-17
I guess you always could try Ubuntu in a VM.  Yea its not like native, however if it doesn't run natively, then I don't know of another option

---

### Post by Rahabib on 2015-01-20
> **kevdog said:**
> I guess you always could try Ubuntu in a VM.  Yea its not like native, however if it doesn't run natively, then I don't know of another option

Thanks, I do have parallels and it works fine enough, but it would be great to have it not run in a VM.

---

### Post by jgamann on 2015-09-24
Hi, I just try to install ubuntu 15.04, xubuntu 15.04 and xubuntu 15.10 beta 1 and it doesn't work for me.
I don't have wifi in the installation and I haven't can continue with the installation.

It have been a pity. &#128532;

---


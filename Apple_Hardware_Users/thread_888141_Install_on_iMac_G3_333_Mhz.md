---
title: "Install on iMac G3 333 Mhz"
date: 2008-08-12
forum: Apple Hardware Users
---

### Post by clayton911 on 2008-08-12
I've checked out the forums on the subject and still haven't been able to run Ubuntu on my iMac.  It's running Classic and I get to the prompt and have tried all of the commands like "live" and "live-nosplash" and all have the same effect.  The Ubuntu screen loads with the Ubuntu text and the scrolling bar across the bottom and it does that for a while and then just goes to a blank screen with no cursor.  I cannot get to any other command line or terminal and have no experience coding in any platform.  It would be great to get an OS that runs firefox and open office on an all in one machine that only costs $30.00.  I believe the iMac would be a great launching pad for Linux to those who can only pay $50.00 but will get a screen, computer, CD player, speakers, USB ports, Ethernet, and access to wright and read their office files as well as photos, music, etc.  I want to mass market Linux using the iMac but I need to be able to get Ubuntu running on it first.  Please help in any way that you can so I can get this thing started.  Thanks a lot.  Ubuntu is the Future, Apple and Microsoft are now the past.  

Peace.

---

### Post by stream303 on 2008-08-13
While I applaud your decison to put an older computer to use, the Apple G3 iMac represents probably the worst one to "mass market" to newcomers to Linux, even if they are on a shoestring budget.

But first, to answer your question, you need to use the "alternate" installer to get the system on your disk.  Then, you'll have to use rescue-mode or linux-single mode to get into the /etc/X11/xorg.conf file and manually edit in the proper vertical and horizontal monitor freqs as detailed in the faqs.  You'll also probably have to manually edit in your video driver.

Problems you are going to run into:

1) The motherboard batteries on the iMacs are nearing end of life, and it is likely you will run into the "date bug" and have to manually fix it until you replace the battery.  The battery is about $15.00 last time I checked at various retailers, so there's half the purchase price of the G3 iMac right there.

2) While 333mhz on a G3 is roughly equivalent to a 666mhz Intel box for comparison, you haven't mentioned how much ram you have.  To be somewhat useful, you'll want at least 256mb, preferably more on board.  Again, more $$

3) There is no native flash-support for ppc, although open-source alternatives are available and being worked on.  They may not work well enough for your target audience.

4) Most of the G3 iMacs had very small hard drives by today's standards, and may be nearing their end of life as well.  Note that if you are dealing with upgraded hard drives, you have a 128 gb partitioning limitation. (make it 125gb to be safe).  You can make use of the rest of the drive, but know up front that you'll probably be doing some custom partitioning.

5) Ubuntu PPC is currently community-supported with recent releases, but there is no guarantee that you won't wake up tomorrow and find it gone.  Unlikely, but perhaps Debian might be a better idea.  Debian won't magically install either due to the PPC hardware not feeding back the right information to Linux hardware probing, so you will still have to follow all of the above.

Just wanted you to know up front what you are facing.

---


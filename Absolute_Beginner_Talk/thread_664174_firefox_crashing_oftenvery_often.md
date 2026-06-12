---
title: "firefox crashing oftenvery often"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by xboxbman on 2008-01-10
Just formatted my laptop 2 days ago and did a clean install of Gusty Gibbon.  I must say I am very impressed overall. But my firefox keeps crashing.  It's whichever is included on the live disc.  It really doesn't matter what site I'm on it seems.  It crashes on the forums here.  It seems I can only hit 5-6 pages before the browser crashes.  I've tried  a few fixes like adding a line to the end of the firefox, but nothing works.  Any one have any ideas?  The only addons I have are foxytunes and forecast fox.

---

### Post by Casual Fan on 2008-01-10
I guess a few different thoughts come to mind:

One, trying to diagnose freezes and crashes is really hard.

Two, are Firefox and Gutsy updated? Have you done a "check" in the update manager?

Three, you may want to try Swiftfox. It will give you Firefox functionality but is just different enough that you may be able to duck the crashes.

Four, try uninstalling Firefox in synaptic (completely remove) and then re-download and reinstall through Synaptic.

Five, Opera is a great browser...! :) (It really is.)

---

### Post by xboxbman on 2008-01-10
> **Casual Fan said:**
> I guess a few different thoughts come to mind:

One, trying to diagnose freezes and crashes is really hard.

Two, are Firefox and Gutsy updated? Have you done a "check" in the update manager?

Three, you may want to try Swiftfox. It will give you Firefox functionality but is just different enough that you may be able to duck the crashes.

Four, try uninstalling Firefox in synaptic (completely remove) and then re-download and reinstall through Synaptic.

Five, Opera is a great browser...! :) (It really is.)

so, number 4 seemed to have done it.  That was suspiciously easy....

---

### Post by barbedsaber on 2008-01-10
I had the same problem, but it only occoured when I visited the ubuntu forums home and if I had been somewhere else previously in that browsing session, I will get opera before I reinstall firefox, so if I cant reinstall it, I can still come back here, and get help.

---

### Post by bouss on 2008-01-11
What I love is that firefox is described as lightweight...
Anyway, I have the same problem. Firefox freezes and does nothing for some seconds, then it starts working, then it freezes again and so on. This is new. Happens even when it does not have to download anything, has allready browsed the site i wanted (home page- no way to go further), Firefox is the only thing running on the PC, no tabs are open.... no reason at all... it just freezes for no reason. This started probably in 2.0.11 and happens only to my ubuntu part (works perfectly on windows). 
I tried to uninstall and reinstall all over (yesterday). Worked...for 1 day. When I tried to browse something today... nothing changed. It was freezing as it used to. I will try to get myself 2.0.10 which seemed to be better.

---

### Post by Patto77 on 2008-01-11
I'm also having some issues with Firefox freezing.  It sounds the same as Bouss, where Firefox fades to grey  and becomes unusable.  It only happens occasionally, but it is regular enough to be annoying.  Anybody got ideas what could be causing this?

---

### Post by philinux on 2008-01-11
The current version in synaptic is.

Gecko/20071204 Ubuntu/7.10 (gutsy) Firefox/2.0.0.11

---

### Post by xboxbman on 2008-01-11
@Bouss and Patto77

that is exactly the problem i was having.  Thus far, the reinstall has worked.  No crashes, no greying.  I hope it lasts.

---

### Post by dark_harmonics on 2008-01-11
The reinstall is definitely something you should try.

Also, is this happening on webpages that require external components (such as java/flash/ect)? If so you might be having problems with those. Trying a different browser on the same website might help determine if these plugins are at fault. I use epiphany as my secondary browser (installable from the repos with sudo apt-get install epiphany). Also, if you launch firefox from a command line you can see if there are any errors on startup.

I've also read that deleting the .mozilla folder and cleaning your temp files can resolve some issues, but i haven't experienced any issues that required me to do this. I recommend backing up anything before you delete just in case. 

Partially unrelated topic: Try this link to make firefox faster:

[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

---

### Post by Patto77 on 2008-01-11
I'm a bit tired so I forget if un-installing then re-installing will lose all my preferences, add-ons, tweaks etc?  I've just about set it up the way I like.  It's no big deal, but I'm not sure if re-installing an app behaves the same as on a Windows install.

---

### Post by xboxbman on 2008-01-11
> **Patto77 said:**
> I'm a bit tired so I forget if un-installing then re-installing will lose all my preferences, add-ons, tweaks etc?  I've just about set it up the way I like.  It's no big deal, but I'm not sure if re-installing an app behaves the same as on a Windows install.

I did a "complete removal" through synaptic and when i re-installed, all my themes and add-ons, even my bookmarks were still there.

---

### Post by Patto77 on 2008-01-11
So far so good after the reinstall.  Thanks for the help everyone.

---

### Post by bouss on 2008-01-12
Installed Opera. Opera works perfectly. Browsing this page with firefox at the moment which seems to have become jealous and works like a clock....weird stuff.

About which sites were open when it freezed. No site at all...just home page google which is 3 lines of text and a picture!

---

### Post by cogitordi on 2008-01-12
SImilar problem: about two weeks ago, Firefox starting going grey and locking up my AMD64 box running the Gibbon/64. So much for my faith in Linux's stability. /o:

I usually keep the browser cache very small but I deleted it and everything else in the profile anyway. That gave me stability for about a week. Then I had another crash today while trying to open a page on a crappy commercial Web site (COUGHrogers.comCOUGH). I suspect at this time that the problem is related to multimedia... which may mean the Flash plug-in. 

This is why I prefer running Firefox for Windows under WINE. (^:

---

### Post by cogitordi on 2008-01-13
I also caught trackerd consuming most of my CPU time after I attached a USB disk. I've removed Tracker and trackerd from my Gibbon installation.

---

### Post by blueridgedog on 2008-01-13
There is an open bug regarding the google tool bar and opening three windows of firefox.  I had to disable the tool bar while waiting for a fix.

---

### Post by bouss on 2008-03-13
There is something really wrong with the relationship between flash, firefox and ubuntu. The grey screens, the crashes (i have crashes too) and slacking are all in some way connected with flash videos or players. Any ideas what to do because the problem persists or just wait for 8.04 and firefox 3?

---

### Post by RussellW on 2008-03-16
I have the same issue with Firefox and Opera. Grey screens and then they die. I actually d/l'd IceApe and have had zero issues with it. Resembles Navigator, but works really well.

---


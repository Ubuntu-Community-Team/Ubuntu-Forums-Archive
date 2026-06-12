---
title: "Grey Screen in Firefox and locks up"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by old_dog on 2007-10-21
Recently installed gutsy, sometimes when waiting for a response from another website the screen goes grey and all you can do is minimise it. When a response is received then everything is ok. If you want to escape from the grey screen you can't or can you?
I would prefer to firefox performing in the standard way.......What do I have to change?
Cheers Old_dog

---

### Post by corney91 on 2007-10-21
If a window goes grey, it means it's not responding. You can either force quit or wait for it to start working again. Generally it is possible to wait but sometimes it needs to be killed.

---

### Post by old_dog on 2007-10-22
Cheers Corney 91.....I get the principal but since I upgraded to gutsy on Saturday the number of websites failing to respond seems to have gone sky high is there another factor lurking in the upgrade that I need to switch on/off or tune something???
any bright ideas....Cheers old_dog

---

### Post by dynamethod on 2007-10-22
heh funny, i just opend firefox to see this thread posted and whadya know! FF went grey and crashed XD

yeah im experiencing the "grey" screen on a regular basis too unforturnatly

---

### Post by realvz on 2007-10-22
try disabling addons in FF if you have any

---

### Post by old_dog on 2007-10-22
All add-ons disabled.....No Change
It really miffs me that the only way out is to force exit from FF
no soft exit???? or is there????
Cheers old_dog

---

### Post by raucous1 on 2007-10-22
Ya,  I am having a similar problem. When first booting up, everything seems to run fine, but if I close the lid of the computer, or allow it to idle, I run into major issues.

The mouse becomes jumpy (unresponsive, then responsive) and right now Im watching firefox just alternate between "normal" and grayed/greyed out every 10 seconds or so (Im having to write this from my windows comp!)

I did not have this problem with Feisty. I tried disabling indexing, installed 915 resolution, checked system monitor for any bloated processes, and have cried about it, but nothing works except restarting. Well its back to windows I suppose. Im running a Compaq/HP nc6220 laptop with intel 915 GMA if that helps the discussion.

---

### Post by TidusBlade on 2007-10-22
I don't know if this will help but usually it happens to me when suing things that require plugins, like Flash and especially Java.
IF things are abit crazy, try out Firefox Gran Paradiso, it might be unstable, but It works much better than 2.0.0.6 on my family computer ;)
EDIT: Or if you want a stable version of Firefox tryout the older versions, I use version 1.5 or 1.6 I think on Damn Small Linux and it's extremely stable, not a single error in a month ;) Of course, not everything will be available to you though...

---

### Post by corney91 on 2007-10-22
Is Firefox really that unstable? Gran Paradiso is worse for me, but I'd recommend Opera (9.50 is very stable even in alpha).
I can't imagine why firefox keeps crashing, Have you tried reinstalling it?

---

### Post by jonboy99 on 2007-10-22
Am also having this problem - firefox unusable, so back to XP on this computer for now.  HAve been running dapper for months and can't remember the last time firefox crashed in it. Not an overheating problem either - in windows prime95 has been running all night.

Help!  :confused:

---

### Post by dynamethod on 2007-10-22
well ive reported the bug here: 

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/155421](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/155421)

if you have this problem, look in the directory /var/crash/ you should see some icons with exclamation marks, double click on them and choose to report them,  they will help the developers, theres been quite a few bugs reported about firefox so far, my one had "medium" concern tagged to it

EDIT - omfg! looks like theres HEAPS of bugs with FF at the moment! very critical and ugly ones too, might be a good idea to switch another browser for now :S

[https://bugs.launchpad.net/ubuntu/+source/firefox](https://bugs.launchpad.net/ubuntu/+source/firefox)

---

### Post by TidusBlade on 2007-10-22
> **jonboy99 said:**
> Am also having this problem - firefox unusable, so back to XP on this computer for now.  HAve been running dapper for months and can't remember the last time firefox crashed in it. Not an overheating problem either - in windows prime95 has been running all night.

Help!  :confused:

You can always use another Browser, Opera is an excellent alternative ;) Konqueror is pretty solid, and as I've said, old versions of Firefox are much more stable from my experience.
[QUOTE=dynamethod]omfg! looks like theres HEAPS of bugs with FF at the moment! very critical and ugly ones too, might be a good idea to switch another browser for now :S[/QUOTE]
Woah, over 200 crashes xD I wouldn't say it's the most stable but I thought It was better than this, when I get the gray screen, then lock up I just kill process and then restore tabs so it's not a problem though...

---

### Post by jonboy99 on 2007-10-22
Well, just disabled ipv6 in the about:config section,and seems to have been ok since then *touches wood*  Ilike opera, but find the firefox extensions too handy.

---

### Post by dynamethod on 2007-10-22
> **jonboy99 said:**
> Well, just disabled ipv6 in the about:config section,and seems to have been ok since then *touches wood*  Ilike opera, but find the firefox extensions too handy.

does nothing to help

---

### Post by old_dog on 2007-10-27
Problem solved for me........I had originally upgraded feisty to gutsy. In my attempts to repair the above problem got in such a mess, ended up with only the command line!
(My ambition far exceeds my talent)
Blew the iffy version away and re-installed from scratch.
Spot on running like a dream
Cheers old_dog

---

### Post by jowaxman on 2007-10-30
I was having this problem for awhile.  I found that I had an old copy of
npwrapper.libflashplayer.so in /usr/lib/firefox/plugins. I deleted this
file and the problem seems to have been solved.

---

### Post by Velociraptor on 2007-11-03
Removing npwrapper.libflashplayer.so from /usr/lib/firefox/plugins worked for me. Thanks for the fix!

(This was driving me mad, firefox would lock up and turn grey everytime I logged into google mail. I think it must be because I upgraded to gutsy, rather than fresh install.)

---

### Post by emid on 2007-11-04
Removing npwrapper.libflashplayer.so worked for me as well in stopping the grey screen and temporary freezes.  Unfortunately now I have no Flash.:(

I'm using 64bit Gutsy which I had updated from 64bit Feisty.


EDIT:

I installed the flash-nonfree plugin and now all is well.

---

### Post by teknorah on 2007-11-05
removed npwrapper.libflashplayer.so from ~/.mozilla/plugins and it stopped the freezing issue as well

To get flash to work in firefox, install gnash w/ synaptec/apt-get.  It is an opensource version of flash that works well with firefox!

---


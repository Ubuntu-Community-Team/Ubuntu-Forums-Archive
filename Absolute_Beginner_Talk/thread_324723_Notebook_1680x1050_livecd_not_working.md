---
title: "Notebook 1680x1050 livecd not working"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by fsando on 2006-12-24
Hi I am a complete newbie to ubuntu
After almost three weeks I finally decided to post my question in its own thread
I have now tried to install ubuntu on my two notebooks sveral times during the last weeks without success.
My primary notebook is a brand new asus W1J core2duo 2.16 with ati x1600 1680x1050.
My experience is that when I let the livecd run default installation it actually installs into some graphic desktop - just the screen is unreadable, it is skewed completely - though some graphic interface is vaguely recognizable.
I have tried quite a few work-arounds (changing text options, graphics safemode etc.) that I have found on the net - any change from the default results in the install process halts somewhere midway, it simply stops responding.
I have been searching here and on google - a few others had the same problem. Unfortunately no one with knowledge of ubuntu has experienced this yet so no useful advice was found.

What am I to do?

I would suspect that there is an option to be typed in at the options menu of the livecd.

Alternatively, it may be possible to start some text console after the installation - even when the screen is unreadable (I think it would be readable in text mode) and then edit some configuration file.

Or even better: create a new livecd that works with my notebook - it could then be posted for others to use.

When I bought this notebook I imagined myself installing linux then running this one unreplacable windows program in a virtual machine - I hoped for a blazing performance.
Now I'm a little dissapointed

---

### Post by Sef on 2006-12-24
> My experience is that when I let the livecd run default installation it actually installs into some graphic desktop - just the screen is unreadable, it is skewed completely - though some graphic interface is vaguely recognizable.

Try the alternate cd.  It can work when the Live CD fails.  You have to input a few things, but most of it is basic: nothing really hard to figure out.   To see what an alternate install looks like, read the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/").  Just skip the part about partitioning, if you are not dual booting.   The rest will apply.

---

### Post by fsando on 2006-12-24
> **Sef said:**
> Try the alternate cd.  It can work when the Live CD fails.  You have to input a few things, but most of it is basic: nothing really hard to figure out.   To see what an alternate install looks like, read the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/").  Just skip the part about partitioning, if you are not dual booting.   The rest will apply.

Thanks for your quick reply, but 
"This website is not about the 'Desktop' Live/Install CD's installer"

I just downloaded the alternate and booted with it but it appears to be for installing only as far as I can see from documentation and the boot screens. And I don't want to install anything before I've seen it working. 

My notebook comes with a 'restore version' of XP (the MS-tax) it was a long and stupid installation process followed by hours of tweaking and uninstalling 'helpful' extras.
So I am not going to remove XP, (or commit any other profound changes like repartitioning, dual boot etc.) before I am sure ubuntu wil work for me.

Perhaps some other solution?

---

### Post by fsando on 2006-12-25
Update:
I'm now writing this post from the ubuntu 6.10 livecd!
I have tried more than 15-20 times in recent days to run ubuntu, so how i succeeded in booting have me wondering a bit:
this time I started in graphics safe mode, Under further options (F6) I deleted the 'quiet' part to see what was going on during boot.

I turns out it stops at 'configuring network' (don't remember precise wording)
Here I usually end up pressing  the on/off button for 30 sek. This time though, (out of old windows habit) I did the Ctrl+Alt+Del and lo and behold! The boot process continued and finished nicely :D 

Now my screen is 1024x768 (I want 1680x1050) but this will hopefully be solvable once it is installed for real

Other thing: where is my windows file system? (well I'll search for that information now).

---


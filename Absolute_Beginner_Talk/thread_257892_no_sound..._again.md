---
title: "no sound... again"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by vulture on 2006-09-15
well today i updated my system, a nice friendly message popped out in my upper-right corner saying new updates available, i installed them and when rebooted... no sound!

I get this error:
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

I spent 3 hours configuring soundcard last time (i have Asus A6R notebook so you know what i mean) and when it finally worked (well at least i had sound) i updated ubuntu and it's gone again! WTF?!

How to get it back?

P.S. as i remember kernel was updated too...

---

### Post by xpod on 2006-09-15
Dont know about the initial complications you had but the first place i check
is the "multimedia system selector" to make sure the settings aint changed again as they regulary seemed to do at one point.

Your updates would`nt have removed anything you need would they?
I just stumble across my fixes mate so can only tell you the checks i made and still "make" if and when the sound goes.

I ended up getting the oss package as the alsa just would`nt work.But now i have the "multimedia selector" set to "autodetect" it ALL seems to work.

Sorry i cany be of any real help but most of it`s still gobbildygook to me.

Theres loads of threads in the "search" utility regarding lost sound.....
A very common problem by all accounts.....Good luck

---

### Post by mario_7 on 2006-09-16
If you compiled Alsa last time, you have to recompile it now and run alsaconf.

---


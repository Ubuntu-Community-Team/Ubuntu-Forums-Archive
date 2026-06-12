---
title: "Sound on Thinkpad 770Z"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by fake_punk on 2006-03-30
Hey all, I am trying to get my sound card to work on my IBM Thinkpad 770z.  It is pretty much the exact same thing as this thread:
[http://www.ubuntuforums.org/showthread.php?t=148281&highlight=cs4236](http://www.ubuntuforums.org/showthread.php?t=148281&highlight=cs4236)
I have tried all the things in that thread, and, I did get a little success, but it still does not work.  Before doing anything in that thread, the speaker at the top right had a little x beside it and said it needed to be configured.  Well, after following what that says, the x is gone, but it is still acting weird.  I plugged headphones into the jack and listened while the sound was turned up on the physical laptop, I realised that the speakers on the front were acting as microphones :confused: .  I hope someone has a solution for this problem, as i want to listen to music on my laptop.  BTW, everything works fine under windows on this exact laptop, so its not a hardware problem.

---

### Post by jr3549 on 2008-03-27
I have a TP770Z also, with a DVD-ROM. I installed Ubuntu 7.10 i386 on it after I did the live cd tour, everything went fine, except when it went into the HW detection process. Then it crashed right out, I don't know if it was the CW audio chip or the DSP chip that caused it.
I do know the Crystal Fusion AC-97 chip is problem for many OpSys, as well as the DSP chip, but my audio worked fine during the live cd. BTW: the DSP chip has nothing to do with the main audio functions of your TP, it is used for the built-in modem to support  ViOP and streaming audio over the internet, that's why it installs mwave driver.
If you can't find a solution to this problem, I suggest that you head over to sourceforge.org and pick up a copy of UltiraAud for linux, this audio app can find and configure most any sound device on the planet, nearly, and has excellent support for AC-97 chips. I use this on my OS/2 install on my P200 and P3 systems, works great.
Also make sure that you have the latest TP utility, BIOS, CW, updates on your system before you try to install Linux. I also remenber that the newer Linux requires more resources than previous versions, live cd requires 384MB of ram. Check out the system requirements for the version of Ubuntu to make sure. My 770Z just meets the requirements for Live-cd and install. I'm going to install DSL on my TP, I'll pass it along.
 I hope this helps

---

### Post by LieToPurify3 on 2008-04-09
I must have posted about 3 or 4 times with this same problem. I have the 770z dual booting with Xubuntu and trying to get DeLi linux to work with it.  I had it dualing with Xubuntu and DSL, and the sound didnt work on either.  I've tried every thread i've been able to find on every linux forum i came across but to no avail.  Please PM me if you find anything out!

---

### Post by LieToPurify3 on 2008-04-09
I just looked for that UltraAud softwar and couldnt find it. Let me know

---


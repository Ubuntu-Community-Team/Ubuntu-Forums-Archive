---
title: "x1900, Compiz Fusion...Possible?"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by Bonz on 2007-07-16
I am new to Linux alltogether.  I installed it 3 days ago and am learning rapidly on installing things and how to run things.  I would really like to get the eyecandy going but I have an x1900gt.  I have seen a few users in these and other forums claiming to have Compiz Fusion running on an x1900gt.  At first I installed the newest fglrx drivers from ATI and made sure direct rendering worked and everything.  I ran through the steps to install xgl, create the session, install compiz fusion and everything.  I made sure everything was all correct (2nd or 3rd time around).  I restarted, went into the xgl session.  My screen was all mangled and distorted with horizontal lines running through it.  I logged out and went back into GNOME session.  My direct rendering was now turned off, and when I type fglrxinfo I get this:
bonz@Bonz-Ubuntu:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
, when it was showing everything perfect right before I logged out.  If anyone has any idea if this is even feasible can you please let me know.  I know I have seen people saying they have it running, and how I don't know.  I am a Linux n00b.  Can someone please tell me if it's able to be done, and how.  Thanks, this community is great.

-Bonz

---

### Post by Chris S. on 2007-07-16
I'm sorry, I don't have an answer, so I wouldn't be much help.  However, I thought direct rendering doesn't work during an XGL session.  I haven't tried installing Compiz Fusion yet, but I don't get why you'd get direct rendering working if you're not going to need it.  I'm only curious because that was part of the reason I had trouble getting Beryl to work.  I avoid XGL now because of that.

If you can clarify this (Linux n00b doesn't imply "everything n00b"), or point out where you found installation instructions, that would help me solve some of my problems.

Good luck with Compiz Fusion.

---

### Post by mcduck on 2007-07-16
You actually have to get DRI working for the XGLK to work. After that, XGL uses DRI so it's not available for any other application.

Anyway, I haven't tried with the laest Ati drivers, but using the drivers from Ubuntu's repositories (and similiar method to install them as is explained in the sticky thread on top of this forum section) I have Compiz Fusion running perfectly on my Mobility Radeon X1600. So it should run just fine with you graphics card too..

---

### Post by Bonz on 2007-07-16
mcduck, did you do anything special other than...install the drivers?  Any special configuration.  I have tried using the 8.35.5 drivers and now the 8.38.6 drivers and neither have worked.  I have DRI working at first, then when I log into the Xgl session everything just messes up.  I log back onto GNOME and It's reverted back.

---

### Post by twiceasworn on 2007-07-16
I am in the same boat as you except I have a X1300.  I got the fglrx drivers all setup and then I logged out, came back and it was back to mesa.  Slightly frustrating to say the least.

---

### Post by mcduck on 2007-07-17
> **Bonz said:**
> mcduck, did you do anything special other than...install the drivers?  Any special configuration.  I have tried using the 8.35.5 drivers and now the 8.38.6 drivers and neither have worked.  I have DRI working at first, then when I log into the Xgl session everything just messes up.  I log back onto GNOME and It's reverted back.

With Feisty I just installed the driver, ran command 'sudo aticonfig --initial' and that was it. Some people say you also need to add some line about video output and disable compositing in your xorg.cong, but it seems I didn't even need to do that. If you haven't done those and you have problems check the sticky thread.

XGL is of course a bit more complicated, as you need to create a new session that loads XGL when you log in. But I assume you already have some instructions for that (it seems I can't find the guide I used any more).

But, like I said, when you are running XGL DIR is no more available for any other app, as XGL is using it. That should not be a problem, I get pretty good performance even with OpenGL apps while running XGL/Compiz.

---

### Post by orangebase on 2007-08-09
I was stuck having a distorted screen when logging in the XGL session, but that's all solved. Combination of tutorials plus an extra step. I've tried virtually every method to fix this before but none of them worked.

```
sudo dpkg-reconfigure xserver-xorg
```
Make sure that fglrx is selected and that the monitor sync ranges aren't written to the config file (not sure if that's important, but that's what I did). Everything else left as default or configured as you please should work.

---


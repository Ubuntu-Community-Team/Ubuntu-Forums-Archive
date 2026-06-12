---
title: "window decorations missing with beryl ?"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-02-10
Hello.
ive just installed beryl (been messing around with things so have had to re-install) and now i dont get window decorations, and if i open terminal i just get a blank white square, which i cant do anything with.
if i un-install beryl i get window decorations ?
the only thing thats is different on my system is that i have the latest nvidia drivers (9746) would this cause the problem ? 
cheers.

---

### Post by sunexplodes on 2007-02-10
In terminal, run the following command:

sudo gedit /etc/X11/xorg.conf

Then scroll down to the "Screen" section, and insert the following line:

    Option         "AddARGBGLXVisuals"

Save, close, and restart your X session. Should do the trick.

---

### Post by techno-mole on 2007-02-10
many thanks, it worked a treat.
beryl ran well with the drivers i installed using automtix, but it runs even better with the latest nvidia driver, well i think it does, and its well worth the effort of trying to install the latest drivers and so on, it pays off in the end.
cheers again.

---

### Post by twosox on 2007-02-12
Thank you, thank you, thank you.

This did the trick for me as well.  After upgrading the kernel and having to re-install the Nvidia driver, I was lost without my wiggly windows and desktop cube.

---

### Post by himeraz on 2007-02-24
This should be in a sticky or guide someplace. Worked for me as well, was having the same problem with missing window decorations. Thanks sunexplodes.

---

### Post by benzstar on 2007-02-25
I'm having the same issue, but in my case it's all the worse because I know I can run Beryl.  My sad tale is this: I had Beryl running great, 3d acceleration (Nvidia 5700) running great, I had ripple effects, rotating cube (inside view) and the only thing that didn't work was skydomes. Life was good.  Then I saw envy on digg and figured, "Hey, if it's this good now, imagine with the very latest Nvidia drivers!" Ooops. Cannot connect us.nvidia.download.....

After some quality time with the command line and learning about the importance of regularly backing up xorg.conf, I had the X server running again. No 3d acceleration, even for Alien Arena... So I updated the kernel and reinstalled the nvdia drivers.  Now 3d acceleration is back, as is my cube. My title bars, however, are MIA. I've tried all the posted fixes I could find, tried removing and reinstalling Beryl completely, same issue. No title bar.   My xorg.conf matches what all the beryl installer guides say. I'm using the "Svn" version of Beryl if that helps. I've tried forcing GLX/AGILX and I've tried turning off all the bells and whistles.  I just want the lovely desktop I had last week back! If I don't figure it out by Thurday I'm reinstalling Edgy from scratch - I really hope to NOT do that as I'm trying to prove to my freinds and neighbors how much more stable/reliable Linux is.... A reinstall after 2 weeks wouldn't look good :)  

Any ideas? This is my first forum post, so sorry for any newbness.

---

### Post by swedishlf on 2007-03-07
I hate to dig up an old thread, but I'm having this same problem.  The fix posted here managed to make my terminal usable when beryl is enabled, but still no title bars or borders on any windows.  Cube works great, minimize/maximize functions are awesome.  Water effects are a little dodgy, sometimes they work sometimes they don't.  I have nearly full functionality without the borders, but they'd still be nice to have!

Using Edgy AMD64 and GeForce 6600.

Edit: Disregard, problem solved.  Finally thought to right click the beryl icon, and reload the window decorator.

---


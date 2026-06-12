---
title: "Widescreen Resolution causes &quot;stretching&quot;"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by davo_ on 2007-04-22
Screen resolution problem: whenever I add 1280x768 to my screen mode section in xorg.conf, and restart X I get a horrible picture full of scanlines and multiple renderings of the same windows, what's going on?

PC Specs: 

Gateway MX3228
S3 Unichrome Pro IGP video, recently downloaded and successfully installed openchrome software

I think it may be my HorizSync and VertRefr information, but I have no idea how to find out what they are, and the Gateway site so far, is being uninformative.

Help?

---

### Post by lluisanunez on 2007-04-22
May be this can help:
[https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")

---

### Post by ggaaron on 2007-04-22
I'm really not sure, but shouldn't the resolution be 1280x800?

If you want to configure xorg, with sync ranges and so, run sudo dpkg-reconfigure xserver-xorg.

Hope it helps.

Aaron.

---

### Post by davo_ on 2007-04-22
I do believe it has something to do with my sync ranges, but I have no idea how to figure out what the correct ranges are.  According to what I've read, X-server is really bad about detecting the wrong ranges.

---

### Post by ggaaron on 2007-04-22
Use middle option when dpkg-reconfigure asks about monitor sync - you will only need to choose something like 1024x768@70Hz - choose that, which is the closest to your desired. It works for me, I have toshiba laptop with 1280x800 screen.

Aaron

---

### Post by davo_ on 2007-04-22
I'm still getting screen lines.

It's odd, the login screen renders perfectly in a great resolution,if I go into failsafe terminal session (which is what I'm in right now), the resolution is perfect, screen is perfect.  But after I login, I get horrible renderings.

---

### Post by ggaaron on 2007-04-22
There is only one more thing that comes to my mind - look in bios for something that changes behaviour of the screen, hmm - usually laptops have something that stretches screen, when too small resolution is used, and there is possibility of turning it off to have a smaller screen in the centre and black borders. I remember, that on one laptop even after choosing wide-screen resolution it would use bad settings. Disabling auto stretch in bios might help. I'm really running out of ideas=/

Aaron.

---

### Post by davo_ on 2007-04-22
Alright um...I seem to have really fubar'd something, I cant see either of my panels anymore.  I get an error that says 'I see two panels already open, I will close now" and I can't see either application or task pane.

Also, running in failsafe terminal, the terminal window is now in the very bottom corner, almost completely out of view.  What command could I use to roll back all changes to xserver-xorg?

---

### Post by davo_ on 2007-04-22
I've managed to rollback to previous X configurations, screen resolution of 1024x728, display mode 24, however if I add in anything larger, the screen stretches, scanlines appear, and I get the problem described above...

Note, the login screen looks perfectly fine, it's after I login, and gnome starts up that I have problems.

---


---
title: "problem loading google earth"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by diracnafobia on 2007-11-03
I just installed google earth on ubuntu and when i try to run it the google earth logo comes up on the screen and it just stops there. I've looked in the terminal I'm running it from and I see that it says 'Xlib:    extension "XFree86-DRI" missing on display ":0.0".' I have no idea what this means or what to do about it. From other forums it sounds like it has something to do with my NVidia driver.

---

### Post by Maestro23 on 2007-11-03
> **diracnafobia said:**
> I just installed google earth on ubuntu and when i try to run it the google earth logo comes up on the screen and it just stops there. I've looked in the terminal I'm running it from and I see that it says 'Xlib:    extension "XFree86-DRI" missing on display ":0.0".' I have no idea what this means or what to do about it. From other forums it sounds like it has something to do with my NVidia driver.

Looks like you don't have Direct Rendering enabled.  Open a terminal:

> glxinfo | grep direct

If is says NO, then you don't.  Do you have the Restricted Drivers enabled?  I'm an ATI guy, so I will let the Nvidia gurus chime in on this one. :smile:

---

### Post by diracnafobia on 2007-11-03
Thanks, it says that I don't have it enabled, but I don't know what direct rendering is or how to enable it. This is all very new to me.

---

### Post by Maestro23 on 2007-11-03
> **diracnafobia said:**
> Thanks, it says that I don't have it enabled, but I don't know what direct rendering is or how to enable it. This is all very new to me.

What model is your card? Did you download any drivers for it? Are the Restricted Drivers enabled?  System>>Admin>>Restricted Drivers Manager

Also, this board is full of threads dealing with Nvidia cards.  Don't just wait around for someone to see your post, run some keyword searches and see if you can find your answer.  And when asking for help, its always good to post:

1. What are you running? Ubuntu Feisty/Gutsy? 32-bit/64-bit

2. Brand/Model of Video card.

3. What you have tried so far to fix the problem.

*Just some friendly advise. :smile:

---

### Post by diracnafobia on 2007-11-03
Ok, thanks again.

Here's what I have for you.
Ubuntu Feisty, 32bit
ATI Radeon Xpress 200M 5955 (I think)
Under restricted drivers it says ATI accelerated graphics driver, Status: Not in use and under enabled there is a check box that is unchecked.

---

### Post by diracnafobia on 2007-11-03
Oh, and no, I didn't download any drivers for it.

---

### Post by diracnafobia on 2007-11-03
I enabled the restricted driver and now everything's running smoothly. Thanks for all your help.

---


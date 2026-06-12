---
title: "Display on Toshiba Satellite Pro 4200 Series Laptop"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by pkc2 on 2006-09-03
Hi, Complete newbie. Installed Ubuntu 6.06 last week on my desktop and everything seems to work fine. Thought I'd give it a go on my old laptop which I just retired. I loaded it and everything seems to work ok, the problem is with the display. The desktop (or any other screen is only showing in the centre of the lcd screen. It's all proportionate but there is a good 1 inch black border around the edge of the desktop. I am unable to find the controls to change the size of the display. Tried preferences > screen resolution and Administration > device manager but can't find a solution. I feel as though there should be a device driver for this laptop. Searched the forums and docs but can't find an answer. Can anyone help please? Thanks Peter

---

### Post by az on 2006-09-03
I think this is an old laptop with a small amount of video ram, right?

I think the problem is that Ubuntu is using the maximum color depth and that prevents you from using the whole screen.

Boot into recovery mode and run

dpkg-reconfigure xserver-xorg

and answer the questions normally (take the default)

When asked about color depth, pick 16-bit instead of a higher resolution.  That should leave enough video memory free so that you can use the full screen resolution.

when you are brought back to the command line, run

init 2

to get into the desktop.

---

### Post by pkc2 on 2006-09-04
Thanks for the advice. Tried it and I can get a full screen display for the log in screen but the next screen that tries to come up is corrupted and then Ubuntu throws me back to the log in screen again. I've run the dpkg-reconfigure loads of times varying my responses with no luck. I've managed to find a manual for the Laptop and it only provides 8Mb ram for the video display. I think this may be a lost cause. Thanks for the help.
Peter

---

### Post by az on 2006-09-04
> **pkc2 said:**
> Thanks for the advice. Tried it and I can get a full screen display for the log in screen but the next screen that tries to come up is corrupted and then Ubuntu throws me back to the log in screen again. I've run the dpkg-reconfigure loads of times varying my responses with no luck. I've managed to find a manual for the Laptop and it only provides 8Mb ram for the video display. I think this may be a lost cause. Thanks for the help.
Peter

8 Megs if more than enough.  Anyway, now your problem is that gnome has the wrong setting for your display and not that you cannot configure the hardware.  You just did that.

Delete all the .gnome and .gconf directories in your home drive and try to log in again.  I think that should fix it.

(.gnome .gnome2 and .gconf)

---

### Post by pkc2 on 2006-09-05
Awesome!!! Not quite sure what I did but thanks very much for the assistance. Safe to say I couldn't have done it without you. I was going to get rid of this computer because it was hopeless running Win Millennium. Now my daughter can have it for her school work (and music and chat etc :-). Thanks again.
Peter.

---

### Post by McTrkdrvr on 2008-03-13
Thanks alot the tip worked perfectly on my Toshiba 4080xcdt:popcorn:

---

### Post by theophiles on 2008-05-30
> **McTrkdrvr said:**
> Thanks alot the tip worked perfectly on my Toshiba 4080xcdt:popcorn:

I have that same computer. This worked before, but I decided since I had such an old computer I should run xubuntu. I get the same small screen. Any ideas?

---

### Post by Jackie999 on 2008-05-30
I'm not sure if this post [http://ubuntuforums.org/showthread.php?t=763964](http://ubuntuforums.org/showthread.php?t=763964)  will help you, but it's the way I get my Toshiba Satellite 1800 (with trident driver) back to full size.

---


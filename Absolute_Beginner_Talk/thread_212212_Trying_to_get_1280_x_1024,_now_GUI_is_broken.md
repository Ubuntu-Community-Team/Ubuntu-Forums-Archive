---
title: "Trying to get 1280 x 1024, now GUI is broken"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by Tom Brokaw on 2006-07-09
Relevant specs:
Geforce 5900 Ultra flashed to 5950
Cornea MP704 LCD (VGA)
AMD Sempron 2400+
MSI KM4M-L mainboard
KVM Switch

Installed fine, but I only had three options for resolutions: 640x480, 800x600, and 1024x768.  My LCD's native res is 1280x1024; that's what I prefer and of course it looks best.

As a side note, the entire display is shifted to the right - there are black, unused pixels on the left side, and the right side of the screen is hiding some of the "active" pixels.  This only happens once the GUI is booted up, so I doubt it's the KVM, but I haven't definitively eliminated that yet.

Tried getting the latest Linux drivers from Nvidia, but I apparently couldn't make them work.  Downloaded to the desktop and ran the specified (by nvidia) command and got a No Path or File error.

Discovered EasyUbuntu, ran that, and it fixed some other stuff (installed Flash, etc) but I still couldn't adjust my res.

Tried a re-autodetect of the hardware, which didn't appear to change anything.  I just hit OK for all the options, as I figured that was less likely to break anything.

Looked around on this forum, found this thread:
[http://www.ubuntuforums.org/showthread.php?t=210218](http://www.ubuntuforums.org/showthread.php?t=210218)
and posted a rant last night(sorry, was very frustrated).

I tried the solution suggested by RaffyTaffy; all the appropriate spots in my xorg.conf file had my desired res in them.  So I saved it and hit Ctrl Alt Backspace.  Now it gives me an error and can't start X.  Can't remember the error, don't know how to copy/paste in that environment (is that the shell?).

Can't understand what went wrong - all I did was save a file with no changes and restart X, and now it's broken.  As stated in my rant, I'm not sure why changing resolution is so hard - what am I missing?

Currently wavering between doing a reinstall to start from scratch, or just trying to fix the problem from where I am; would appreciate any and all help.

To restate problems/questions:
Goal is to get 1280x1024 resolution.
Also want to eliminate "offset" of display.
GUI currently busted.

Thanks.

---

### Post by %hMa@?b&lt;C on 2006-07-09
if you are at the console, you can try
sudo dpkg-reconfigure xserver-xorg

---

### Post by Tom Brokaw on 2006-07-09
Excellent, that worked fantastic, and it also allowed me to add my desired resolution, so!  Thanks so much, Jeff.

Upon going through the setup again, I think I had switched the drivers to "nvidia" from "nv" so I was wrong, I did change something, and that's probably what broke it.

I'm still not sure why I couldn't get 12x10 to show up, as it was checked in the appropriate box.

Now, anyone think they can help with the "offset" issue?  I tried adjusting it with my LCD's osd and it fixes it, but then my Windows display is too far to the left.  Right now I've got it halfway.

Should I start a new thread for that?

Thanks again!  If I couldn't get the resolution, er, resolved, I was going to give up on Ubuntu, as there was no point in continuing with learning other stuff if my screen was fuzzy.

---

### Post by tseliot on 2006-07-09
> **Tom Brokaw said:**
> Now, anyone think they can help with the "offset" issue?  I tried adjusting it with my LCD's osd and it fixes it, but then my Windows display is too far to the left.  Right now I've got it halfway.

Should I start a new thread for that?
I don't know if a fix exists.

Try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by confused57 on 2006-07-09
I have the same problem with the screen shift switching between Ubuntu and Windows...Windows to Ubuntu, screen is shifted to the right & Ubuntu to Windows, screen shifted slightly to left.
It's a 19" LCD with auto tuning, which corrects it in Ubuntu, but I have to manually press the auto tuning button in Windows.
I don't think there is a fix for it, though.

---

### Post by Tom Brokaw on 2006-07-09
Well, pressing a button on the monitor is a lot better than my current workaround, so thanks for the tip!  Obviously it won't work every time I switch from one to the other for 5 seconds, but it'll be good for extended sessions on either platform.

---


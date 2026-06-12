---
title: "Running Ubuntu on Parallels: Resolution Problems"
date: 2007-02-21
forum: Apple Intel Users
---

### Post by Paralex on 2007-02-21
Hello all,

Okay, here's the deal. I installed Ubuntu 6.10 on Parallels (build 3036). At times, I need to view Ubuntu at full screen. But, the maximum resolution right now is 1024x768.

I tried a few steps that I thought would help out.

Before I did anything, I went into Parallels configuration and set my custom resolution to 1680x1050. I thought it would be the most logical thing to do.

1.) Go into terminal, run command: *sudo gedit /etc/X11/xorg.conf*

The reason for this command is because I couldn't save the file by just simply editing it (due to that I don't have permissions to the file).

Anyway, I edited the file and added my resolution in depth 24. Then, of course, I had to restart the X Server (via CTRL + ALT + Backspace) -- that worked. Once restarted, I check System > Preferences > Screen Resolution. My resolution was still not on the list.

2.) Go into terminal, run command: *sudo dpkg-reconfigure -phigh xserver-xorg*

Here, I set the driver to Vesa and selected my resolution, 1680x1050. I restarted X Server once again, no avail.

This was done last night. When I went to school today, I went on a PC with Ubuntu on it. I realized that the resolution was totally wrong at 1024x768 (17" CRT = 1280x1024). I tried the *sudo edit /etc/X11/xorg.conf *method, and it worked! 

Mine must not be working because it's being emulated? 

Just to be on the safe side, I reinstalled Ubuntu this afternoon to give it another shot. No luck.

If anyone has any tips for me, I'd kindly appreciate it. :KS

PS: I'm running an iMac 20", Intel Core Duo 2.0GHz, 2GB RAM, 500GB HD, 256MB ATI Radeon X1600.

---

### Post by hobbanero on 2007-03-06
I am having the same issue.......I set a custom screen resolution in Parallels to get a higher resolution, but the custom setting does not appear as an option in the Ubuntu guest OS....1024x768 is the highest option.  The same strategy worked in my WindowsXP guest OS previously.

Parallels officially only supports Ubuntu 5.05, according to their web site, and I am using 6.10....maybe that is a problem.  I have emailed Parallels tech support....hopefully they have an answer.

What would be awesome is if Parallels rolls out the automatic resize capability that they recently launched for Windows guest OSes.

---

### Post by entangled on 2007-03-06
X tries to use other info in xorg.conf to limit screen resolution.
Edit the Screen-Display subsection entries for increased mode, as you were doing.
Also try setting the HorizSync to a higher upper limit, maybe 100. If you are using a TFT the VertRefresh value can be set to upper limit of 61.
You find these values under the Monitor section.
After changing these, re-start the X server using Ctl-Alt-Backdelete.

---

### Post by patrickfromspain on 2007-03-07
the vesa driver won't do higher than 1024x768

---

### Post by entangled on 2007-03-08
My resolution is currently 1280x1024 on parallels and seems OK.

---


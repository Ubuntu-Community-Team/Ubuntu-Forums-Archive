---
title: "top .5 inch of screen black and cursor invisible"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by blufur on 2007-02-25
Hi. Just installed newest version of Ubuntu on my Dell Latitude D505 and the top 0.5 inch of screen is black (with a smattering of red pixels).  Otherwise the image is great, and the menubar even begins right below that top blacl bar and appears intact.  The other problem is that while the mouse is there (menu pops up when I rt-click and if lucky i can guess where it is to click on menu items) there is no cursor visible.  Any suggestions? Thanks.

---

### Post by macogw on 2007-02-25
My mouse sometimes disappears.  I don't know why, but if I move it around a bit it usually reappears after moving over the panel a bit or clicking on something.  For the black bit, press the buttons on the front of your screen.  It's probably set to put the screen that far from the edge.

---

### Post by blufur on 2007-02-25
The computer is a laptop (latitude D505) so no screen adjustment... definitely not a positioning issue, as there are bright red pixels scattered in black area.  Also, the mouse is not sometimes missing - it's always missing.  Anyone else?? Thanks so much for the effort, though!

---

### Post by bluepixel on 2007-02-25
I am having the same issue - I have spent *hours* this weekend trying to get it fixed and am still not sure what the issue is.

Here are the specs of my machine:
cpu: intel pentium m / x86
graphics: intel 855 chipset
native resolution: 1280x768

I have tried the most recent 915resolution and it hasn't fixed the issue. I would greatly appreciate any information on how to resolve!

Thanks!
(oh and I *am* a newbie)

- bluepixel

---

### Post by bluepixel on 2007-02-25
I may have found a partial resolution to this problem. Note however that the solution was intel chipset specific.

Digging a bit deeper into the forums I found this post:
[http://www.ubuntuforums.org/showthread.php?t=261019&highlight=top+screen+black+mouse](http://www.ubuntuforums.org/showthread.php?t=261019&highlight=top+screen+black+mouse)

At the bottom of the thread the author mentions using the package xserver-xorg-video-intel to solve the problem.

Here is what I did:
1. opened a console window and ran: 
    sudo apt-get install xserver-xorg-video-intel

2. After the install completed I went to /./etc/X11

3. I opened up xorg.conf:
    sudo gedit xorg.conf

    NOTE: Make a back-up of this file before you do anything.

4. I found the "Device" Section for my monitor. In my case it looked something like this (hand copied):

Section "Device"
  Identifier "Generic Video Card"
  Driver "i1810"
  BusID "PCI:0:2:0"
EndSection

I changed it to this:

Section "Device"
  Identifier "Generic Video Card"
  #Driver "i810"
  **Driver "intel"**
  BusID "PCI:0:2:0"
EndSection

The only real change here was to comment out the current driver (Driver "i810") and add a line below it for the new driver( Driver "intel") that I installed with package xserver-xorg-video-intel. 

A few notes/warnings:
- I AM a newbie - I may be doing stuff that's not advised (sorry just learning).
- This will ONLY work (I think) with Intel Based Cards.
- I have only tested this on the 855 chipset. I don't know how well it will work on other chipsets.
- I had previously edited my xorg.conf file to support the correct resolution for my card - you may need to do similar to get the right resolution for you.
- I have not tested the machine much after putting the fix into place. I don't know if things like suspend/resume function correctly with the fix.
- Use at your own risk :)

Hope this helps. 

Thanks to jfernyhough for his helpful hints.


- bluepixel.

---

### Post by lybbe on 2007-04-17
Any solution to this?

I'm running Feisty and got the same problem. No cursor and graphic error on top of the screen. The solution above doesn't work for me. X refuse to start with the above solution.

Anyone?

Thank you

---

### Post by yuppio on 2007-05-01
I got the same bug, i solved it by downgrading to A09 firmware for my computer BIOS.

---

### Post by Pluscom on 2007-05-17
> **yuppio said:**
> I got the same bug, i solved it by downgrading to A09 firmware for my computer BIOS.

yuppio.
My Dell D505 had a green bar at the top of the display and no mouse pointer.  I tried several solutions based on "855resolution" but lacked the Ubuntu smarts to make them work after several evenings wasted.  Ten minutes after seeing your solution my A_11 firmware was back to A_09 and Ubuntu was pristine!

Thanks,
Pluscom (Seventy year old Linux rookie)

---

### Post by Tethtibis on 2007-06-27
bios edition a11 does this, dunno' why, try downgrading the bios to a09, it should work fine then. :O)

---


---
title: "Install problems noob here no video after 5 minutes"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by markfw on 2007-12-01
OK, so I am a total noob on ubuntu. I download the iso (x64 version) and put it in 2 different computers that have XP installed, they are overclocked , but stable@100% load for months, so this is not a hardware problem. They both do the same thing. One is an E6300 CPU, ASUS P5K (P35 chipset) @ 3.3 ghz, and an S3 Trio64V2 video card. The other is a Gigabyte P35-DQ6 (P35 chipset) @ 3.610 ghz and the same video card.

I put the CD in and boot from it (7.1) and after a little bit a menu comes up, and says something like below(from memory, just as close as I remember):

Boot or install Ubuntu
 ....(can't remember)
Install Ubuntu with a driver disk
Check the CD for errors
...(other stuff)

So I checked the CD for errors, no problem. So I try the first one, that runs by default if you don't do anything. A Ubuntu logo comes up, and a progress bar.  On one the progress bar (left to right, and repeats)  goes for a while then just stops (Q6600) 10 minutes later, no action, reboot try again, same thing.

Next the E6300, same thing, except the progress bar changes to filling in from left to right the whole bar, then the screen goes black, then after a couple of minutes, the CD stops spinning, and 10 minutes later, no change.

What am I missing here ? 2 different boxes, totally stable on XP, but nothing during install ? Please, all advice is welcome. I tried reading the install guide, but I don't recognise any of the windows, so I don't think I have gotten that far yet.

Thanks, Mark

---

### Post by red_Marvin on 2007-12-01
A google search suggests that the video card is unsupported by X (that controls graphics), what happens when you press ctrl+alt+f1 to ctrl+alt+f12?

---

### Post by markfw on 2007-12-01
I guess my google search was wrong. I did it and got text like this:
"When I start X.org, it tries all the different graphic modes and the log brings up an error for any of them:
e.g.: 800x600: Insufficient memory.
This repeats with all aviable modes and results in the end in: "no valid modes found" and the X-Server won't start. In xorg.conf all looks well, the Graphic card (S3) and Monitor are detected (and named) correctly.
At least some of the modes definitely correct and really should work (e.g. 640x480).
I added "VideoRam 1024" - no effect. I created my own xorg.conf with the config utility - no effect.
It could well be, that e.g. 1024x768 is only possible with 256 colors, is that why X.org doesn't want to use it? Why doesn't work the fallback to a lower mode?"

That doesn't look to me like installing ubuntu, its looks like its already installed.

Anyway, thanks, I guess I have to put in my 2 x1900xt video cards just to run F @ H...Great.
[B]
So, what is the oldest, slowest, cheapeast video card that has the best support for ubuntu ?[/B]

---

### Post by markfw on 2007-12-02
So, what is the oldest, slowest, cheapeast video card that has the best support for ubuntu ?

---

### Post by mdpalow on 2007-12-02
why not try the 2nd option in the menu to install 7.10?

I can't remember the option name, but my video card won't allow for an install using the first option either. I always have to select the second option and it works fine.

---


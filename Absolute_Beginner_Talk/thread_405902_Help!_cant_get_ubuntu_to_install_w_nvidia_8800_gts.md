---
title: "Help! cant get ubuntu to install w/ nvidia 8800 gts"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by evill33tlavlley on 2007-04-10
I just finished building my new computer and i can't get any version of ubuntu to install. I'm new to ubuntu so help is greatly appreciated. I am using the nvidia 8800 gts video card and i do not have onboard video, my mobo is the asus m2n32-sli deluxe wireless edition.

---

### Post by Big Dave on 2007-04-10
More information needed . . .

What do you mean by "I can't get any version of Ubuntu to install"? How far into the installation do you actually get? Are you doing a Live CD install or an alternate install?

---

### Post by evill33tlavlley on 2007-04-10
By any version of Ubuntu I mean 5.04 and up. And for 6.10 (live) it will get to my firewire port and then freeze up.

---

### Post by Roost 12 on 2007-04-10
I assume you are getting the same error I did:
> Fatal server error:
No screens found.

When it asks you if you want to view report select No (selecting Yes only delays your ultimate goal, i.e. to get into the console). Once your screen is all black, hit ctrl+alt+F1 keys to enter terminal (console). Now you need to type this:
> sudo dpkg-reconfigure xserver-xorg

Default options (i.e. the ones linux offers them to you) should be fine for most settings. Important settings are:
[list][*]video card driver (the first option) - make sure to select **vesa**
[*]when it asks you if you want to use FrameBuffer (or something like that), choose "Yes"
[*]make sure to set up your monitor correctly, in my case linux didn't recognize it.  When choosing screen resolution, select the one that you want to use (my LCD works best at 1280x1024...so you chose that one). Also, choose "16" when it asks you about color-depth. If you choose 24-bit xserver (user interface) will most likely fail (I know VGA did in my case because it doesn't support so many colours).
[*]Now you only need to type **startx** into the console.[/list]

These pointers should start Linux environment. Since you have been running Linux from CD so far, make sure to click "Install" on desktop to install your copy of Linux. :)

Now I need to figure out how to install drivers for my video card. >.<

PS: I have GF 8800 GTS 640 MB so these settings work for sure. ;)

---

### Post by evill33tlavlley on 2007-04-10
Unfortunately no I'm not getting that far. It just freezes up, I'm not getting any error messages.
p.s. mine is the PNY manufactured NVIDIA GeForce 8800 GTS w/ 640MB.

---


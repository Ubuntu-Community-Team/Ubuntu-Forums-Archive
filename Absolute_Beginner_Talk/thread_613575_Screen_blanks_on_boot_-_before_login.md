---
title: "Screen blanks on boot - before login"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by Milliways on 2007-11-15
I need help to restore or repair my Ubuntu setup.

When I boot it gets as far as the splash screen, the progress indicator completes, but then the screen blanks before I get to the login prompt.
I can boot in recovery mode, but do not know what to do from here.

Ideally I would like to know how to identify and disable drivers.

History:-
I had loaded Ubuntu 7.04 and been using this for a month.
I upgraded to 7.10, and had problems with Open Office freezing, but resolved this by restoring a standard theme.

I installed a Belkin KVM Switch to enable me to share a monitor etc with another computer, replacing the old monitor, keyboard & mouse I had been using.
I proceeded step by step; first adding a USB mouse, the KVM, a USB keyboard via the KVM, then transferring the mouse to the KVM.
This claims to support Linux and Video up to 2048x1536 @ 65Hz.

This seemed to be working, so I transferred the monitor to the KVM, which I assumed would be a simple replacement.

When I could no longer boot I removed the KVM and reverted to the original configuration, but still could not boot.

After trying lots of other options I managed to boot using an old kernel 2.6.20-16-generic which informed me "Ubuntu is running in low graphics mode". This was 800*640, but anything I did could only make it worse i.e. 640*480.

(One other bitch - Ubuntu will not work below 1024*768 - it just ignores anything which won't fit on the screen.)

---

### Post by alienexplorers on 2007-11-15
Try booting in recovery mode and log in.  Try running:
> sudo dpkg-reconfigure xserver.xorg
When done reboot in normal mode.

---

### Post by SunnyRabbiera on 2007-11-15
I had a similar issue, it seems that the latest version of ubuntu has this bug with the xorg configuration and junk

---


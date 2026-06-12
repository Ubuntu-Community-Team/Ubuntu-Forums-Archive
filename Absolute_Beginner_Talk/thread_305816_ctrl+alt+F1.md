---
title: "ctrl+alt+F1"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by Mazen on 2006-11-24
when i do ctrl+alt+F1 instead of getting a command line or "terminal" i get a weirdly colored screen...i guess it might be a problem with my graphic drivers..not sure...any ideas?
thank,

---

### Post by faraazs on 2006-11-24
Have you set ctrl+alt+f1 to be the hotkey to open a terminal in the keyboard shortcuts?

System | Preferences | Keyboard Shortcuts

---

### Post by junglepeanut on 2006-11-24
This is a bug, you probably also experience if you try to log out of some sessions. I believe you are correct that it is some driver.

I think it was multiply listed last time on Launchpad, search for gray screen too, mine was only gray but recently has been doing pastel colors.

If you are experiencing the same thing I am...

---

### Post by Mazen on 2006-11-24
> **junglepeanut said:**
> This is a bug, you probably also experience if you try to log out of some sessions. I believe you are correct that it is some driver.

I think it was multiply listed last time on Launchpad, search for gray screen too, mine was only gray but recently has been doing pastel colors.

If you are experiencing the same thing I am...

ya i guess pastel colors would describe it well...thanks, and if you have a link to a howto or any posts here that would be gr8...

---

### Post by junglepeanut on 2006-11-24
Many more in Launchpad as it seems to occur many places with different issues (i.e. nobody has really locked it down yet) it is an old bug,..., it also posted here in the forums please use the search button I am to tired to search though all the junk ones for a good one with actual knowledge compared to launchpads as I have done it numerous times.

Jp

[https://bugs.launchpad.net/distros/ubuntu/+source/xserver-xorg-video-ati/+bug/30447](https://bugs.launchpad.net/distros/ubuntu/+source/xserver-xorg-video-ati/+bug/30447)

---

### Post by strabes on 2006-12-11
remove the word 'quiet' from the kernel line of your ubuntu install:
> kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro splash vga=792

---


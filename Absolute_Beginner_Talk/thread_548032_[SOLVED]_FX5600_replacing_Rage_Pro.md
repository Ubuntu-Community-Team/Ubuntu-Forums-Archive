---
title: "[SOLVED] FX5600 replacing Rage Pro"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-09-10
I have a stock Dell Dimension 4100 computer. It came with an ATI Rage Pro 128 card (AGP 4X). I got an MSI Nvidia FX 5600-VTDR128 card.

This OS, Feisty is a fresh install, less than 48 hours ago. 

What is the correct way to change cards?

Can I (merely) change them physically, install the nvidia drivers and them I am good to go?

Do I have to reset the X-ORG? And how, before or after putting the new card in?

---

### Post by gn2 on 2007-09-10
Never done it myself, but I would suggest changing the display driver to "vesa" then swap the cards, then install the NVidia driver.

The command to reconfigure things is: sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Mark_in_Hollywood on 2007-09-11
I report that by

sudo dpkg-reconfigure -phigh xserver-xorg

xserver gave a friendly 'error' message, and backed it's configuration file up.

Next, i shut the computer down, changed cards and fired it back up. The computer defaulted to the Xserver non-graphic window and asked if I wanted to review the settings. I declined, which returned me to a mark@lexington:> prompt. I sudo'd

shutdown -r now

allowed the computer to reboot, ran the recover mode kernel, then shutdown -r now a second time in a row. On restart, I was returned to the Gnome Desktop, I promptly used Automatix to install the Nvidia drivers and am happily running 

Second Life (Linux Alpha -- no voice communication).

thanks, community.

---


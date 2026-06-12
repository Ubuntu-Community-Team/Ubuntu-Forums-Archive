---
title: "Macbook 5,3: blank screen when trying to run 11.04"
date: 2011-07-02
forum: Apple Hardware Users
---

### Post by vibe3 on 2011-07-02
I am currently running Lucid 10.04 without problems and would like to upgrade to 11.04. I created a startup disk on a USB stick with the 11.04 64-bit iso.

When I boot, rEFIT gives me the option of booting from the USB stick. I do that and get a menu with 3 options:

Try ubuntu with out installing
Install Ubuntu
Check disk for errors

When I try the "Try ubuntu without installing" option, I get a blank screen indefinitely (I tried waiting 20+ minutes).

After some searching I found the suggestion to use the kernel option: "nouveau,noaccel=1".

When I insert that line into the options, it outputs a lot of initialization text, finds hardware etc, but then hangs without starting GDM.

If I replace those options with "nomodeset", it boots successfully to a command prompt, but I can't start GDM from that either.

Anyone know what to do? Thanks!

---


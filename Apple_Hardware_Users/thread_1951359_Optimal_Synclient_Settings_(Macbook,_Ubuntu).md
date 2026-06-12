---
title: "Optimal Synclient Settings? (Macbook, Ubuntu)"
date: 2012-04-02
forum: Apple Hardware Users
---

### Post by Roasted on 2012-04-02
I've been tinkering with Ubuntu on a Macbook. I believe it's a late 2007 or early 2008, I kind of forget exactly. Lately I've been tinkering with Synclient, which has dramatically helped out the way the touchpad feels. Now, I don't really care to mimic the "Apple touchpad", I just want it to work half decently and support two finger scrolling. Lately I've been using:

synclient FingerLow=10
synclient FingerHigh=20

It's much better, but a bit clumsy yet. I'm curious if anybody out there utilizes other settings that might make it a bit smoother. Any insight?

FYI - I'm just going to throw those two synclient commands into an .sh file and set it to run at login.

---

### Post by tom.swartz07 on 2012-04-02
Here's some awesome documentation from Arch's wiki: [https://wiki.archlinux.org/index.php/Touchpad_Synaptics](https://wiki.archlinux.org/index.php/Touchpad_Synaptics)

I've used this in the past to set up the 'OSX Lion-style' natural scrolling on my netbooks and laptops.

You will likely have to tweak the instructions a bit, Arch installs some of the config files in different locations. 

Cheers dude.

---


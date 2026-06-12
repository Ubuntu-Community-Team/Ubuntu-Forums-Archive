---
title: "Xorg on Powerbook (pismo) problems"
date: 2005-03-17
forum: Apple PPC Users
---

### Post by thalavoy on 2005-03-17
All,

I recently upgraded to Hoary preview, including Xorg. But after upgrading, I am running into some problems. (Frankly, I had just installed Warty and saw that the preview available. So changed the apt repository to point to hoary and did a dist-upgrade. So did not know what was the behavior in Warty at all)

1. Cant switch to other consoles (Option+Ctrl+fn+Fn does not work), though it was working in Warty

2. Not able to seem to run DRI on Xorg. I have tried many options, but using the ati/r128 driver automatically chooses FBDev to be true. In fact, it ignores the Display section totally.
Not sure if Warty (Xfree) supported it.
Should I go back to Xfree?

3. One mouse question. With the powerbook touchpad, how to emulate middle and right clicks. None of Ctrl+click or Option+click works. 

Thanks for your help

Siva

---

### Post by mirco on 2005-03-17
you'll have to add three lines to the file /etc/sysctl.conf to emulate 2nd +3rd mouse button.

# Emulate the middle mouse button with F11 and the right with F12.
dev/mac_hid/mouse_button_emulation = 1
dev/mac_hid/mouse_button2_keycode = 87
dev/mac_hid/mouse_button3_keycode = 88

This will be available after a reboot

Greetz
        Mirco

---


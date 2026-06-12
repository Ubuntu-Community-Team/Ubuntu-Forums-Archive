---
title: "Keyboard Issues in Grub"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2008-03-24
I'm using an HP laptop and many of the keys on my keyboard don't work while in grub. I've 
already checked the USB legacy option in the bios and that wasn't the issue.

The problem arises on a cold boot and not on reboots. I am able to scroll down with the 
down arrow key, but the up key and the enter button don't work.

I was able to workaround the problem by pressing E to edit and B to boot, but this doesn't 
work on my encrypted partition as it requires the mounting password before booting the 
os. Once I'm in an OS, the keyboard works fine.

I couldn't find any setting in my bios to give priority to the bios for keyboard control as I 
found in an old thread on Google.

Thanks for any help!

---

### Post by Awperator on 2008-03-24
> **shanepardue said:**
> I'm using an HP laptop and many of the keys on my keyboard don't work while in grub. I've 
already checked the USB legacy option in the bios and that wasn't the issue.

The problem arises on a cold boot and not on reboots. I am able to scroll down with the 
down arrow key, but the up key and the enter button don't work.

I was able to workaround the problem by pressing E to edit and B to boot, but this doesn't 
work on my encrypted partition as it requires the mounting password before booting the 
os. Once I'm in an OS, the keyboard works fine.

I couldn't find any setting in my bios to give priority to the bios for keyboard control as I 
found in an old thread on Google.

Thanks for any help!

To understand you better, you're using an external USB keyboard with your laptop, or just the keyboard on the laptop?

---

### Post by shanepardue on 2008-03-24
I am using the laptop's keyboard...no usb keyboard.

---

### Post by shanepardue on 2008-03-26
To clarify, if I boot into Windows using the E, B buttons then reboot once in windows to 
Ubuntu, things work perfectly. Once any OS is booted, the keyboard works until powered 
completely off.

---

### Post by shanepardue on 2008-03-27
I'm contemplating a different bootloader such as lilo because this is unacceptable. I don't want to boot into windows and reboot to get my keyboard working.

If you have any tips of getting another bootloader running with an encrypted partition, let 
me know. Thanks!

---


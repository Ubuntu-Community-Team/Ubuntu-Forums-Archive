---
title: "Before I install...."
date: 2005-08-21
forum: Absolute Beginner Talk
---

### Post by akabugeyes on 2005-08-21
Hello everyone. I really want to install Ubuntu 5.0.4, but before I install it I want to make sure I am completely safe as I don't want to mess anything up with my existing Windows XP installation.

Basically what I have been planing to do is install an additional hard drive on to my computer and install Ubuntu on to that.

So when I partition the drive that doesn't have Windows on it, am I safe to assume that nothing bad will happen to my other hard drive with Windows on it? May sound like a silly question but my brother is worried that something will go wrong and screw up the original hard drive with Windows on it.

---

### Post by jasmuz on 2005-08-21
I assure you that by installing Ubuntu to your additional drive there is no risk for harming your Windows install except for the boot loader that will boot before anything else asking you if you wish to go into Windows or Ubuntu.

---

### Post by Kvark on 2005-08-21
[QUOTE=akabugeyes]Hello everyone. I really want to install Ubuntu 5.0.4, but before I install it I want to make sure I am completely safe as I don't want to mess anything up with my existing Windows XP installation.

Basically what I have been planing to do is install an additional hard drive on to my computer and install Ubuntu on to that.

So when I partition the drive that doesn't have Windows on it, am I safe to assume that nothing bad will happen to my other hard drive with Windows on it? May sound like a silly question but my brother is worried that something will go wrong and screw up the original hard drive with Windows on it.[/QUOTE]
Partitioning isn't the easiest thing to do and a mistake could mess things up. Personally I'd not feel comfortable trying without making a complete backup first. But if you know what you are doing then it should be all right. Might be best to search for some guides and howtos to read up first.

---

### Post by akabugeyes on 2005-08-22
Thank you for your feedback.

I decided to install Ubuntu on my old hard drive in my old computer. And I am loving it so far.  ;-) 

I am hoping to transfer my old hard drive to my computer (Unfortunately it is an internal hard drive and my computer lacks a place to store it, but that is my problem not yours ;))

Now when I put the hard drive in, will the boot loader automatically pick up that there is another OS on another hard drive? Because on my old computer I had a corrupt Windows XP on one hard drive and Ubuntu on the other, and when I took the Windows hard drive out I found that the boot loader would not load at all without both hard drives in.

---

### Post by cayamara on 2005-08-22
[QUOTE=akabugeyes]Now when I put the hard drive in, will the boot loader automatically pick up that there is another OS on another hard drive?[/QUOTE]
No, it won't. But with GRUB, it's easy to configure it that way. And when you install Ubuntu on a computer with Windows, Ubuntu will most likely configure GRUB to give you the choice of which OS to boot.

---


---
title: "Kernel 2.6.22-14 won't load"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by i5sfe on 2008-01-10
I have upgraded to Ubuntu 7.10 but when I try to boot using the 2.6.22-14-generic kernel the following happens....

Starting
Ubunutu splash screen
then stalls before getting to first block on bar and stops loading
all hard drive activity stops
goes to blank screen 
system is still responsive (keyboard lights) but didn't finish booting

For the time being I have edited the grub loader to boot using the older Ubuntu 7.10 kernel 2.6.20-16-generic kernel and it works fine except I can't compile any new software for the kernel because my complier is for the new kernel. Instead of reverting the compiler I would like to diagnose why it will not boot using the new kernel. 

I new to Linux but I work as a Systems Administrator for windows machines so I know my way around computers but need some pointers on diagnosing these issues.

---

### Post by nowshining on 2008-01-10
yes u prob. have what's known as hardware that won't work with that kernel - it has a bug,

OR like me it also didn't work edit: from an upgrade from feisty.

does it work on the live CD? if so then u prob. have what I had, upgrading hosed feisty, best thing is to - backup, esp. ur home folder (all ur settings are there) onto another external medium, format and re-install Gutsy from scratch. Installing Gutsy from the CD/DVD it should format for u.

---

### Post by i5sfe on 2008-01-10
I don't know if this is related by I also can't hibernate because of hardware conflicts. Sometimes I think it would be easier to swap the hardware.:(

---

### Post by nowshining on 2008-01-10
hehe, i only tried hibernating once on feisty - it didn't work for me, never on Gutsy and I have my own custom kernel optimized for my particular CPU - it's .2 behing 2.6.23.11 that I custom compiles - it's really really easy to do and u can add/remove what u need/want from it as well. :)

edit: oh and I disabled hibernating and suspending from my current kernel & stopped it at boot up from resuming..

---

### Post by i5sfe on 2008-01-16
Sorry for the delay.
My computer boots fine on the live CD on the 2.6.22-14 kernel. Could this be that the orginal wasn't compiled correctly?

This weekend I will back-up and reinstall. Since I am new to ubuntu, is there a backup program that is recommended or should I just manually copy my entire user folder?

---


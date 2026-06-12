---
title: "I installed XP after Ubuntu and now I'm trapped in XP !!"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by maramot on 2008-04-14
Can anyone give me instructions on how to set up dual boot after I have installled XP (and after it has taken over my MBR)? I believe it can be done without reinstalling ubuntu.

---

### Post by stchman on 2008-04-14
> **maramot said:**
> Can anyone give me instructions on how to set up dual boot after I have installled XP (and after it has taken over my MBR)? I believe it can be done without reinstalling ubuntu.

Here is a site to help you.

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by 068139 on 2008-04-14
did you install xp and ubuntu to the same drive? ie: C:/

I have the opposite problem, I've installed them to seperate drives but because im using a usb keyboard i cant select to boot xp on the startup...i have a ps/2 keyboard somewhere but its a bit of a hassle really..oh well

---

### Post by Moop on 2008-04-14
> **068139 said:**
> did you install xp and ubuntu to the same drive? ie: C:/

I have the opposite problem, I've installed them to seperate drives but because im using a usb keyboard i cant select to boot xp on the startup...i have a ps/2 keyboard somewhere but its a bit of a hassle really..oh well

There should be a setting in your bios that will recognize your usb keyboard. I can't remember what it's called but it's not hard to find. I can't say every bios has it but the ones I've seen do.

---

### Post by 068139 on 2008-04-14
> **Moop said:**
> There should be a setting in your bios that will recognize your usb keyboard. I can't remember what it's called but it's not hard to find. I can't say every bios has it but the ones I've seen do.

thing is it used to but now I think it's plugged in to a different port, I'll have a play around and see what I can dig up. Thanks

---

### Post by zvacet on 2008-04-14
@ **maramot**

Try [this.](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)

---

### Post by maramot on 2008-04-14
stchman and zvacet -- you rule guys! :) I'm back in Ubuntu. From here on, it's not going to be problem for me to include XP as an OS choice in Grub.
I didn't get the right place (hd0, 0) for root from the first time, but I made a few tries directly from the boot manager by pressing 'e' and 'b' to edit a line in the list and then to boot. Very handy, a baby would have done it. Anyway, thanks again :)

---


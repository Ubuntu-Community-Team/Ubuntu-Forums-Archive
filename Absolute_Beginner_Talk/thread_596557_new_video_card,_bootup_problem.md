---
title: "new video card, bootup problem"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by onearmedpanda on 2007-10-29
i just got a new video card (GeForce fx 5200) upgrading from an intel integrated graphics card. when i boot up the Ubuntu loading screen never fully loads, it always loads about 1/10 of the way then stays there at a standstill. then i switch it back to my old integrated card and it boots up fine. any suggestions on why it won't load?

---

### Post by Crafty Kisses on 2007-10-29
> **onearmedpanda said:**
> i just got a new video card (GeForce fx 5200) upgrading from an intel integrated graphics card. when i boot up the Ubuntu loading screen never fully loads, it always loads about 1/10 of the way then stays there at a standstill. then i switch it back to my old integrated card and it boots up fine. any suggestions on why it won't load?

Can you go into verbose mode?

---

### Post by onearmedpanda on 2007-10-29
whats that and how can i get there?

---

### Post by Crafty Kisses on 2007-10-29
> **onearmedpanda said:**
> whats that and how can i get there?

Basically when it's stuck at the loading screen, do the following:
```
Ctrl+Alt+F2
```
See if that does anything.

---

### Post by onearmedpanda on 2007-10-29
it doesn't do anything

---

### Post by Crafty Kisses on 2007-10-29
> **onearmedpanda said:**
> it doesn't do anything

Try it right before it freezes.

---

### Post by onearmedpanda on 2007-10-29
it went into a black screen with a bunch of stuff scrolling very quickly, and it's been doing that for about 10 minutes the left column contains a number that goes up once a second. so i know it's not repeating.

---

### Post by Crafty Kisses on 2007-10-29
> **onearmedpanda said:**
> it went into a black screen with a bunch of stuff scrolling very quickly, and it's been doing that for about 10 minutes the left column contains a number that goes up once a second. so i know it's not repeating.

Hmmm, weird, wait 5 minutes and see what happens.

---

### Post by az on 2007-10-29
> **onearmedpanda said:**
>  any suggestions on why it won't load?

Are there any bios settings you can change in regards to your new card?

As well, the first time you boot, you will need to reconfigure your display (the X server).  You will need to boot into recovery mode and run

dpkg-reconfigure -phigh xserver-xorg
and then
init 2

to get into graphical mode.  You only need to do this the first time you boot after changing a video card.  You have to do thatn when you change your card back, too.

I doubt you will be able to boot into recovery mode until you settle your hardware problem.  But try it anyway.  There is a chance that your problem is due to the old integrated card driver trying to access conflicting hardware.

---

### Post by onearmedpanda on 2007-10-29
i tried the ctrl + alt + f2 thing and it stopped with the last two messages being:

[28.999289] [<c02f0000] clip_ioctl+0x500/0x510
[28.999408] ================

any ideas?

---

### Post by onearmedpanda on 2007-10-29
i looked in the bios and the options for primary video adapter are onboard and auto. i don't think either are the card. just the integrated controller.

---

### Post by az on 2007-10-30
> **onearmedpanda said:**
> i looked in the bios and the options for primary video adapter are onboard and auto. i don't think either are the card. just the integrated controller.

What is it set to?

Setting it to Onbpard will use the onboard video regardless of whether there is another one present.  Auto will use the other one by default.

Try booting into recovery mode and see how far you get.  You boot into recovery mode by pressing escape to reveal the grub menu at boot time.  Then pick the recovery mode option.

---


---
title: "darkened second monitor"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by stainless_steel on 2008-04-05
hi,
ive got a dual monitor setup, and everything was fine until i booted yesterday and my secondary monitor looked like it had a dark filter over it. i swear i didnt change anything.  of course i tried to adjust brightness to no avalil. checked the cables: nope. i took a screenshot and it looked fine. then i plugged the monitors into the other ports to see if it was just a broken monitor: it wasnt. the filter switched to the other monitor. i booted from the cd - scondary monitor resolution out of range (still dark during boot sequence) I booted in safe graphics mode: still dark.

its dark during boot sequence, its dark in a virtual terminal, and its dark in safe graphics mode.
so im guessing its a busted v-card, which would really suck cause its kinda new and returning it would be a huge hassle

specs:
nvidia g-force NX6200AX card
proprietary "nvidia" driver
the secondary monitor is a vga plugged into a dvi adaptor (i swapped out the adaptor to with no change)
i dont think its relevant but heres my xorg.conf

thanks a lot everyone!

---

### Post by stainless_steel on 2008-04-05
oh, and also,
i tried to mess around with nvidia-settings (which is great) but it doesnt color configuration options for the secondary, just the primary.

---

### Post by reeseslover531 on 2008-04-05
it could be your monitor, can you test your monitor on another computer?

---

### Post by stainless_steel on 2008-04-05
no, but the monitor works fine when i plug it into the primary port.
and now it seems that the secondary has gradually gone completely black
crap

---

### Post by bsalus01 on 2008-04-17
i'm having the same problem! (in 8.04)

my laptop monitor worked fine, but when i enabled twin view my secondary monitor is fine and the backlight on my laptop monitor is off.

help!

---

### Post by euxneks on 2008-04-25
I found that if you restart your window manager it returns it back to normal. (I use fusion-icon to do this)

---

### Post by stainless_steel on 2008-04-25
im not sure what a window manager is or how to restart it. restarting the computer didnt help though.

---


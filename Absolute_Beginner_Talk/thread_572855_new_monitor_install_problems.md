---
title: "new monitor install problems"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by onearmedpanda on 2007-10-10
i just bought a new acer 22" widescreen lcd and i first plugged it in and it all worked, but the max resolution was 1024 x 768 but the max resolution on the monitor is 1680 x 1050 so i reconfigured  xserver-xorg and then when i restarted the computer and chose my os in GRUB then the screen stays black and after a minute or so my monitor turns off and back on (just as usual) but instead of displaying the login screen it come up with a message that says "input not detected"

i tried to fix it up plugging up my old monitor and uninstalling and reinstalling the xserever-xorg to get the defaults back (the ones that worked one the new acer originally. any suggestions on just how to get the new acer to work again? thanks in advance

---

### Post by taurus on 2007-10-10
What video card do you have and have you installed any driver for it?

---

### Post by onearmedpanda on 2007-10-10
i don't know, some integraded video card
how can i find out what it is?

---

### Post by taurus on 2007-10-10
Applications -> Accessories -> Terminal
```
lspci | grep VGA
```
Some video cards won't be able to display at high resolutions so you need to look at the manual to see if your onboard integrate graphic controller can go up to 1680x1050.

---

### Post by onearmedpanda on 2007-10-10
i figured out it's an intel
i don't even care about the high resolution anymore
i just want the monitor to work period, at any resolution

---

### Post by onearmedpanda on 2007-10-10
i think i may have misconfigure xserver-xorg
on the part where it ask you what you video card driver is,i just put whatever it came default with, but i looked it up and my driver is 845G, but that's not on the list, what do i do?

---

### Post by onearmedpanda on 2007-10-10
i just went back and double checked and it says "input not supported" i'm not sure if that makes a difference

---

### Post by yuku-aki on 2007-10-10
I had this problem when hooking up my laptop to an external monitor or TV via S-Video; what I have to do sometimes is reset my resolution using a working monitor (your old one, if you still have it - or borrow one, maybe?) Reset, change the connection, and try logging in.

If this doesn't work - one of two things happened:

One - The resolution you chose was still too big or small. Keep changing them on the other monitor until it looks right.

Two - The resolution of your login splash is too big or small; this can easily be temporarily evaded by just logging in anyway by feel.  If you can type your login/pass by touch rather than by seeing it, this shouldn't be difficult.  Your window manager will change to the correct resolution once you're logged in, then you can change the resolution of your splash screen.

Hope this helps.

---


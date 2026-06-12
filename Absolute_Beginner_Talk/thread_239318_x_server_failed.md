---
title: "x server failed"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by g8m3rtag on 2006-08-19
im trying out ubuntu with the live cd/installer and when i first loaded it up i chose the first option i believe its run or install ubuntu. i got the x server failed message with the text on the screen all spread out and stuff. i then loaded the disc and pressed f4 to change the resolution to 1024x768x24 and got the same thing, then i tried the safe graphics mode and it didnt work either.

im using an old 3dfx pci card for that monitor, and i have another lcd plugged into my onboard agp slot which is on an intel d845grg board. the primary monitor however is the one running off the 3dfx card.

what else can i try to get the live cd version up and running so i can try out ubuntu. i have very limited experience with linux, and by very limited i mean i used gaim on a friends laptop that was running linux once, so step by step information would be greatly appreciated.

---

### Post by g8m3rtag on 2006-08-19
ok i switched my primary monitor from the 3dfx to the onboard intel and i booted into the live version of ubuntu without a problem (im posting from it:-D ) 

now my problem is that only the primary monitor is working. does ubuntu support dual displays, i checked in the device manager and it sees the other graphics card, but that monitor wont detect anything, it just stays black. 

is there a way i can get my dual display to work?

---

### Post by djsroknrol on 2006-08-19
You might try in a terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

To see if it picks up the other card...don't forget to reboot...

And yes, it supports multiple monitors...If need be you could write it into your xorg.conf file...

---


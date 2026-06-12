---
title: "on-going issue - white screen at log on"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by tchoklat on 2007-06-13
I have a fresh Feisty install - fresh as I was having permission issues so thought I would reinstall to make my life easier - or so I thought.
 
I get to enter my user name and password, get the nautilus flash screen - but only for a moment (the services loading ar not shown). I then get a white screen!
 
Going to a teminal prompt (Ctr alt F1) I have tried sudo dkpg-reconfigure etc and tried Vesa, nv, and a few other drivers (I am using NVidia 7600GT) but to no effect. One thing, at the terminal prompt as X is running do I need to turn it off before I reconfigure X? If so what is the command? I mention this as after reconfigure, the command 'startx' says that X is running!
 
 
The system ran perfectly with this card in the past and other distros on my HDD run perfectly with Nvidia drivers also - it is just this install of feisty (I have installed and reinstalled three times to no avail).
 
Any assistance would be helpful.

---

### Post by shearn89 on 2007-06-13
the command to kill X would probs be something like:

```
kill $(pgrep X)
```

I don't know if that helps?

---

### Post by diatribe on 2007-06-13
after you have reconfigured your xserver; ctrl-alt-bksp will restart it

---


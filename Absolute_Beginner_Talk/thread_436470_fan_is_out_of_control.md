---
title: "fan is out of control"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by xthund3rh3adx on 2007-05-07
hey, i just installed ubuntu again on an older model PC, origninally had Windows Me.

Everything is working fine, except for one thing: My fan is running like a madman! It runs at max no matter what state the computer is in; idle, working, doesnt matter -- its always at max speed.

i dont know if i should be concerned or not, but i do know it gets quite annoying at night.

Any suggestions/tips? im pretty desperate here...

Dell Optiplex
Intel Celeron (Coppermine) 800MHz
20GB HD
Ubuntu Feisty

---

### Post by goumples on 2007-05-07
An out of control fan probably means alot of heat inside the case.. try checking your hardware specs versus the recommended specs for the Operating System.. if that checks out then you might want to consider a better fan, or an additional fan.

---

### Post by xthund3rh3adx on 2007-05-07
everything is fine and checks out. The computer can be off for 3 days, and then id start it up and it would still be  at maximum

---

### Post by jimrz on 2007-05-07
> **xthund3rh3adx said:**
> everything is fine and checks out. The computer can be off for 3 days, and then id start it up and it would still be  at maximum

what make and model? also, what is the date of your BIOS? do you see a warning about BIOS date and acpi when you boot'er up?

i still have my old ThinkPad 600x ... it has the latest BIOS made for it but they are dated 1999, the cutoff date for BIOS to work with acpi in the recent kernels is 2000 ... to resolve this and get proper acpi i append the followig to the kernel line in /boot/grub/menu.lst:
```
acpi=force pci=noacpi
```

force makes the acpi work and the pci=noacpi is there because force by itself on that machine renders my pcmia slots useless and this corrects that, so both function properly.

if this is the case with your box, each time there is a kerel update this will need to be done again for the new kernel line.

---

### Post by xthund3rh3adx on 2007-05-09
how can i update my BIOS?!

---

### Post by teknosexual on 2007-05-09
All the above is good advice, but don't overlook the simple things... open up the case and blow out all the dust with compressed air. Dust buildup can have a huge affect on a fan's performance!

---

### Post by xthund3rh3adx on 2007-05-09
thanks......anything on updating BIOS?!

---

### Post by xthund3rh3adx on 2007-05-09
.....bump

---

### Post by jimrz on 2007-05-12
> **xthund3rh3adx said:**
> thanks......anything on updating BIOS?!

you should be able to get the latest BIOS update from your laptop's manufacturers site. however in some cases, my TP 600x is one, although the latest update actually came out in 2001 the date string in the new BIOS still shows the original date (in mine's case) 1999 and therefore does nothing to alleviate the issue since that is where the kerenl reads the date info from.

---


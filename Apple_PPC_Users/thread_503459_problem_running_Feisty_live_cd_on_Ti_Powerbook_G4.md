---
title: "problem running Feisty live cd on Ti Powerbook G4"
date: 2007-07-17
forum: Apple PPC Users
---

### Post by zubala on 2007-07-17
The live cd boots up fine until after the username prompt.  but it just freezes afterwards with an orange screen. i can move the pointer and I can get to terminal using ctl alt F1 but I don't really know what to do at that point since I don't know anything about terminal commands. or computers for that matter. Anyone have any suggestions?

This is a much abused Powerbook with a non-working hard drive.  I was gonna throw it away but I thought I'll give the live cd a try. Can the Feisty live cd even run  properly on this thing without a hard drive?

Thanks!

---

### Post by stmiller on 2007-07-17
Hey unfortunately this is a bug on the live CD, but here's what you do to get to the desktop:

When it boots to the blank brown / orange screen, hit Cntrl+Alt+F1 to get to a terminal window and type
```

killall esd

```
and hit enter. Now press Cntrl+Alt+F7 to get back to the desktop, if needed. And all should be fine now.

---

### Post by zubala on 2007-07-17
That worked! It doesn't recognize any hard drives or USB drives and I get warnings that Nautilus doesn't work but internet works and at least I know this computer isn't quite dead yet.

Thank you!

---

### Post by AceofAzrogoth on 2007-07-20
I have the same problem on a Powerbook G4 laptop, however this fix seems to not do anything.

I get the brown/orange screen and can open terminal using ctrl+alt+F1, but when I type the command and hit enter the text cursor goes down one line and nothing happens. Hitting ctrl+alt+F7 returns me to the blank orange screen.

Thanks!

---


---
title: "I hate this 'X' thing"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by lovloss on 2006-11-05
My external HD linux isn't working on other people's computers because of this 'x' system. Is there any auto-detect functionality? This doesnt seem to have any. Or at least, some othe rloophole?

---

### Post by K.Mandla on 2006-11-05
It might help, after you boot on their machine, to try

```
sudo dpkg-reconfigure xserver-xorg
```
Just an idea, anyway. ;)

---

### Post by lovloss on 2006-11-05
Were it only so simple :( Believe me, thats the first thing I tried. It wont autodetect or anything , and i dont know their exact system layout. i dont think they even have a card, just a chipset. But gnome loaded up from the live cd, so it shouldnt be like this.

---

### Post by Chayak on 2006-11-05
I can't remember the package name atm but look at knoppix's autoconfigure system.

---

### Post by TheMono on 2006-11-05
You could try setting X to using very generic settings, ie, the vesa driver (which will work on almost anything), low resolution, etc...

---

### Post by idjut on 2006-11-05
Check in the bios if UMA is set to 1mb and change to 8mb if it is.

---

### Post by bulldog on 2006-11-05
> **lovloss said:**
> My external HD linux isn't working on other people's computers because of this 'x' system. Is there any auto-detect functionality? This doesnt seem to have any. Or at least, some othe rloophole?

I don't know if I understand you correct,but are you trying the install you made for your own computer on an external harddisk,to boot on an other computer?

Or are you trying to do a new install from the live cd on other computers?

If you try the first option I'll think it fails.
Do this with a windows install and it fails too.:D 

If you try the second option it should work if the live cd run nicely,you can run the install.

If I don't understand anything at all what you're trying to do,don't read this at all,I'm just wake up :D

---

### Post by spinflick on 2006-11-05
> I hate this 'X' thing Dont you just love it when people talk all geeky ;)

---


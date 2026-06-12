---
title: "Installing new dvd burner (how to)"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by ikkem on 2007-03-08
I just bought a new dvdburner the question I wanted ask is what should I do to install it I tried searching google but have not found a how to yet....

thanks in advance....

---

### Post by Bachstelze on 2007-03-08
You should have nothing particular to do. If it's an IDE burner and your BIOS detects it, Ubuntu should detecct it too.

---

### Post by AtrejuT on 2007-03-08
Well I don't really know, but what I'd try is build it in, start up Ubuntu and see if its not recognized automatically. I think your chances should be pretty good there.

atreju

---

### Post by enopepsoo on 2007-03-08
I would take a side off the case, and attach the power cable.  It will only go on one way.  The other flat cable is called an IDE cable.  The red stripe goes to the pin labeled 1 on the back.

Once you have those two cables attached, boot up and Ubuntu should find the thing.  If not, there is probably an issue with the cable.

If your computer wont boot at all, it means that there is a problem with a jumper.  You will have to check the other drive that the cable is plugged in to to see what mode it is in.  If it's jumper has it set to MA=master, set your burner to SL=slave.  if the other drive is set to CS = cable select, then set the burner to CS.

It is possible that you have an SATA burner, in which case you should just have to plu the burner directly into your motherboard, and everything will work, but not many burners use this.  The way to tell the difference is that if your burner has 40 pins sticking out of the back of it, it is IDE.  SATA is really a lot easier.

:)

---

### Post by laidback on 2007-03-08
Just plug it in; check you have power connection and ribbon cable properly attached to the rear of the drive. Switch on and test.

---

### Post by ikkem on 2007-03-08
Thanks to all for reacting I just installed the dvdburner but it does not seem to get recognised I will continue looking into it later on....

---

### Post by Bachstelze on 2007-03-08
Is it recognized in your BIOS ?

---

### Post by ikkem on 2007-03-08
> **HymnToLife said:**
> Is it recognized in your BIOS ?

I just noticed that the flatcable was not properly connected :oops:

---

### Post by undertakingyou on 2007-03-08
So is it recognized?  it really should just fire up, no problem :)

---


---
title: "Headphones &amp; Speakers at the same time"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Elitegunslinger on 2007-11-27
I read prior to asking this question about the alsa mixer head phone jack option.  However it isn't showing up.  I get sound from both the headphones and speakers at the same time.  Is there anyway to get the option to detect the headphone jack for my model laptop?

Compaq
C712NR
or C700

HDA Intel if that helps

Many thanks in advance.

---

### Post by lespaul_rentals on 2007-11-27
Have you checked the BIOS for an option regarding this?

---

### Post by Elitegunslinger on 2007-11-27
I remember looking but not finding anything.  Should I be looking for something in particular?

---

### Post by FuturePilot on 2007-11-27
Press Alt+F2 and enter
```
gnome-volume-control
```
Try muting Master and adjust the headphone slider if necessary

---

### Post by Elitegunslinger on 2007-11-27
there is no headphone slider or bios option

---

### Post by sailor2001 on 2007-11-27
right click sound icon and open volume control..then edit/preferences and check/uncheck what needs to be done

---

### Post by FuturePilot on 2007-11-27
> **Elitegunslinger said:**
> there is no headphone slider or bios option

Open the volume control again and go Edit>Preferences. See if there is a check box for Headphone

---

### Post by annda on 2007-11-27
some sound chips will not have the 'headphone' option. mine doesn't (also a member of the intel HDA family). you can see if this is the case with your hardware by chcecking all the possible options in volume control preferences.. maybe a switch or a slider will show up somewhere.

we will just have to wait until the ALSA team gets to that.

---

### Post by Elitegunslinger on 2007-11-27
Master, PCM, LineIn, IEC958, Digital, Ext Mic, Int Mic, IntMic

No headphone

---

### Post by kodoku on 2007-11-27
I have a similar issue on a desktop.

In my case, the headphones option does show up.  Checking and unchecking the option turns on or off the headphone jack in front.  However, is there a way to have the speakers turn off when I plug in the headphones?  Right now, I'm having the aforementioned issue of headphones and speakers functioning simultaneously.  I've pulled up gnome-volume-control and exhausted all the options I could find to no avail.  Any help would be greatly appreciated!

---

### Post by Neonjack on 2007-12-02
Same here.....

---

### Post by CLI-Linux on 2008-01-28
I have the same problem on my C700.  Both the headphones and speakers play at the same time and there's no options to switch either of them off.  Is there a fix for this that's being worked on?

---

### Post by billgoldberg on 2008-01-28
I would also want to know a solution.

Turning the subwoofers button to zero only takes a second, but automating that would be better.

---


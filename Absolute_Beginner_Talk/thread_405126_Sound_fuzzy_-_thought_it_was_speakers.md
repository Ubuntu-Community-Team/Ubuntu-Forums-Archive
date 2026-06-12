---
title: "Sound fuzzy - thought it was speakers"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by awiggin on 2007-04-09
Hey,

I've got sound but the quality isn't quite right.  I thought it was my speakers because they are a bit old and the sound problem is similar to what happens when you blow a speaker out - a little buzzing.

But the speakers don't do that in my other OS.

Any ideas what might cause this?

Cheers - 

Lance

---

### Post by ComplexNumber on 2007-04-09
what sound card are you using?

---

### Post by 3rdalbum on 2007-04-09
Right-click on the speaker icon in the top-right corner of your screen and choose "Open Volume Control". Check that the PCM channel isn't at 100% - I'd turn it down to approximately 80%.

Now go to the File menu, Change Device, and change it to the other device if there is one. Check the PCM volume in that mixer too, if it is there.

---

### Post by awiggin on 2007-04-09
I tried lowering the PCM to about 80%, but it still hisses a little.

How do I find out what kind of sound card I have?

---

### Post by ComplexNumber on 2007-04-09
> **awiggin said:**
> I tried lowering the PCM to about 80%, but it still hisses a little.

How do I find out what kind of sound card I have?
right click on the volume applet and open the volume control. then go to the menu and select 'change device'. list the options that it gives you and tell me what sound device is selected.

---

### Post by awiggin on 2007-04-09
The one selected said:

HDA Intel (Alsa mixer)

The unselected one said:

SigmaTel STAC9221 A1 (OSS Mixer)

---

### Post by ComplexNumber on 2007-04-09
which iof those(if any) is your onboard sound card and which one is your main sound card?

---

### Post by awiggin on 2007-04-09
The SigmaTel is my sound card.

---

### Post by awiggin on 2007-04-09
Not sure what the difference is between main sound card and onboard sound card.

I had to go out to Windoze to look up what card I had.

---

### Post by ComplexNumber on 2007-04-09
on my system, i have an inbuilt sound card thats inbuilt into the motherboard. it comes with the PC when you buy it. some people like to upgrade their sound card, so they add a better one in one of the expansion slots in the PC......but they forget todisable the onboard sound card. you can disable it by going into the BIOS and disable it there.

---

### Post by Settesh on 2007-05-17
I had the same problem. I installed Ubuntu Studio and it was fuzzy in the speakers.  I went into volume control and clicked on the "Switches" tab and there was a check box nest to "SB Live Analog/Digital Output Jack".  I unchecked it and the fuzzyness went away.  

I don't know if it is the same for you though.

---

### Post by MFerrante713 on 2007-08-27
Go into volume control, file, change device, select the first option with the following bars

PCM, Front Mic, Line in, CD, PC speaker.

set front mic at 0%

Thats what did it for me.

---

### Post by Gomek on 2007-09-12
> **Settesh said:**
> I had the same problem. I installed Ubuntu Studio and it was fuzzy in the speakers.  I went into volume control and clicked on the "Switches" tab and there was a check box nest to "SB Live Analog/Digital Output Jack".  I unchecked it and the fuzzyness went away.  

I don't know if it is the same for you though.

Holy crap, this one worked for me.  I've had this problem ever since I upgraded to Gutsy.  Thanks!

---


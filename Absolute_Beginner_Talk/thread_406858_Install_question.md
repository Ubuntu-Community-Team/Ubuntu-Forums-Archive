---
title: "Install question"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by Quickened on 2007-04-11
I burnt a fiesty disk not too long ago. The problems i am having is that when i choose

start or install
start in safe graphics mode
install with driver update CD

it just goes to a black screen and never does anything else. So technically i cant run the live CD. I guess my question is .... would this be caused by a problem during the burning process? Would burning it at a slower speed help?

Thanks for your time! I appreciate it :)

---

### Post by oilchangeguy on 2007-04-11
please advise your computers specs.

---

### Post by Quickened on 2007-04-11
surely

Intel(r)
celeron(r) CPU 2.20 GHz
256mb RAM

I think this is what you needed to know. I am a bit noobish about that kid of stuff

---

### Post by annda on 2007-04-11
what about the graphic card? that may be a problem, too.

---

### Post by Quickened on 2007-04-11
> **annda said:**
> what about the graphic card? that may be a problem, too.

I am not entirely sure. Would i have to pop open the box to find out?

---

### Post by Quickened on 2007-04-11
I dont know if mentioning this matters... but i had no problems with my edgy disk in this department.

---

### Post by annda on 2007-04-11
i assume you are posting from windows on your computer - is that right?

if so, you can find it out in system information. i'm not quite sure but it must be in the control panel, or you can right-click on "My computer" on your desktop and find device manager. i think it's called that.

the most important thing is the manufacturer: is it intel? ati? nvidia? or something else?

---

### Post by oilchangeguy on 2007-04-11
ok, this falls under, if it ain't broke don't fix it. i'm not sure what the system requirements are for 7.04, but just as with each version of windows requiring more power, so does ubuntu, just not as much as windows does.

---

### Post by annda on 2007-04-11
> **Quickened said:**
> I dont know if mentioning this matters... but i had no problems with my edgy disk in this department.

this is rather strange. but try to change the video mode (i think it's F4).

or you can try F6 for extra boot options: for example, vga=791 or resolution=1024x768

---

### Post by chaplanger on 2007-04-11
Quickend,
To identify your video card:

From within Windows -- Right click on "My Computer" Choose "Properties"
click on the "Hardware" tab and then choose "Device Manager"
From within "Device Manager" find the item "Display Adapters" -- click on the + sign by it and this will list your video card.

---

### Post by sailor2001 on 2007-04-11
you're ram is too light..increase to at least 512   ..also burning iso should be at 4x

---

### Post by jputman01 on 2007-04-11
Does the screen just go completely black and nothing else at all, or does it attempt to load then go black? trying to dl from a different place or burning at a slower speed could help, sounds like could be video card issue too, i've had something similar on most ubuntu distros ive tried on my laptop, ive always had to use noapic command to get the live cd to boot

---

### Post by Quickened on 2007-04-11
> **annda said:**
> i assume you are posting from windows on your computer - is that right?

if so, you can find it out in system information. i'm not quite sure but it must be in the control panel, or you can right-click on "My computer" on your desktop and find device manager. i think it's called that.

the most important thing is the manufacturer: is it intel? ati? nvidia? or something else?

Yes i am currently posting using XP.

I didnt see anything pertaining to the device manager when i did that. But when i went to the control panal i switched it to classic view so i could easily view everything and i noted an icon called Intel(r) extreme graphics. After reflecting on this post i would be led to assume that is what it would be (intel)

---

### Post by Quickened on 2007-04-11
> **chaplanger said:**
> Quickend,
To identify your video card:

From within Windows -- Right click on "My Computer" Choose "Properties"
click on the "Hardware" tab and then choose "Device Manager"
From within "Device Manager" find the item "Display Adapters" -- click on the + sign by it and this will list your video card.

Ah thank you for the easy step by step instructions :)

I have an Intel(r) 82845G Graphics controller

---

### Post by Quickened on 2007-04-11
> **jputman01 said:**
> Does the screen just go completely black and nothing else at all, or does it attempt to load then go black? trying to dl from a different place or burning at a slower speed could help, sounds like could be video card issue too, i've had something similar on most ubuntu distros ive tried on my laptop, ive always had to use noapic command to get the live cd to boot


It seems like it attempts to load and then goes black. For a short while you can hear that it is reading the disk but then that just stops all together.

If i want i can ctrl-alt-del and it will automatically reboot from this point.

---

### Post by rgd55 on 2007-04-11
I had a similar problem and just pushed one of the keys and the monitor started as if
it was in a sleep mode.

---

### Post by Quickened on 2007-04-11
I noticed something. I was going to try the F4 advice at the bootup screen and i inserted the disk while XP was still running. The disk booted and it showed that i could try some of the programs. (firefox, blender, abiword)

So it seems that it worked in that case. I hope that made sense when i was wording it.

So i will try a different disk perhaps.

---


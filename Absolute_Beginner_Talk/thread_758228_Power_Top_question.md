---
title: "Power Top question"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by spectrevk on 2008-04-17
Lately I've been concerned about the power consumption on my laptop, as I just don't seem to be getting the battery performance that I was getting under XP, and often it seems like the estimate of battery power that Ubuntu's power management makes are wildly inaccurate. 

Recently I heard about something called Powertop that's supposed to be helpful in this area, but I was wondering if there is already something similar in Ubuntu's distribution that I could be using to get better battery performance, or at least isolate the programs that are creating the most problems.

---

### Post by neurostu on 2008-04-17
So there are a lot of power saving features that have been worked into the windows OS. Power consumption is one thing that windows really beats linux at.

Here is a thread I started earlier about conserving battery life. Its about seting up ubuntu to let you slow down your CPU clock speed (it is REALLY EASY TO DO)  and it has added a few minutes to my battery when I've really needed it.

[http://ubuntuforums.org/showthread.php?t=734556](http://ubuntuforums.org/showthread.php?t=734556)

Check it out and let me know what you think.

---

### Post by neurostu on 2008-04-17
That post was kinda messy so here is the meat and potatoes of the post:

> 

Here it Ok so to turn on CPU Scaling frequency I did the following:

Code:
[code]
sudo dpkg-reconfigure gnome-applets

I clicked OK then I selected YES.

Then I added the CPU frequency monitor to my desktop panel, no simply clicking on it will allow me to set the desired frequency by hand!!



---

### Post by PurposeOfReason on 2008-04-17
You could always
```
sudo apt-get install powertop
``` and check what the damage is.

---

### Post by spectrevk on 2008-04-18
Slowing down the CPU? I can see how that would use less power, but isn't it also kind of counterproductive? Is there a way to slow it down for simpler processes, but speed it back up when more power is needed?

---

### Post by Trail on 2008-04-18
My CPU does that automatically (slowing down when idle and full speed when under pressure, that is). I have a Dual Core2. And KDE at least handles this nicely. I can also right click the power manager and select between Dynamic, Powersave and Performance CPU policies.

I found powertop quite nice as well. It suggests (and executes) several actions to conserve battery and it seems to have a noticeable effect.

---

### Post by spectrevk on 2008-04-29
Powertop has left me with a rather odd problem. After making a change involving my DVD-ROM drive's power useage, my drive no longer works in Ubuntu. I think it's no longer loading the driver correctly. The error message says "Cannot mount volume." Details say:

```
mount: block device /dev/scd0 is write-protected, mounting read-only mount: wrong fs type, bad option, bad superblock on /dev/scd0, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg|tail or so
```

So I tried that, but dmesg|tail gives me this:

```
[ 3272.820421] psmouse.c: Failed to reset mouse on isa0060/serio1
[ 3272.834021] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3272.841706] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3272.844075] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3272.846269] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3272.856010] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 3272.856020] psmouse.c: issuing reconnect request
[ 3272.965843] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input10
[ 3272.997724] psmouse.c: Failed to enable mouse on isa0060/serio1
[ 3276.074717] UDF-fs: No fileset found

```

---


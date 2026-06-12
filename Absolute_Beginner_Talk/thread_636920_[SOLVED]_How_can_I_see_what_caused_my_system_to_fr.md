---
title: "[SOLVED] How can I see what caused my system to freeze?"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by NickGray on 2007-12-10
I have been using **Ubuntu 7.10** for the past one week. It's great! But I still have a lot to learn as a newbie.

Today I am trying to install Mythbuntu on a fresh install of Ubuntu 7.10. But my system seems to be hanging a lot while using Synaptic Package Manager. The computer stops responding to input from the mouse and keyboard, so I do not think I can enter a terminal window. Even CTRL+ALT+DEL does not work, so I have to reset power to the box and boot up fresh.

**Is there a terminal window or an error log that I can view after a hard-reset to the system to see what caused the computer to freeze?**  It would be nice to know what process the computer was working on last. Perhaps I could poke around on these forums and see if there is a fix.

Thanks,
Nick

---

### Post by ptn107 on 2007-12-10
Type this in a termnal:
```
dmesg > errors.log
```

This will create an *errors.log* file in your home folder.  Browse through the file and look to see if you can spot any system errors.

---

### Post by NickGray on 2007-12-11
Still having trouble with my computer freezing up. This is a fresh install of Ubuntu 7.10 that I have had for less than two days, and it still locks up. Some details...
[LIST]
[*]The mouse is active, but the system is non-responsive to mouse input.
[*]The keyboard stops giving input. Caps Lock and Num Lock lights will not engage.
[*]The system clock (top right of screen) freezes.
[/LIST]
I tried the command that **ptn107** suggested (*reading through the dmesg > errors.log file*) but did not notice anything abnormal.

How can I find out and fix what is causing my machine to lock up?

---

### Post by NickGray on 2007-12-11
Here are the last few lines of output from** dmesg** before I had to hard-reset the machine:

```
[   48.105635] intel8x0_measure_ac97_clock: measured 54717 usecs
[   48.105639] intel8x0: clocking to 46900
[   48.627929] lp0: using parport0 (interrupt-driven).
[   48.676240] Adding 835340k swap on /dev/hda5.  Priority:-1 extents:1 across:835340k
[   48.972772] EXT3 FS on hda2, internal journal
[   50.157162] No dock devices found.
[   50.297054] input: Power Button (FF) as /class/input/input4
[   50.301528] ACPI: Power Button (FF) [PWRF]
[   50.337321] input: Power Button (CM) as /class/input/input5
[   50.341728] ACPI: Power Button (CM) [PWRB]
[   50.571555] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (version 2.00.00)
[   50.575862] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
```

---

### Post by NickGray on 2007-12-12
Could a swap file that is too small be causing these lock-ups? I have 1GB of memory, but my swap partition is only 900MB.

---

### Post by NickGray on 2007-12-13
I switched video card drivers, and that may have solved my freezing problems.
I have an ATI video card and am now using the ATI proprietary drivers (unsupported by Ubuntu). My system has not locked up in three hours. I will update this thread tomorrow and mark it SOLVED if my luck continues.

---

### Post by NickGray on 2007-12-13
I have been running great all day with the proprietary ATI drivers, with no freezes. I will go ahead and mark this thread as SOLVED - although I still don't know how to **open a terminal window or an error log that I can view after a hard-reset to the system to see what caused the computer to freeze**.

---


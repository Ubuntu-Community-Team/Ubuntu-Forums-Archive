---
title: "Identify USB port"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by luken8r on 2006-10-17
Hi
Excuse my n00bity, but I am in my first week of Ubuntu-dom and have probably a really simple question.  Probably so n00bish that I dont even know what to search for.

I need to communicate to a external part via serial, but my PC doesnt have a serial port. I just installed the minicom terminal interface and I need to point it to my USB->serial dongle. How do I identify which port my USB port is on for this serial link?
Under minicom, I go to 'Serial port setup' and select 'A - Serial Device'
It currently reads /dev/tty8.  What is /tty8 and how do I recognize which port my device is hooked into

---

### Post by adwait on 2006-10-17
I am not sure, but I think you could try this:
```
lsusb
```

---

### Post by luken8r on 2006-10-17
Thanks for the tip. I actually already got it. I was trying the lsusb, but it was giving me an error saying the command not found. As it turns out, I had multiple terminals open and was trying that command on the box and not the PC OS

Port was /dev/ttyUSB0

---


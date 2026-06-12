---
title: "Disabling onboard sound"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-10-14
I am trying to disable my onboard sound so that I can use my new sound card.
Can anyone give me some tips?

---

### Post by trak87 on 2007-10-14
You need to enter the computer's BIOS chip. This happens BEFORE Ubuntu starts up and just after reboot. On my desktop system I press the Del key to enter this area. It may be different on your computer. Look at the screen during bootup for a hint of a keystroke. But once there, look for the option to enable/disable the onboard audio system.

If you don't find which key to hit, look in your computer manual or check your motherboard manufacturer's online documentation.

---

### Post by klytu on 2007-10-14
If you can't find the BIOS setting to disable the onboard sound, you can try making the new card the default sound device in Ubuntu.  As trak87 posted, I would try the BIOS route first.

---

### Post by skompier on 2007-10-14
Not sure how old your m/b is, but some had a jumper on the board that needed to be moved in order to disable onboard sound. I suspect it's in your BIOS under Integrated Peripherals though.

---


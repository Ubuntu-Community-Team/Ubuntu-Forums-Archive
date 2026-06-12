---
title: "how to get detailed startup screen?"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by Underpants on 2007-01-29
During my system boot and shutdown, I don't get the graphical display, I only show a blinking cursor in the top left of my screen..

Is this a problem with X11 config or in menu.lst?

please advise

---

### Post by Denn1s on 2007-01-29
do u mean u dong get the ubuntu letters and the bar?  try the recovery mode in grub to see the details, hav u edited any files recently?

---

### Post by jbayone on 2007-01-29
You may also want to check your BIOS to make sure the correct video card is enabled.  I had something simlar to this and had to enable AGP in the BIOS.

---

### Post by highneko on 2007-01-29
Maybe this guide will help? Maybe it's a similar situation. If it was working once, then this might fix it. If it never did work and the last thing you did was install ubuntu then don't follow guide.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Underpants on 2007-01-29
I'm using an onboard intel video card. 

Correct: I'm not getting the long bar and ubuntu logo. 

It was like this fresh out of the box.

---

### Post by Denn1s on 2007-01-29
intel's cards give troubles, check your drivers, there are many guides to install the correct drivers since xgl/aiglx came

---


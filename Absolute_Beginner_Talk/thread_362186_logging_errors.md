---
title: "logging errors"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by meniscus on 2007-02-15
Does ubuntu log setup/installation failures or incompatiability errors?

---

### Post by tgalati4 on 2007-02-22
Not really.  dmesg will tell you what was detected and what confilcts exist when assigning interrupts.  In /var/log there are several log files created once the operating system is up and running.  In /boot/grub/menu.lst you can remove the 'quiet' setting and see the gory bootup details.  This is useful when setting up Ubuntu on a new machine.  Is there a way to capture this non-quiet bootup output.  I don't know.  Perhaps there is a grub command to do that.  A super cheesy way to do it is to take a digital camera and use the video mode and record the bootup sequence and then play it back to see where things went wrong.

---

### Post by meniscus on 2007-02-26
Does it log incompatability errors when the computer is up and running. I was trying to install dependencies for games back when i had the breeezy version of ubuntu installed and i was gettin errors. Does it log them errors in /var/log/messages?

---


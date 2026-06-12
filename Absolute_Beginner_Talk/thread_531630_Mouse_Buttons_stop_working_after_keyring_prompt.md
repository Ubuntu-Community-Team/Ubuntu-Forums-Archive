---
title: "Mouse Buttons stop working after keyring prompt"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by tepidarium on 2007-08-21
Hi,

Sometimes (not all the time) when i load ubuntu after the keyring prompt, the integrated mouse buttons on my laptop will become unresponsive and my only solution is to shut own the laptop (by holding down the power button) and resetting the computer.  This happens randomly.

I have an IBM Thinkpad t60 with both touchpad and ultranav. This problem only started happening this week.

Any advice will be appreciated.

Thank you.

---

### Post by Dave54 on 2007-08-22
Shutting down your laptop by holding the power button until it immediately powers off doesn't allow the filesystem to unmount, which can be very bad. Next time, use one of these options:

1. hit ctrl+alt+backspace

2. hit ctrl+alt+F2. Login, then use the command "sudo reboot"

3. If all else fails:
Hold LEFT alt, hold Sys Rq (usually the "print screen" key), and tap each following key a few seconds apart:
r,s,e,i,u,b.

As for your mouse problem, I'm not sure, but I felt it important to make sure you weren't accidentally corrupting your filesystem.

---

### Post by tepidarium on 2007-08-22
Well, thanks for telling me about this. I was press ctrl-alt-del - but that's for windows and did nothing ;)  If anyone can help with the mouse button issue, it would be much appreciated.  Thanks.

---


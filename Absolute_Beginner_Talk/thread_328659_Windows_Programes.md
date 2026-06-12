---
title: "Windows Programes"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by slohia on 2006-12-31
I am still downloading ubuntu while making this post.
I have been with windows all this while but the number of times that windows crashes is increasing and I thought it would be a good idea to try out something else.
I would like to know if there is any programme / emulator thru which I can run some of the windows softwares. These are developed on Visual Basic.
Thanks.

---

### Post by opticalfiber on 2006-12-31
The best known W32 programs emulator is Wine. Which are the programs you have to emulate? I ask this just because in linux almost all win progs have an alternative and some are much better!

---

### Post by robenroute on 2006-12-31
Hi slohia,

There are several routes to walk when trying to run Windows programs:
- QEMU
- Wine
- Parallels
- VWware
- and a few more

What you would have to ask yourself is why you would want to run Windows programs. Often, there are very capable equivalents available for Linux/Ubuntu. If it's games you're after, people have mixed experiences with playing Windows games on Linux, but it basically comes down to a very limited proposition.

If you definitely do want to run Windows programs, then you could also consider dual-booting your machine.

If you have more questions, I'm sure there are plenty of people on the forums here to help you.

Good luck!

---

### Post by slohia on 2006-12-31
There are a few custom developed windows programmes I want to run. These have been developed in Visual Basic for Windows. There is also an accounting software called Tally I would like to run. This is basically why I need windows emulator.

---

### Post by robenroute on 2006-12-31
There's a reasonable chance this runs under Wine (but you would need to put the VB run-time dlls in the application directory (or another place Wine can find them). Before starting out with Wine, I would recommend installing the latest (available as a deb package from the Wine web site) and following the Wine tutorial on the same web site.

If things don't work out, you can always try QEMU or VMware Server and install Windows and the software you need to run. That will work "guaranteed".

---


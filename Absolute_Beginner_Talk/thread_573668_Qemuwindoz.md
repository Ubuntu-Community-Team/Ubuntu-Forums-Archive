---
title: "Qemu/windoz"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by GerryH on 2007-10-11
First post here with a stupid question.
I have Qemu loaded and windows working under it, and today for some reason when I click the icon, the terminal starts and then shuts down so windoz doesn't start. 
I have the 64 bit thingy  ver 7.04, but that should not be causing this. The launcher code is:
qemu /home/gerry/Windows.img -cdrom /dev/cdrom and has done well up to now.
Thanks for any advice.
Gerry

---

### Post by Frak on 2007-10-11
You may not have enough RAM allocated to it.

Use -m [ram amount here] flag to allocate.

---


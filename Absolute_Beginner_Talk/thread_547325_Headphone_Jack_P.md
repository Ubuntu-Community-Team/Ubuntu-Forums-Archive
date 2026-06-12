---
title: "Headphone Jack :P"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by Vic! on 2007-09-09
My issue is that before I had no sound. Now i have sound but when i plug in headphones the speakers still emit audio while playing the headphones. i have a toshiba satellite a135 s4656

any help will be much appreciated
V :)

---

### Post by Maverynthia on 2007-09-10
I had this same problem and solved it by adding:
options snd-hda-intel model=3stack

To the end of my /stc/modprobe.d/alsa-base

HOWEVER after the kernel update it no longer makes it work right.. :/

---


---
title: "USB Keyboard problem"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by belovedmonster on 2007-12-28
I was using the  Live CD on a Windows machine but I found that the USB keyboard failed to work on the initial option screen, it was only after the allotted seconds ran out and the Live disk automatically booted into Ubuntu that the keyboard then started to work.

This presents a problem because I was planning on setting up a dual boot with Windows and Ubuntu and now Im worried that the keyboard and mouse which are both USB wont work on the OS Selection screen, leaving them unable to choose OS.

Any advice?

---

### Post by kestrel1 on 2007-12-28
One thing you could try is to enable legacy USB in the BIOS.

---

### Post by belovedmonster on 2007-12-28
How would I do that?

---

### Post by public_void on 2007-12-28
When your computer boots you have to enter into the BIOS menu. Usually its by pressing either F1, F2, F10, ESC or DEL. Hopefully the boot screen may tell you. Once in, you need to find the option for legacy USB support for your keyboard and enable it. It might not be those exact words, but should be something similar.

---

### Post by belovedmonster on 2007-12-28
Thanks I'll give that a try.

---

### Post by belovedmonster on 2007-12-28
That has fixed it it seems :-) Although now when I boot up it stays on the screen showing my computers specs for ages before it then loads up either Windows or the Live disk. :(

---

### Post by rocka on 2007-12-31
FWIW I thought I might reply to the thread in case it might help someone else

I got a Microsoft cordless keyboard and mouse for Christmas and plugged it and all seemed to work fine. Until a few days later when I had to boot into windows for something - and found that the keyboard would not work to select which OS in the boot list.

Searched "absolute beginner" and found this thread, enabled Legacy USB Support in the BIOS, and all is ok.

Thanks guys, and have a happy New Year :)
\\:D/

8-)

---

### Post by kestrel1 on 2007-12-31
> **belovedmonster said:**
> That has fixed it it seems :-) Although now when I boot up it stays on the screen showing my computers specs for ages before it then loads up either Windows or the Live disk. :(
You may have set the quick boot option to disabled by mistake. Go back to the BIOS & check. Glad the legacy thing worked.

---


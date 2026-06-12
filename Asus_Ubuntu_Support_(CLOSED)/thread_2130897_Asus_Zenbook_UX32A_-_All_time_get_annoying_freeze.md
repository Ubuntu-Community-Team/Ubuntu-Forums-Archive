---
title: "Asus Zenbook UX32A - All time get annoying freeze"
date: 2013-03-30
forum: Asus Ubuntu Support (CLOSED)
---

### Post by stonedmind on 2013-03-30
Hello all.


I have a big trouble with Ubuntu 12.04.2 and 12.10.
After boot all works fine. But an uncertain time, my computer freezes. Only hard power off work.
I tried different kernels - have the same problem.
Memtest86+ says: no errors on RAM.


Maybe you, guys, have some idea how to fix it or why this happens?
Maybe someone have same laptop. If yes, please answer: your system get freeze like my?


Thanks!

---

### Post by LudoTW on 2013-04-25
Hello,

I have exactly the same problem, with 12.04. I have noticed it freezes when I watch a youtube video, or on facebook. It may happen under other circumstances but I haven't noticed it. Same, hard reset is the only way.
If any one else has the same problem, please chime in! But it doesn't seem so, or the problem would have been much more reported.

It is more than annoying... 

What can be happening? 
Is it our notebook which has a problem?

Thanks a lot for any help.

Ludo

---

### Post by LudoTW on 2013-05-14
No one else is getting these freezes?

---

### Post by homerobono on 2013-05-23
When these freezes occurs there are messages of I/O errors on tty. When I restart my computer I get "Read error" and the system doesn't boot. Although my HD is new.

---

### Post by chyno on 2013-05-27
The same problem here... except my model is UX32VD...
I don't know, is there anything to report?

I'm getting these freezes like once a day.

---

### Post by AlmaTlust on 2013-06-11
Just a guess - do you have a nvidia card and use the nouveau driver? Because my problem went away when I installed the proprietary one...
I also had to put pci=noacpi for it to boot, but that's another story...
My guess is that Asus use some non-standard acpi procedure that the nouveau driver doesn't know about...

---

### Post by akraievoy on 2013-06-26
Yup. Observing the same with UX21A. Sometimes this correlates with activity on GPU like switching to another window which has a heavy repaint to do. Sometimes system goes stuck after a night of mostly idle state (like seeding couple of torrents). Strongly correlates with CPU activity. I guess there's overheating problem with an extra bit added via graphics driver and probably a somewhat stale kernel.
Please see this for more details on kernel (unable/not willing to find particular fix or commit which pinpoints the problem):
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1047294](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1047294)

---


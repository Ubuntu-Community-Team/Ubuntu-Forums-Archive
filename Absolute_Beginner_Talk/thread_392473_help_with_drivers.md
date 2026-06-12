---
title: "help with drivers"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by jandaba on 2007-03-24
i recently installed ubuntu, and at the moment i'm an absolute beginner. i plan to read up on the topic in the near future but until then, i need your help :) 

drivers. where do you find them? i have a dell inspiron e1505. and a driver for the graphics card (mobility radeon x1300) is obviously needed as the resolution is low and scrolling is kinda screwed up and you know the usual stuff. however on the dell website under OS menu for drivers there are things like enterprise linux 3 & 4, suse ES 9 & 10, and linux 8 & 9; on ati's website there's only linux x86 and x86_64.... now i'm really new to all this, so can anyone explain, does ubuntu fall under any of these? or if it doesn't, where the hell do i get drivers? 

and one more thing.... i have intel pro wireless 3945ABG and if i don't disable it through bios, ubuntu wont start..... any way around this?



cheers

---

### Post by igknighted on 2007-03-24
> **jandaba said:**
> i recently installed ubuntu, and at the moment i'm an absolute beginner. i plan to read up on the topic in the near future but until then, i need your help :) 

drivers. where do you find them? i have a dell inspiron e1505. and a driver for the graphics card is obviously needed as the resolution is low and scrolling is kinda screwed up and you know the usual stuff. however on the dell website under OS menu for drivers there are things like enterprise linux 3 & 4, suse ES 9 & 10, and linux 8 & 9; on ati's website there's only linux x86 and x86_64.... now i'm really new to all this, so can anyone explain, does ubuntu fall under any of these? or if it doesn't, where the hell do i get drivers? 

and one more thing.... i have intel pro wireless 3945ABG and if i don't disable it through bios, ubuntu wont start..... any way around this?



cheers

Most things (like your mobo) don't need drivers.  Specific drivers for all this hardware are compiled into the kernel (the core of the OS).  Video cards are another story.  Don't try to install the drivers from ATI, except as an absolute last resort.  Not that they are bad, but downloading programs/drivers from websites to install is old fashioned and dangerous (not that ati will give you malware, but in general it is an unsafe practice).  Ubuntu gives you all the software/drivers you could need in a safe package repository.  You can access this by opening the synaptic package manager (System->Admin->Synaptic).  Here you want to search for "fglrx", then install the package "xorg-drivers-fglrx" (or something along those lines).  If it needs to install dependencies do that.  Also, install the package fglrx-control (again, im 99% sure thats the name).  Then click apply and let it install.  Now you need to open a terminal window (Applications->Accessories->Terminal) and type the following command:
```
sudo aticonfig --initial
```
Now you need to restart your computer, and on reboot the graphics drivers should work fine.

EDIT: as for your wireless, that is really odd.  Intel wireless almost always "just works" in Ubuntu.  Perhaps there is a boot option you can pass to the kernel so you don't have to disable it... someone else might know better than me here.

---

### Post by jandaba on 2007-03-24
yep that hit the spot :) thanks

---


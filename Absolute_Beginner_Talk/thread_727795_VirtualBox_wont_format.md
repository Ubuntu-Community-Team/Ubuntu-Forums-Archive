---
title: "VirtualBox wont format"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by Marko Tica on 2008-03-18
Hi all,

I've installed 7.10 Gusty Ubuntu, which works smooth like always.
I've installed VirtualBox OSE and tried to install Windows XP SP2 on it...but installa tion won't go pass "...setup is formating selected partition..." bar. 
I gave it 265 bas and 64 video memory, enabled IO APIC just and everything else just like I did on my PC at home (there is works just fine) but this version on my laptop won't format .vdi drive...anyone has a clue why?

Thanks in advance.

---

### Post by billgoldberg on 2008-03-18
I use the normal version of virtualbox (not the ose) and it installed xp sp2 without any problems.

It's not in the repository you can download it from their site.

I believe there is a .deb installer for ubuntu gutsy.

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewFilteredProducts-SingleVariationTypeFilter;pgid=01RgaHqkAdxSR0EUQncsoQ3D0000vCooqXTh;sid=R2VJEL98KylJE_ijhRwBFVDZH0AtsHI5EoeG0aJifuwk5w==](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewFilteredProducts-SingleVariationTypeFilter;pgid=01RgaHqkAdxSR0EUQncsoQ3D0000vCooqXTh;sid=R2VJEL98KylJE_ijhRwBFVDZH0AtsHI5EoeG0aJifuwk5w==)

The differences between the normal and ose version can be read here:

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

---

### Post by gobbles414 on 2008-03-18
> **Marko Tica said:**
> Hi all,

I've installed 7.10 Gusty Ubuntu, which works smooth like always.
I've installed VirtualBox OSE and tried to install Windows XP SP2 on it...but installa tion won't go pass "...setup is formating selected partition..." bar. 
I gave it 265 bas and 64 video memory, enabled IO APIC just and everything else just like I did on my PC at home (there is works just fine) but this version on my laptop won't format .vdi drive...anyone has a clue why?

Thanks in advance.

Two questions... First, is the disk image for your XP installation expanding or static? Static is best, IMHO. Second, what's BAS? Does this help?

---

### Post by Marko Tica on 2008-03-18
> **gobbles414 said:**
> Two questions... First, is the disk image for your XP installation expanding or static? Static is best, IMHO. Second, what's BAS? Does this help?

BAS was typo...I meant 256 base as in base memory.

@ billgoldberg...
tnx I'll try that one too.

---

### Post by gobbles414 on 2008-03-18
> **Marko Tica said:**
> BAS was typo...I meant 256 base as in base memory.

@ billgoldberg...
tnx I'll try that one too.

Thanks. **Are you using an expanding or static disk image?** Expanding disk images have given me problems similar to yours in the past.

---

### Post by Marko Tica on 2008-03-18
> **gobbles414 said:**
> Thanks. **Are you using an expanding or static disk image?** Expanding disk images have given me problems similar to yours in the past.

I tried to use static image, and I still had the same problem.

---

### Post by gobbles414 on 2008-03-18
> **Marko Tica said:**
> I tried to use static image, and I still had the same problem.

Disable IO APIC and try again.

---

### Post by Marko Tica on 2008-03-19
I managed to get it to work.
First I reinstalled VirtualBox completely, restarted laptop, installed OSE again, that I've created .ISO with windows CD (at one point I suspected that Windows disk is wrecked), I created new machine, with fixed image disk and no IO APIC, I enabled CD ROM (but .ISO mode where I've mounted windows .ISO), I started install and it crashed several times, but I managed to save much time with frequent screenshots. Now everything is working smoothly.

Thank you all for your time and support.
Cheers

---


---
title: "upgrading macbook3,1 to ubuntu 8.10"
date: 2008-09-09
forum: Apple Hardware Users
---

### Post by rifak on 2008-09-09
i am wondering about the stability of the upcoming 8.10 release. i have everything working just the way i like it here on my macbook now with 8.04, and am wondering if when i upgrade in october, what i will have to do. will i have to fix the wireless, screen, sound, and everything like i did with 8.04? thanks everyone for the help.

---

### Post by kosumi68 on 2008-09-09
If stability is an issue, and nothing is missing from the current installation, then the solution is simply: do not upgrade. There are unix systems out there running code from the sixties. You will not be left out in the cold just because you do not upgrade - Hardy Heron LTS is a Long Term Support release, and as such will work well with other systems for a long time to come.

---

### Post by mabovo on 2008-09-09
There is nothing to do with 8.10 on MacBooks cause it doesn't apply at all.
I tried before and get a lot of system errors and hardware problems with disruption on Intel video configuration, wireless unsupported, keyboard malfunctioning, unrecogneable touchpad functions, external monitor unuseable, and mainly the isight internal webcam a known issue besides poorly sound environment.

---

### Post by Kooothor on 2008-09-09
Yeah, I won't upgrade either...

---

### Post by rifak on 2008-09-09
well thanks everyone. looks like im going to hold back on the upgrade. just out of curiosity, what are the actual benefits of doing the upgrade? i read all about the new default desktop themes, more wireless compatibility, and things like that, but if there are any other big benefits, id like to hear about them.

---

### Post by cyberdork33 on 2008-09-09
> **mabovo said:**
> There is nothing to do with 8.10 on MacBooks cause it doesn't apply at all.
I tried before and get a lot of system errors and hardware problems with disruption on Intel video configuration, wireless unsupported, keyboard malfunctioning, unrecogneable touchpad functions, external monitor unuseable, and mainly the isight internal webcam a known issue besides poorly sound environment.
When was that? The current alpha is running quite well.

Having Linux 2.6.27 is probably the biggest advantage of Intrepid. Many of the fixes for Mac hardware that have been spawned here have made it into the kernel (Multitouch touchpad drivers, keyboard misconfiguration, etc). If you do not have problems with your current install, then you don't need to upgrade (in fact, "upgrading" almost never works properly, and the best way to get the latest version of Ubuntu is to reinstall completely anyway.) If you are happy with what you have, then stick with it.

---

### Post by mabovo on 2008-09-09
> **cyberdork33 said:**
> When was that? The current alpha is running quite well.

Having Linux 2.6.27 is probably the biggest advantage of Intrepid. Many of the fixes for Mac hardware that have been spawned here have made it into the kernel (Multitouch touchpad drivers, keyboard misconfiguration, etc). If you do not have problems with your current install, then you don't need to upgrade (in fact, "upgrading" almost never works properly, and the best way to get the latest version of Ubuntu is to reinstall completely anyway.) If you are happy with what you have, then stick with it.

I forgot to say with kernel 2.6.26.

Didn't try with 2.6.27 yet on my MacBook2,1

Glad to know some improvements are being done by Canonical.

---

### Post by cyberdork33 on 2008-09-09
> **mabovo said:**
> I forgot to say with kernel 2.6.26.

Didn't try with 2.6.27 yet on my MacBook2,1

Glad to know some improvements are being done by Canonical.

There are still some issues with iSight. It seems that they have stripped the firmware-loading capability out of iSight-Firmware-Tools and it is only used now for extracting the firmware from the OSX driver. You just put the isight.fw file into /lib/firmware and it should load automatically. It is working OK for me now, but there are few people reporting issues.

---

### Post by joonyah on 2008-09-21
I've heard some good things about Ibex Alpha 6, at least for MacBook2,1.  If you're worried how it will work why not try the Live CD.  That way you can get an idea of what works out of the box and what doesn't.

-- jon

---


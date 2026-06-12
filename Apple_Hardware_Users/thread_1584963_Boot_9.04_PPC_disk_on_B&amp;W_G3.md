---
title: "Boot 9.04 PPC disk on B&amp;W G3"
date: 2010-09-29
forum: Apple Hardware Users
---

### Post by kikizing3 on 2010-09-29
I've got a (New World) Blue and White Powermac G3. I'm trying to boot into the live CD of 9.04, since 0S9 crashes while starting up. 
I've tried holding C, that other key combo, and OpenFirmware, but no avail. 
When I try it in OF, I type "boot cd:,\install\yaboot", but upon pressing enter, it tells me "bad READ-1 can't open cd:,\install\yaboot".
What am I supposed to do? Anyone else have this problem.

---

### Post by linuxopjemac on 2010-09-30
Boot:
[http://mac.linux.be/content/booting-open-firmware](http://mac.linux.be/content/booting-open-firmware)

Your specific Mac has a problem:
[http://mac.linux.be/content/installation-karmic-koala-when-hard-disk-not-recognised-g3-bw-0](http://mac.linux.be/content/installation-karmic-koala-when-hard-disk-not-recognised-g3-bw-0)

---

### Post by kikizing3 on 2010-09-30
Thanks for the reply. As I said before, I can't get it to boot from CD, so the second link is kinda useless. :(
The first link, though, is telling me I could boot from USB? I'll try that.

---

### Post by linuxopjemac on 2010-09-30
You will need both links.

---

### Post by kikizing3 on 2010-09-30
Yeah, eventually, but I have to solve my current problem first.

---

### Post by lookathing on 2010-09-30
so it just continues to boot if you hold the c key? could it be a bad cd burn?

---

### Post by kikizing3 on 2010-09-30
Yeah. I've burned multiple CDs and am convinced that's not the issue.

---

### Post by gordo on 2010-10-01
> **kikizing3 said:**
> I've got a (New World) Blue and White Powermac G3. I'm trying to boot into the live CD of 9.04, since 0S9 crashes while starting up. 
I've tried holding C, that other key combo, and OpenFirmware, but no avail. 
When I try it in OF, I type "boot cd:,\install\yaboot", but upon pressing enter, it tells me "bad READ-1 can't open cd:,\install\yaboot".
What am I supposed to do? Anyone else have this problem.

Just to be sure : you have the Intel or the PowerPC version of Ubuntu on your CD? The PowerPC version is unsupported and cannot be downloaded directly from the Ubuntu homepage.

---

### Post by kikizing3 on 2010-10-01
> **gordo said:**
> Just to be sure : you have the Intel or the PowerPC version of Ubuntu on your CD? The PowerPC version is unsupported and cannot be downloaded directly from the Ubuntu homepage.

Yeah, I have powerpc. I'm gonna try booting from USB, I'll let you guys know how it works out.

---

### Post by kikizing3 on 2010-10-01
Yeah, it's not working so far. Every time I try to boot from the flash drive I get "method <open> not found; ihandle=ff9d1dc0" some other stuff, and "can't OPEN".

Hmph. Kinda lost at this point. Redownloading the .iso in case something went wrong while downloading last time.

---

### Post by linuxopjemac on 2010-10-02
did you "burn" the usb with the 

dd if=/dev/dadada.iso of=/dev/yourUSB

command? It's all explained on the link I gave you.

---


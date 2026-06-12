---
title: "Restricted driber enabled but not in use?"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Evil Wayz on 2007-11-04
WTF? I have set the monitor type and have all the resolution modes I should. BUT apparently while the driver for my ATI is enabled, it's not being used! damn you stupid aticonfig!

---

### Post by bgast1 on 2007-11-04
I think that I have the same problem. I have what used to be one of the fastest video cards around. It sure doesn't seem to be working correctly. I have an ATI Radeon X1950 Pro.

---

### Post by Evil Wayz on 2007-11-04
don't have anything that fancy, just trying to get my stupid second monitor to work and its wreaking havoc on my system. Right now it's black. I just want 3d accel enabled, is that so wrong????

---

### Post by elctb on 2007-11-05
It took me forever to get the X1950 radeon card to work. The problem turned out to be I was using the kernel modules from ATI which don't work. Once I used ubuntu's kernel modules and ATI's fglrx xorg driver everything worked. I did this about a year ago, so things might have changed. Try it again without installing ATI's fglrx-kernel* packages and using ubuntu's kernel driver's instead. I can dig out some notes I kept, if you need instructions.

---

### Post by Evil Wayz on 2007-11-05
> **elctb said:**
> It took me forever to get the X1950 radeon card to work. The problem turned out to be I was using the kernel modules from ATI which don't work. Once I used ubuntu's kernel modules and ATI's fglrx xorg driver everything worked. I did this about a year ago, so things might have changed. Try it again without installing ATI's fglrx-kernel* packages and using ubuntu's kernel driver's instead. I can dig out some notes I kept, if you need instructions.

I ended up installing ati catalyst for linux, and it worked. And then i tried to use big desktop, it forze, and now it won;t admit there is another connected monitor, plus my screen saver and compiz don't work.

Oh well.

---


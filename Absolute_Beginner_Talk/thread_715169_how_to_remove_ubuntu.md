---
title: "how to remove ubuntu"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by moondoggy17 on 2008-03-04
ok since i cant get ubuntu to work i want to remove it from my laptop and remove grub menu loader so that vista starts up on its own.

so how would i go about doing this

---

### Post by Cypher on 2008-03-04
POp in the Vista CD and have it repair itself. That will get rid of GRUB, and in Vista just delete the Ubuntu partition..

---

### Post by kellemes on 2008-03-04
> **moondoggy17 said:**
> ok since i cant get ubuntu to work i want to remove it from my laptop and remove grub menu loader so that vista starts up on its own.

so how would i go about doing this

Don't know about Vista but in XP you can use the Windows-installcd to enter the recoveryconsole and type "fixmbr" to restore the Windows-bootloader. I can imagine this option will be available with Vista too.

---

### Post by lswest on 2008-03-04
it is, but it's not "fixmbr" it's "bootrec /fixmbr" in vista

---


---
title: "Edgy not recognizing boot parameters"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by velozoom on 2006-10-30
I have an ADM64 system and need to add 'noapic noalpic' to the optional boot paramaters.  

editing /boot/grub/menu.lst worked for Dapper but it's not for Edgy.   In the Edgy version it says that the defoptions line is only used for the default boot version and no others.  Well, even after adding noapic and nolapic to the defoptions they do not appear when doing a standard boot.  I will have to manually add them every time I reboot.  

'Sup with this?  

FYI- I'm a serious noob so the simpler the answer the better!  ;)

---

### Post by Roobert on 2006-11-01
Actually, I'm having the exact same problem with a fresh install of Dapper. Noapic is being ignored in /boot/grub/menu.lst. I'm having to manually edit the boot parameters at every reboot just to avoid an APIC-induced kernel panic.

---


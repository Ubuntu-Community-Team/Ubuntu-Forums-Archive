---
title: "Windows 7 Boot Options"
date: 2012-08-30
forum: Any Other OS
---

### Post by JaySeeJC on 2012-08-30
I was wondering if it was possible to pass boot options to windows 7 via GRUB. I am especially interested in the noguiboot option. Is there any way to do this, or is it a wild goose chase?

---

### Post by oldfred on 2012-08-31
Moved to OtherOS.

Do not know about Windows boot options, how do you add them in Windows?

All grub does is jump to the PBR - partition boot sector. That is all the Windows boot loader in the MBR does, jump to the PBR. 

So grub is before Windows starts to boot and generally you do not add options in the MBR when booting Windows, it has to be later in boot process.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by JaySeeJC on 2012-08-31
> **oldfred said:**
> Moved to OtherOS.

Do not know about Windows boot options, how do you add them in Windows?

All grub does is jump to the PBR - partition boot sector. That is all the Windows boot loader in the MBR does, jump to the PBR. 

So grub is before Windows starts to boot and generally you do not add options in the MBR when booting Windows, it has to be later in boot process.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Windows does it through msconfig, but once GRUB is installed it's impossible to change the boot options. Considering I didn't change any of said options before I installed ubuntu, I have no way of knowing if said options would have survived the grub install

---

### Post by oldfred on 2012-08-31
Why cannot you run msconfig? That is in Windows and has nothing to do with grub.

Some say getting f8 to work from grub is tricky as grub is too fast compared to MBR boot. They say to hit f8 almost as you hit enter on the grub menu and may have to try several times.

---


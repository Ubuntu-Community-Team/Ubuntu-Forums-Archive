---
title: "Quick kernel question"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by energiya on 2007-01-20
If I compile a kernel using the "sudo cp /boot/config-`uname -r` .config" command or unaltered config (no changes to the config), shouldn't it run out of the box? ... or at least run? :confused:

---

### Post by kinematic on 2007-01-20
if you use the original config that comes with ubuntu it should run out of the box.
the default is a config to include drivers for the widest range of hardware.
but if you're going to compile your own kernel you can strip it down to include only drivers for hardware that you actually have wich will give you a much leaner and cleaner kernel.....that's what i always do.

---

### Post by energiya on 2007-01-20
That is what I did, but only managed to get a black screen and 30 sec of hdd read. So I thoght it would be wise to strip only a few thinks at a time, to be sure it's not my mistake... and when tried to copile using the config that I allready used from my stock kernel, the same happaned: black screen and some hdd reading.

---

### Post by zgornel on 2007-01-20
> **energiya said:**
> If I compile a kernel using the "sudo cp /boot/config-`uname -r` .config" command or unaltered config (no changes to the config), shouldn't it run out of the box? ... or at least run? :confused:

It should run out of the box for a kernel compiled from the ubuntu kernel sources.

---

### Post by energiya on 2007-01-20
I used sources downloaded via aptitude and from kernel.org, different kernel versions (2.6.17-10 from repos, 2.6.19 and 2.6.19-2 from kernel.org). All gave me the same black screen.

---

### Post by energiya on 2007-01-20
ok... managed to get the kernel working... I had to remove nvidia driver and all modules.
I still have a black screen and no <Alt>+<Ctrl>+Fx terminal... :( **help please!!!** GDM works, but I NEED the console. Does anyone know what must I select when configuring the kernel (2.6.19-2)?

I have 
- VGA (M) and VESA VGA (Y)
- Video mode selection support (Y)
- MDA text console (M)
- Framebuffer Console suport (Y)
- Logo Configuration (Y)

---


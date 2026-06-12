---
title: "i just got a couple of questions i'm a linux noob~ &gt;.&lt; please help!"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by bigb0i on 2007-12-11
how many stages are in a Linux loading process and which boot loader should i use?thanks guys

---

### Post by Pumalite on 2007-12-11
Grub

---

### Post by jflaker on 2007-12-11
I took the default which installed the Grub loader and had no issues.....even when I was dual booting Vista.

---

### Post by PeterJS on 2007-12-11
Grub has 3 stages, intuitively named 1, 1.5, and 2, and then the Linux boot process can be divided up in to 3 stages.

The first stage of grub is embedded in the MBR itself, and it's job is to load stage 1.5. Stage 1.5 is where the real work starts, 1.5 is smart enough to read multiple file systems and can dynamically find stage 2. Stage 2 is what is the menu you actually see when grub loads up.

Then linux boot process starts with loading the kernel, boot splash, and other modules, in to RAM. Once everything is loaded the init process starts and begins loading system services and programs. Once that is done X starts up and off you go.

Grub is the way to go for boot loaders. Lilo is older and should only be used as a last resort if you need to do something really funky.

---


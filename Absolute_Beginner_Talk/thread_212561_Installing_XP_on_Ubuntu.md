---
title: "Installing XP on Ubuntu"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by skivan on 2006-07-10
Hi!

I am running ubuntu but now I need windows xp too since i have to make some flash movies.

All guides on how to make dualboot starts with installing windows xp then ubuntu, but how do i install windows xp after i have insalled ubuntu??

thanks,

Magnus

---

### Post by dmizer on 2006-07-10
your best bet in this case is probably going to be through using some sort of virtual machine like vmware.  there's some good tutorials out there for it.

the problem is, xp doesn't have the ability to live with other operating systems.  it will overwrite your master boot record.  it also wants to live at the very beginning of your hdd.

there are ways to overcome these problems, but i think you'll be much happier with a virtual machine instead.  that way you won't have to reboot to go work with your flash.

---

### Post by qrm on 2006-07-10
try this [http://www.ubuntuforums.org/showthread.php?t=187413](http://www.ubuntuforums.org/showthread.php?t=187413)

---

### Post by skivan on 2006-07-10
I have tried that, but my laptop is to slow. I haveto wait for like 2 seconds every mouseclick... :)

---

### Post by bigken on 2006-07-10
did you install vmware tools

---

### Post by Crosbie on 2006-07-10
I have XP running in an out-of-the-way partition fine.  It will bork your MBR but you should be able to reinstall Grub using the liveCD... right?

---

### Post by dmizer on 2006-07-10
> **skivan said:**
> I have tried that, but my laptop is to slow. I haveto wait for like 2 seconds every mouseclick... :)
what kind of machine are you running?  i had vmware with qemu kqemu as described in the link qrm gave you, and though it did run a touch slower than it would have if i booted directly to it, it wasn't unusably slower unless the kquemu accelerator didn't load (then it was impossibly slow).

my machine is a 850mhz pIII machine with 256meg of ram.

---

### Post by skivan on 2006-07-10
I dont remember all the specs right now, but something like P4, 512 Mb RAM.

I installed qemu but not vmware. Do I have to do that? What does vmware do?
What is KQEMU?

---

### Post by dmizer on 2006-07-10
qemu is a virtual machine which by itself is terribly slow.  kqemu is a cpu emulator which significantly increases the speed of qemu. vmware is another virtual machine, which seems to be more stable and a bit faster than qemu by itself.

---

### Post by dmizer on 2006-07-10
if you already have qemu installed, you should remove it and start from scratch.

for kqemu to work as an accelerator, you'll have to compile qemu and kqemu together.  just look at the link that qrm gave you.  there's a script in that link that will do everything for you.

---

### Post by bigken on 2006-07-10
I use vmware with win xp pro and vista with vmware tools and its very nippy give it a try before you install win xp as a stand alone os ;)

---


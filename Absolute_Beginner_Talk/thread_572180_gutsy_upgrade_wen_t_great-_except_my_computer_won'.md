---
title: "gutsy upgrade wen t great- except my computer won't turn off"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by Protagonistics on 2007-10-10
So when I turn off my compy Ubuntu shuts down and it's all fabulous until right at the point when it should just turn off-- it doesn't. I have to manually turn it off. there is text on the screen (no gui, as I said, this is deep in shut off stages) which states that a couple of parts of the computer are shut down namely eth0 and eth1.

Why is it doing this? How can I get it to POWER off automatically? is anyone else having the same issue?

---

### Post by alienexplorers on 2007-10-10
My computer suffers from the same problem in Gutsy.  Don't know why it will not turn off.  Has something to do with APCI I believe.

---

### Post by skymera on 2007-10-10
my one shuts down in Gutsy.

but i have to use command line :(

are eth0 and eth1 used? if not hash them out

sudo gedit /etc/network/interfaces

---

### Post by philinux on 2007-10-10
try editing grub kernal entry and at the and append acpi=force

---

### Post by alienexplorers on 2007-10-10
Mine uses eth0.  The program when booting says something about ACPI being off even though I know in BIOS that it is on.

---

### Post by Protagonistics on 2007-10-10
philinux said: 
try editing grub kernal entry and at the and append acpi=force

how does one access the grub kernel?

---

### Post by alienexplorers on 2007-10-10
Type in a terminal:
> gksudo gedit /boot/grub/menu.lst
Edit that file and save the changes.

P.S. - I made the changes and now have an error showing up about not being able to access my /home directory due to the wrong chmod code of 644 was missing.  Did not even touch anything in the /home folder.  Now what happened.

---

### Post by Duck2006 on 2007-10-10
> **Protagonistics said:**
> philinux said: 
try editing grub kernal entry and at the and append acpi=force

how does one access the grub kernel?

In the terminal type

gksudo gedit /boot/grub/menu.lst

---

### Post by philinux on 2007-10-10
Mine looks like this 

```
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=25b61946-bda3-4a9c-8627-b7030986be78 ro quiet splash acpi=force
```

never had a problem :confused:

Sorry to here about your error alien.

---

### Post by Protagonistics on 2007-10-10
SIlly computers with there personalities- mine fixed itself today. It always does that, no matter what the problem is....

EDIT: Turns out today was just a fluke. It even does it when when I restart. And has anyone else had the problem of the GUI not firing up on startup? that scared the pants off me yesterday. I'm still not clear on what the solution is, based off these posts. there seems to be some disagreement

---


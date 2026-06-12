---
title: "Unknown Interrup or fault"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by raytux on 2007-04-15
Tried to check install disc or run install, and get Unknown Interrup or fault at EIP 00000060 c01002b1000002b0. What does this mean? Do I need to remake an install disc?

Udate
Ran install, and got Unknown Interrup or fault at EIP 00000060 c01002b1000002b0. What does this mean? Managed to get Live cd to run and os to load by pressing F6 and entering "acpi=off". Now I can't get Ubuntu to run at all  off the hard drive with the same fault message. Computer is Compaq Persario Sr1210nx, run Ubuntu 6.10

---

### Post by dstew on 2007-04-16
You can add the same "acpi=off" to the kernel line right before you boot from the Grub menu. When the Grub menu appears, press 'e' to enter edit mode. Then, select the kernel line, add the statement to the end, press enter, then enter 'b' to boot. If this works, you can add the acpi=off option to the kernel line permanently by editing the grub menu file. Open a terminal window (Applications --> Accessories --> Terminal) and at the prompt enter:

sudo nano /boot/grub/menu.lst

Page down until you find the kernel line, add the statement, save the file and reboot.

---


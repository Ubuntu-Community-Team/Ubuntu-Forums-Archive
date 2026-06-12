---
title: "Boot natty on MBP 3,1"
date: 2011-06-29
forum: Apple Hardware Users
---

### Post by lambengolmor on 2011-06-29
I couldn't find info about my problem anywhere, so I hope someone can point me in the right direction.

Situation:
I have a Macbook Pro 3,1 (mid 2007) with OSX/Ubuntu 10.04 64bit (under bios emulation). I want to format Ubuntu partitions and install Natty 64bit. So, following instructions, I insert the cd in the drive and reboot; rEFIt presents me 3 cd options (grub efi 64, linux from cd, legacy os from cd). The first, as expected, boots grub, boots ubuntu but the nvidia graphic card doesn't work (assume it boots since I can hear it work and when i press the power button it shut down clean ejecting the cd). So i went to the second and third options (that behave the same).

My problem:
When I try to boot "linux from cd" or "legacy os from cd" it presents me a black screen asking which mode i want to use (1 or 2). I assume this is for choosing bios/efi mode on non-rEFIt hardware. Anyway the problem is that keyboard doesn't seem to work (pressing any key doesn't have any effect), I don't even know if system freezes or if it's just the keyboard itself (I have an Italian layout, but numbers have the same position than the US one). I don't have an external keyboard, I tried with an usb numpad but without success.

I hope anyone has some ideas about it,
thanks for any answer

---

### Post by lambengolmor on 2011-06-29
**WORKAROUND:**
I managed to boot&install. I downloaded the official iso, deleted the EFI folder, burned and it booted without other problems. It's not a real solution, but works.

---


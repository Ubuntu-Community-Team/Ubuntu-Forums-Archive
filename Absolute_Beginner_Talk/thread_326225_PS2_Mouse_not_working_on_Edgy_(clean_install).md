---
title: "PS/2 Mouse not working on Edgy (clean install)"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by mirobe on 2006-12-27
Hi,

My mouse doesn't wotk on edgy (clean install).
It doesn't work in both liveCD & installed OS.

From dmesg:

[171...] mice: PS/2 mouse device common for all mice


In /etc/X11/xorg.conf:

Section "InputDevice"
Identifier "configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAsixMapping" "4 5" 
Option "Emulate3Buttons" "true"
EndSection


Tried with ImPS/2, Protocol Auto.. no change.

USB mouse attached works without any problems. The problem is that it's not mine :/

Mouse model:
Logitch optical (M-SBF69)
E-C011-03-0155(B)
(don't know what it means..)

Please help,


Robert

---

### Post by M8M on 2006-12-28
Did you ever figure out a solution to this problem? I have the same problem on the Edubuntu that I just installed on my other computer. If I could figure out how to get to applications without using the mouse, I might be able to access the terminal and try xorg.conf, but I can't figure out how to acess the applications without my mouse. Any ideas?

M8M

---

### Post by M8M on 2006-12-28
My brilliant husband has just figured it out.
Connect the mouse cord to a PS/2 mouse port instead of a 9-pin serial port.
God Bless

---

### Post by deadgobby on 2006-12-28
Sounds like a K.I.S.S. method there. "Keep it simple stupid". I have been there and making sure it is plugged in. Like my cable modem for sample.
Gobby

---

### Post by mirobe on 2006-12-28
I think it is a kernel bug related problem.
Nothing to do with xorg.conf file.

There have been some problems with psmouse kernel  module
starting from 2.6.15 afair, and I don't see this fixed.

Some patches for that around, but I don't want patching, I want a usable
system, and honestly Ps/2 mouse not working makes me really mad :-(

Thanks for your responses,

Happy New Year!

Robert

---

### Post by bodzasfanta on 2007-01-04
Hello!

I had a similar problem but thanks God someone told me a good way to fix it.

"In grub, hit e to edit the boot line. Then move the selection over the kernel line and hit e again. Move the cursor to the end of the line and add the following:
Code:

noapic irqpoll pci=routeirq

Then hit enter to get our of line editing mode and b to boot the modified kernel line.

This will set you up until you power down or reboot. Edit /boot/grub/menu.list to make it permanent." (thanks for Frem)

I hope I could help you

---

### Post by stroopwafel on 2007-01-04
> **bodzasfanta said:**
> Hello!

I had a similar problem but thanks God someone told me a good way to fix it.

"In grub, hit e to edit the boot line. Then move the selection over the kernel line and hit e again. Move the cursor to the end of the line and add the following:
Code:

noapic irqpoll pci=routeirq

Then hit enter to get our of line editing mode and b to boot the modified kernel line.

This will set you up until you power down or reboot. Edit /boot/grub/menu.list to make it permanent." (thanks for Frem)

I hope I could help you

I'm having trouble with my ps/2 mouse too. What does this mean:> In grub, hit e to edit the boot line.  How do I get there?

---

### Post by stroopwafel on 2007-01-04
> **stroopwafel said:**
> I'm having trouble with my ps/2 mouse too. What does this mean: How do I get there?

I found it. sorry for asking before trying the obvious.

---


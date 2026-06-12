---
title: "laptop shutdown troubles"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by nowald on 2008-01-27
Hi . I have troubles using Ubuntu 7.10 on my laptop (Packard Bell MV85-101). 

I can't shoutdown my system without press the power off buttom from the laptop. I tried changing /boot/grub/menu.lst:

First time:
> Adding acpi=force

Second:
> edit /etc/modules and adding apm, also edit /boot/grub/menu.lst, adding apm=power-off

Last time:
> adding acpi=on

Any of that changes works and I've no idea how to do know.... Can you help ?

PS.: sorry about my poor english. Im from Spain.

---

### Post by Kilz on 2008-01-27
> **nowald said:**
> Hi . I have troubles using Ubuntu 7.10 on my laptop (Packard Bell MV85-101). 

I can't shoutdown my system without press the power off buttom from the laptop. I tried changing /boot/grub/menu.lst:

First time:
> Adding acpi=force

Second:
> edit /etc/modules and adding apm, also edit /boot/grub/menu.lst, adding apm=power-off

Last time:
> adding acpi=on

Any of that changes works and I've no idea how to do know.... Can you help ?

PS.: sorry about my poor english. Im from Spain.

Do you have to hold the button down, or is it that you have to use the button?

---

### Post by nowald on 2008-01-27
I can read:  Power off   ; but if I dont press the button, my laptop still running (I had been trying to wait about 1 or 2 minutes, without pressing power off button, but my hardware still running, so finally, I have to press it, if I want to turn off my computer)

Thanks for your answer.

---

### Post by nowald on 2008-01-27
Here is another try:

- Edit /etc/modules and adding:

apm power_off=1

- Next, I edit /boot/grub/menu.lst and add:

ro quiet splash acpi=off apm=on apm=power-off noapic


But didnt work :(

---


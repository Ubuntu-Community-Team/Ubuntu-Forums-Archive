---
title: "Laptop Installation"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by BrendanT on 2008-01-13
Greetings,
Being a WINDOWS whinger from way back I decided to try LINUX on my old ACER TRAVELMATE 521TXV,
its a P3 600 with 192mb RAM
I downloadedl XUBUNTU since it says its less demanding on the hardware than UBUNTU but I cant make it work.
After choosing the Install option the GUI dissappears and I am left with the term "initramfs" and a flashing cursor. I typed "help" as suggested on the screen but cannot recognise the available commands.
So here I am STUCK, I'd really appreciate some help folks.
Out of interest I also attempted to install UBUNTU, it did exactly the same thing.

Regards
Brendan

---

### Post by dcstar on 2008-01-13
> **BrendanT said:**
> Greetings,
Being a WINDOWS whinger from way back I decided to try LINUX on my old ACER TRAVELMATE 521TXV,
its a P3 600 with 192mb RAM
I downloadedl XUBUNTU since it says its less demanding on the hardware than UBUNTU but I cant make it work.
After choosing the Install option the GUI dissappears and I am left with the term "initramfs" and a flashing cursor. I typed "help" as suggested on the screen but cannot recognise the available commands.
So here I am STUCK, I'd really appreciate some help folks.
Out of interest I also attempted to install UBUNTU, it did exactly the same thing.

Regards
Brendan

Download the "Alternate" install CD, that has a better chance of installing the base system on such low spec hardware.

---

### Post by Pogeymanz on 2008-01-13
Yup. That's your problem. I couldn't use the LiveCD install on my old PIII with 192MB RAM either. The alternate went fine, though.

---

### Post by BrendanT on 2008-01-13
Thanks for your suggestion.
I downloaded the ALT cd and gave it a whirl but it still failed.
Fortunaley I found a post from december 06 that provided a fix.
A BIG THANK YOU to Stephen Howard...........
I added the following to the boot parameters

irqpoll
acpi=off
noapic
nolapic
pci=noacpi
pci=biosirq 

and YAHOO!

---


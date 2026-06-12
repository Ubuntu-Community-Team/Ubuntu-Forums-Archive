---
title: "Ubuntu on an HP a522n?"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by tll_2k on 2007-06-25
I've been trying to install ubuntu feisty on an hp pavillion a522n. I can't boot the live cd, but i can boot the alternative cd with acpi=off. I was able to install ubuntu, but I can't boot into it. i've tried apci=off, noapic, nolapic, and pci=noacpi. It is a P4, 512 MB ram, Nvidia Geforce 5200 or something. Does anyone have any ideas on how to get it to work? Or any other distros that might work? Or is this computer just a no linux box? 

Thanks in advance!
    Tyler Lane

---

### Post by overdrank on 2007-06-25
> **tll_2k said:**
> I've been trying to install ubuntu feisty on an hp pavillion a522n. I can't boot the live cd, but i can boot the alternative cd with acpi=off. I was able to install ubuntu, but I can't boot into it. i've tried apci=off, noapic, nolapic, and pci=noacpi. It is a P4, 512 MB ram, Nvidia Geforce 5200 or something. Does anyone have any ideas on how to get it to work? Or any other distros that might work? Or is this computer just a no linux box? 

Thanks in advance!
    Tyler Lane

Hi have you tried to reconfigure your xorg through the terminal. After the grub loads use the keys  ctrl,alt,F1 all at the same time. This will bring you to the terminal then you can use the command 
*sudo dpkg-reconfigure xserver-xorg* then answer a few question and if you dont know the answer leave it as the default answer given. Hope this helps good luck!

---

### Post by tll_2k on 2007-06-25
I can't get to a terminal. when I choose what os to run, it starts to load, then comes up with an error like:

EIP: [<c011c706>] native_apic_write_atomic

I think it's different depending on what boot code I try.

---


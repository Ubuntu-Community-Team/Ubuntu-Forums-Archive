---
title: "Intel graphics and nvidia fx5500 guide not working"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by merobertd on 2007-03-15
Hi
I am very new to Linux so you may have to spell it out for me. I have installed ubuntu 6.06 downloaded & installed all the updates from the update manager. My on board Intel graphics and nvidia fx5500 pci graphics card are having trouble with ubuntu. There are many posts about the problem and my symptoms are similar, but when I follow that guides in have found they don’t work

[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

By tseliot 

The problem is when i get to step 4 i dont get this 

Section "Device"
Identifier "NVIDIA Corporation NV34 [GeForce FX 5500]"
Driver "nv"
#BusID "PCI:1:9:0"

Can I just type this in & if so how do I find out what my PCI number is
I can see the card in my device manager when my Bios is set to boot to the integrated one.

Any help would be great Thanks.

---

### Post by Kobalt on 2007-03-15
I think you can get your PCI number with the *lspci* command line. Try to type it in a Terminal and copy/paste the output please.

---

### Post by merobertd on 2007-03-16
the lspci worked but putting the result in didnt. any other suggestions?

---

### Post by Luk0r on 2007-03-16
If you don't mind installing the proprietary (official) Nvidia drivers, you can use envy, which automates the process for you.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by merobertd on 2007-03-28
That didnt work. Thanks for the help but i have gone back to windows traped bill and my poor computer skills.

---


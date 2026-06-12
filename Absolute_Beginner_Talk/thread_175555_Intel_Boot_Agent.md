---
title: "Intel Boot Agent"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by typon on 2006-05-13
I have this problem and i searched around a lot and got no solution.

i installed ubuntu, when half the installation is done, it says "un mounting and ejecting Cd-rom". up to that point, i am good.

but when it restarts the computer, Intel Boot Agent 4.1.17 loads and is looking for DHCP...\

then it says "No bootable file name recieved- insert boot disk.."

i have changed the order of the Boot Agent in the bios, but it still loads up...

can any one PLEASE explain what this problem is and how to solve it...

i really want to install ubuntu...

---

### Post by hw-tph on 2006-05-13
Intel Boot Agent is the network bootloader on your Intel network card (can be a PCI card or built-in on the motherboard). Try disabling it entirely in your BIOS and make sure you try to boot from the installed hard drive.


Håkan

---


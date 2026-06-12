---
title: "Installation problems on IBM desktop"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by Skouboe on 2008-01-19
Hi

I am a new user for Ubuntu, and my experience with Linux so far is little, but I am very interested in trying it out and use it.

My problem is that I have 3 IBM computers that I would like to install with Xubuntu, but the installation seems to crash.

Hardware: Desktop
Maker: IBM
Model: model no. 6275-22, Personal Computer 300 GL, cel 

Known issue: installation starts fine but shortly after the Xubuntu(Ubuntu has the same error) logo apear and the status bar has been shown 2 min. the screen turns black with the cursor in top on the left hand side. 

What can be wrong!

BR Dennis

---

### Post by spiderbatdad on 2008-01-19
maybe some pci issues. you can look at various boot parameters from the grub screen. When grub loads hit f6 to edit the boot line. F1 will show you other options, then f6 from the menu that f1 display will show some examples. For that machine you may need something like this: At the end of the boot line options, that f6 displays, delete everything back to and including "ro,"...so ro  -quite splash... something like that. and add "noapic nolapic vga=771" without the quotes. I am no expert at setting these parameter, nor how to determine what parameters will be successful. I have only done this by trial and error. Once you have found what works, you can edit the kernel line in /boot/grub/menu.lst of your installation.

---

### Post by louieb on 2008-01-19
How much memory do these machines have? If any less than 256MB you will need to use the (IMHO better) text based installer.

---

### Post by dankdave on 2008-01-19
I installed xubuntu on an old pII computer yesterday.  At first, I was trying to install it with only 128 Mb's of memory.  I could get fairly far but each time it failed on me. After throwing in two 256 Mb sticks the install went fine for me.

If you can't get to the desktop with the install icon it might be not enough memory.

---


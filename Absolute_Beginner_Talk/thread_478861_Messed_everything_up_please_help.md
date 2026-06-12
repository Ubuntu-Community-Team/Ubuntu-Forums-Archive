---
title: "Messed everything up please help"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-06-19
what is the command to auto detect hardware, and how to i access a terminal with out the gui.  let me know please

---

### Post by FleetAdmiral74 on 2007-06-19
To access terminal just boot into the ubuntu recovery mode instead of the standard kernel.

---

### Post by rickycodie on 2007-06-19
to see all hardware it's fdisk -l i think

---

### Post by swoll1980 on 2007-06-19
when I instaled ubuntu it automaticly detected and  configured its self for my hardware. is there a command to make it do this over again?

---

### Post by swoll1980 on 2007-06-19
how do i make it boot into recovery mode?

---

### Post by Jimmyfj on 2007-06-19
> **swoll1980 said:**
> what is the command to auto detect hardware, and how to i access a terminal with out the gui.  let me know please

If you broke your GUI:

sudo dpkg-reconfigure xserver-xorg

If you need to reconfigure more try

sudo dpkg-reconfigure -a

---

### Post by swoll1980 on 2007-06-19
how do i get to a terminal

---

### Post by regomodo on 2007-06-19
> **rickycodie said:**
> to see all hardware it's fdisk -l i think

thats just to see your drives and partitions.

$ lspci

is to see everything that linux can see, i believe. won't set it up though

---

### Post by swoll1980 on 2007-06-19
Do you  know how i can get to a terminal

---

### Post by Tomosaur on 2007-06-19
Applications > Accessories > Terminal

If you are unable to do this, just hit ctrl+alt+f1 and you will be given a terminal login prompt. Ctrl+alt+f7 to get back to the GUI.

---


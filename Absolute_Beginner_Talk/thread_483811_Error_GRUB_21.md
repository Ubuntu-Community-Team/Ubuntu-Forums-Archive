---
title: "Error GRUB 21"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by sindbad_x on 2007-06-25
Plz i wanna instyall ubuntu 6.14 or 7.04

and i have hard 160G SATA

before install when i choose GRUB loader found (hdd)

when i let it found the error 

when i change it to (sta) found the error 

when change to (/dev/sta1)  found the erroe

plz i need help

---

### Post by sindbad_x on 2007-06-25
plz any one help me

---

### Post by LaRoza on 2007-06-25
What exactly happened? Your post is not clear. Tell us step-by-step what the problem is.

---

### Post by sindbad_x on 2007-06-25
I have hard 160G sata

when install ubuntu found error GRUB 21

before install ubuntu
i found where ca i install GRUB boot (hdd) ----------- that's dafult

when let it found message after install 

error
GRUB 21

---

### Post by LaRoza on 2007-06-25
Error 21 means the disk does not exist. a sata disk will be sda not sta. Actually, in Feisty every disk is sda.

---

### Post by sindbad_x on 2007-06-25
yep i try with Feisty 

u mean i change (hdd) to   (sda) only

and it will work

---

### Post by LaRoza on 2007-06-25
No, the menu.lst setting should be hdd, but this:

> when i change it to (sta) found the error 

when change to (/dev/sta1) found the erroe

Implies that you manually editted something. I would recommend reinstalling Grub, or reinstalling Feisty.

-edit If nothing is on the hard disk, choose the install option to overwrite the entire disk and install.

---


---
title: "Super Error"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by wandarkaf on 2007-04-21
im new in this.

im installing ubuntu 7.04 for amd64 processor and the install goes ok.

the problem is when the restart after installacion.

the computer start checking hardware and just in the moment when the pc check is there a boot cd appears this
strange error: "error loading operating system" and the comp freeze. 

plz help me

---

### Post by leibowitz on 2007-04-21
Please provide more information like what CD did you used, Desktop or alternate.

What did you do during the installation related to the "Grub installation / Boot menu".

It seems that you have no boot menu at all. So maybe the Grub was not installed correctly or not at all. To fix this, I will need more information about your Hard Drive(s). 

How many hard drive do you have. Of which type. Where are they connected to (Master/Slave)

Lets take one generic example : one IDE Hard drive connected on the primary Master IDE. Imagine this is where the Linux is installed. In that case boot the live-cd and go to the Applications menu > Accessories > terminal. And type this:
```
sudo fdisk -l /dev/hda
```

And paste the output in here.

---


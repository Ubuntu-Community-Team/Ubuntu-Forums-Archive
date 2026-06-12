---
title: "Grub Error 17"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by cumanzor on 2007-04-12
I resized my partition and now I get Grub Error 17, so I can't boot to Ubuntu. I installed Acronis OS Selector so I can boot to windows, but I still get error 17 if I try to boot into Ubuntu.

What can I do? How do I reinstall Grub? I really don't want to reinstall Ubuntu again.

---

### Post by callkalpa on 2007-04-12
If you have the live CD of Ubuntu. Boot the PC from it. Open the terminal.

Then type **sudo grub** 
Then **find /boot/grub/stage**

It will output a similar as **(hd0,1)**
Suppose its **(hdx,y)**

Then
type **root (hdx,y)**
*Here and ahead x,y should be replaced with what you get as the output of the "find" command*

Then type **setup (hdx)**

Accutually this process reinstalls the grub loader and I hope this will help you.

Enjoy Ubuntu .....

---

### Post by cumanzor on 2007-04-12
I booted with the LiveCD (7.04)

sudo grub

then

find /boot/grub/stage

> Error 15 File not Found

---

### Post by DeltaUK on 2007-04-12
i think it was meant to be find /boot/grub/stage**1**


try that

---

### Post by callkalpa on 2007-04-14
I'm Sorry. As DeltaUK has suggested **find /boot/grub/stage** should be replaced with **find /boot/grub/stage1**

---

### Post by jack3 on 2007-04-23
when I type find /boot/grub/stage1

it gives me an error 15 still.

Any clue?

Jack

---


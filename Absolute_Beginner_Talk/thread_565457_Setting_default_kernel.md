---
title: "Setting default kernel"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by savemekaizer on 2007-10-02
I know this is a really quick and easy question, but...
I have 2 incomplete kernels that are installed, due to ignorance and I have no clue how to remove them.
The one I want to boot under is 20-16, the two incomplete ones are versions of 22.
How do I delete or disable them, or how do I make the 20-16 kernel the default a startup?
Anything so I dont have to keep remembering to press ESC at startup. :P

---

### Post by aashay on 2007-10-02
```
sudo gedit /boot/grub/menu.lst
```
Find a line which says "```
default 0
```" and replace it with ```
default		saved
```.
GRUB should boot the last booted kernel on the next boot

---

### Post by SOULRiDER on 2007-10-02
Yopu should try fixing those incomplete kernels.
Try doing:
```
sudo dpkg --configure -a
``` and see whats up. Please post results here :P

---

### Post by savemekaizer on 2007-10-02
> **SOULRiDER said:**
> Yopu should try fixing those incomplete kernels.
Try doing:
```
sudo dpkg --configure -a
``` and see whats up. Please post results here :P
Absolutely nothing comes up.
> gaby@Cuttlefish:~$ sudo dpkg --configure -a
gaby@Cuttlefish:~$ 

As for the other reply- Thank you! <3

---

### Post by DouglasAWh on 2007-11-08
> **aashay said:**
> ```
sudo gedit /boot/grub/menu.lst
```
Find a line which says "```
default 0
```" and replace it with ```
default		saved
```.
GRUB should boot the last booted kernel on the next boot

um, this did not work for me.  Maybe I should just get rid of my realtime kernel, since it doesn't work with my wireless.

---


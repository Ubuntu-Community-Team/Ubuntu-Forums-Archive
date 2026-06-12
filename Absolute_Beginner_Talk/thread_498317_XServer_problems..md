---
title: "XServer problems."
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by fidde88pven on 2007-07-11
Hello.

Ive searched in this forum and google, but not found anything helpful so now I hope you can help me...

On several distrubutions, including Ubuntu Feisty 7.04 and Debian and Fedora Core 7 ive had this problem.
The problem is:

I installed the Ops but at the first startup the Xserver is just weird. I cant see anything clear, there are only 
colored stipes and flashing squares on the screen.


Hope you understand my English and can help me. 

Regards Fredrik Eliasson //Sweden

---

### Post by shearn89 on 2007-07-11
you could try:
```
sudo dpkg-reconfigure xorg-xserver
```
 and see if that helps. It re-runs the video hardware configuration utility from the install. It might work...?

---

### Post by moore.bryan on 2007-07-11
> **shearn89 said:**
> you could try:
```
sudo dpkg-reconfigure xorg-xserver
``` and see if that helps. It re-runs the video hardware configuration utility from the install. It might work...?
*and if you're running an intel chipset, the 915resolution package may solve any dimension problems you might have.*

---

### Post by fidde88pven on 2007-07-11
Thanks for the help, but already tried it... Didn't help... What do you mean with resolution packages...? Thanks again! //Fredrik

---

### Post by Majorix on 2007-07-11
915resolution is a package that you can install using the terminal or Synaptic. It is used with intel cards, as spoken by the above poster.

---

### Post by moore.bryan on 2007-07-12
*do you have an nvidia card?  that could also be the source of your problems...*

---

### Post by AndyCooll on 2007-07-12
Two points. First, what is your graphics card?
Second, you be able to quickly get up and running by accepting most of the defaults but choosing "vesa" at the graphics card section when you run "sudo dpkg-reconfigure xserver-xorg". It's a bog standard graphics card setting but it should at least get you started.

:cool:

---

### Post by fidde88pven on 2007-07-12
Oki! I will try some more then... My card is NVIDIA 6800, tanx

---


---
title: "i cant logon after disable nivida driver"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by DO55 on 2007-10-08
i enable Restricted Restricted Driver for nivida also enable (desktop effects)

it was work great  but after disable  Restricted Restricted Driver and restart i cant logon !!

when i try to log my account the screen change to white  and freeze  

what can i do ?

---

### Post by overdrank on 2007-10-08
> **DO55 said:**
> i enable Restricted Restricted Driver for nivida also enable (desktop effects)

it was work great  but after disable  Restricted Restricted Driver and restart i cant logon !!

when i try to log my account the screen change to white  and freeze  

what can i do ?

Hi when you reach the login screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

### Post by DO55 on 2007-10-08
it dose not work 

i select the card which i (nv) the select the resolution and restart

same problem

---

### Post by overdrank on 2007-10-08
> **DO55 said:**
> it dose not work 

i select the card which i (nv) the select the resolution and restart

same problem

Hi you can choose vesa as the driver and hopefully this will get you to the desktop.

---

### Post by DO55 on 2007-10-08
no

its not work

the problem is could be from (desktop effects ) is still enable 

if i can disable it maybe its will work

---

### Post by overdrank on 2007-10-08
> **DO55 said:**
> no

its not work

the problem is could be from (desktop effects ) is still enable 

if i can disable it maybe its will work

Hi you can remove the desktop effects with this command
```
sudo apt-get remove desktop-effects
```

---

### Post by DO55 on 2007-10-08
dose not work too

---

### Post by overdrank on 2007-10-08
> **DO55 said:**
> dose not work too

Ok, does the command remove the desktop effects? And did you reconfigure your xorg with vesa as the driver? And what nvidia card do you have?
And we are talking about Feisty not Gutsy?

---

### Post by DO55 on 2007-10-09
yes it remove it
and also reconfigure xorg with vesa

my card is   fx 5200 

Feisty

---


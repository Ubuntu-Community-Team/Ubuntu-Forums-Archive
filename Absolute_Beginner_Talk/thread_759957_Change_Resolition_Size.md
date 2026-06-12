---
title: "Change Resolition Size"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by xcvcx on 2008-04-19
Instead of going to the options and changing it from their. I want to make my resolution smaller.


and I need another msn copy... all these i keep getting told you download completely suck. people keep saying aMSN is the best if you want something like msn.. but it's not even close.

---

### Post by NightwishFan on 2008-04-19
For Msn I use pidgin, it does all I need. Although I only have one contact on Msn. :lolflag:

So for the resolution what do you mean not in options?

---

### Post by xcvcx on 2008-04-19
Instead of going to system and screen resolution. I remember seeing a guide on typing something in the terminal where i could select what screen resolution i want. the options in the system don't have the sizes i want

---

### Post by NightwishFan on 2008-04-19
I think you can try to reconfigure the xserver to do that.

---

### Post by xcvcx on 2008-04-20
Where do I go to do that? To get the xserver I don't remember.

---

### Post by chewearn on 2008-04-20
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by xcvcx on 2008-04-20
I didn't see any resolution changing when i entered that. Are you sure it's correct?

---

### Post by Claus7 on 2008-04-21
Hello,

if you type the aforementioned command it should open a window where it has such a format :

...
...
[ ] 1024*768
[ ]  800*600
...
...

[CENTER]ok[/CENTER]

if you press space in front of every resolution you wish (mind though that it should be supported both from your graphic card and your screen) and then press tab and enter (when ok has become red), you will be able to choose that resolution from System -> Preferences -> Screen resolution

Are you sure that your graphic card is recognised? If you type ```
lshw -short | grep display
``` 
it should show you your graphic card.

Regards!

---

### Post by xcvcx on 2008-04-21
Yea it recognizes it.

andrei@andrei-laptop:~$ lshw -short | grep display
WARNING: you should run this program as super-user.
/0/100/1/0               display     G70 [GeForce Go 7600]
andrei@andrei-laptop:~$

---

### Post by xcvcx on 2008-04-21
When it type the command i got before all i get is a bunch of keyboard options.

---

### Post by Claus7 on 2008-04-23
Hello,

is it possible to show us the result of the command? I haven't faced such a problem before...

Regards!

---


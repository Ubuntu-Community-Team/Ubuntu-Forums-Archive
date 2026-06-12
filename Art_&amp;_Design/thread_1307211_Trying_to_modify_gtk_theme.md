---
title: "Trying to modify gtk theme"
date: 2009-10-30
forum: Art &amp; Design
---

### Post by sigurnjak on 2009-10-30
I am trying to modify gtk theme but one aspect is driving me crazy .
There is a panel image i am trying to apply and for the life of me i do not seem to be able to apply it when i apply theme . I can apply it manually and it looks great . 
Could someone look at this .rc file and tell me  what should i edit to make changes stick .

Image name is this : panel-bg.png
Image is unflattened gradient , btw if that makes any difference .

And here is a screenshot with panel applied manually .

---

### Post by eamon63 on 2009-10-31
have you tried removing  #  before the line bg_pixmap[NORMAL] ?

---

### Post by sigurnjak on 2009-10-31
Yes , but then i loose transparency .

---

### Post by Giant Speck on 2009-10-31
> **sigurnjak said:**
> Yes , but then i loose transparency .

If I remember correctly, the Pixbuf theme engine does not support transparency.

---

### Post by sigurnjak on 2009-10-31
Ah , crack !!!! So  do you have any suggestion which engine i could try and  maybe simple info  for clutz like me  on how to change the engine ?

Btw here is link for mediafire  if someone  would like to tinker with it :
[http://www.mediafire.com/?sharekey=5232ffa158efbfeed6baebe61b361f7ce04e75f6e8ebb871](http://www.mediafire.com/?sharekey=5232ffa158efbfeed6baebe61b361f7ce04e75f6e8ebb871)

 Thank for your time guys !:p

---

### Post by eamon63 on 2009-10-31
> **sigurnjak said:**
> Yes , but then i loose transparency .


for panel transparency, use compiz settings instead...

---

### Post by sigurnjak on 2009-10-31
I tried that and then all icons go transparent as well .
I believe i need to find theme that uses engine with transparent gradient for panel . That way i could use my panel image for sharp glassy effect , while keeping icons sharp and in nice contrast . 

My greatest problem that this is my first attempt at modifying themes and i have so much to learn .;)

---

### Post by eamon63 on 2009-11-01
> **sigurnjak said:**
> I tried that and then all icons go transparent as well .
I believe i need to find theme that uses engine with transparent gradient for panel . That way i could use my panel image for sharp glassy effect , while keeping icons sharp and in nice contrast . 

My greatest problem that this is my first attempt at modifying themes and i have so much to learn .;)

how about via gnome panel properties, use panel-bg.png as background.  then in gtkrc, use a transparent image as background for all panel applets?

---

### Post by sigurnjak on 2009-11-01
Hi Eamon ! That is what i did , but it would be nicer to have it applied itself when theme is applied .

Regardless , it looks great now !

---

### Post by eamon63 on 2009-11-01
well, good for you.  but i think the issue of panel transparency is not with any theme engine but with gtk/gnome itself.

---

### Post by sigurnjak on 2009-11-02
So , i tried again and this time since i moved working file elsewhere  i got plain panel background. But when i ticked background image it finally showed up without me navigating to it . 
Well , it is some progress .:p

Cancel that , it didn't survive reboot.

---


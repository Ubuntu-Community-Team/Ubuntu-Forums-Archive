---
title: "installing new fonts"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by gervogero on 2007-12-12
im a beginner in the ubuntu world. im sorry if my questions are too simple to the more experimented users. im trying to install some truetype fonts i used in windows, i read in some forums that i could just copy them to the usr/share/fonts/truetype but i face a problem every time i try to do that. when i drop the fonts files in the folder an error pops out saying i have no permission to write in this folder. my question is how do i get permission for this, i mean im the only user of my laptop and im too the only administrator. i hope somebody can help me and i excuse myself again for such a basic question. thanks

---

### Post by NilsE on 2007-12-12
> **gervogero said:**
> im a beginner in the ubuntu world. im sorry if my questions are too simple to the more experimented users. im trying to install some truetype fonts i used in windows, i read in some forums that i could just copy them to the usr/share/fonts/truetype but i face a problem every time i try to do that. when i drop the fonts files in the folder an error pops out saying i have no permission to write in this folder. my question is how do i get permission for this, i mean im the only user of my laptop and im too the only administrator. i hope somebody can help me and i excuse myself again for such a basic question. thanks
Your doing the right thing but you need to be executing the copy under root.   Go into a terminal and type:  

gksudo nautilus 

Then you get past the permissions after you enter your password.

---

### Post by santiagoward2000 on 2007-12-12
> **gervogero said:**
> im a beginner in the ubuntu world. im sorry if my questions are too simple to the more experimented users. im trying to install some truetype fonts i used in windows, i read in some forums that i could just copy them to the usr/share/fonts/truetype but i face a problem every time i try to do that. when i drop the fonts files in the folder an error pops out saying i have no permission to write in this folder. my question is how do i get permission for this, i mean im the only user of my laptop and im too the only administrator. i hope somebody can help me and i excuse myself again for such a basic question. thanks

Hi and welcome!!
In Ubuntu, you normally don't have "Administrator" privileges like in Windows. To use programs with these privileges, you can use **gksudo**.
For example, if you want to copy a file to these folders, just open a Terminal and type:
```
gksudo nautilus
```
supposing you are using Nautilus...
Then, just enter your password and you can edit whatever you want. Just be careful with what you do with your privileges :lolflag:
Cheers!

---

### Post by gervogero on 2007-12-12
thanks a lot i finally did it

---

### Post by santiagoward2000 on 2007-12-12
> **gervogero said:**
> thanks a lot i finally did it

You're welcome! :)

---

### Post by fenian on 2007-12-12
The easiest way to install new fonts is to do this...
Open  a window and hit ctrl+l to show the location bar.In the location bar type...

 fonts:///

you can drag and drop the fonts you want to add into that window.

---

### Post by carloslosgrande on 2007-12-13
[FONT="Comic Sans MS"]Hey Fenian, great tip!
I don't mind the terminal but I'm bone lazy (and proud of it) and drag n drop always appeals to me:guitar:
Thanks[/FONT]

---

### Post by shuttleworthwannabe on 2007-12-13
synaptic has this under msttcorefonts, I think. It will install all common MS fonts, as far as I know.

---


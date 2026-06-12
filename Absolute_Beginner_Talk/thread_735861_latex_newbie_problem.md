---
title: "latex newbie problem"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by afeasfaerw23231233 on 2008-03-26
i never use kile before, i just download kile and don't know where to start. 
i click  'new' and type ' solve \cos 2x - sin^2 x = 0 \ ' but how can i get a preview of the equation? i google the web and cannot find some easy example. for example, i want to make a math question involving cosine law involving words and equation and paste it in openoffice writer, how can i do it? or can anyone give some simple working examples or tutorial link of kile for me? thanks

---

### Post by abo_shreek11 on 2008-03-26
what are you talking about ??

---

### Post by afeasfaerw23231233 on 2008-03-26
i already find a wikiguide of latex

---

### Post by bdsatish on 2008-03-26
I have not used kile. But whatever editor you use, it doesn't matter. Call your file "my_equation.tex" (say). All you need to do is, open a shell:

```
 [bash]$ latex my_equation.tex my_equation.dvi  
```

Which gives you the device independent code. Then you can use 'dvipng' or 'dvips' for obtaining a PNG image or a post-script file of your eqn. Something like,

```
 [bash]$ dvipng my_equation.dvi  
  [bash]$ dvips my_equation.dvi  

```

An even better way is to use pdftex:

```
 [bash]$  pdftex my_equation.tex

```
which will straightaway give you the PDF . You can do a prnt-screen and copy-paste into OpenOffice, etc.

---

### Post by frisket on 2008-04-09
Read [http://latex.silmaril.ie/formattinginformation/](http://latex.silmaril.ie/formattinginformation/)
for newcomer documentation

---


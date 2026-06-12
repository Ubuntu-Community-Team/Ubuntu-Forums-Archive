---
title: "Any way to make themes?"
date: 2010-01-19
forum: Art &amp; Design
---

### Post by Urhungry on 2010-01-19
I hope this is in the right place, sorry if it's not. Anyway, is there any way to make custom theme in xubuntu 9.10? I can't seem to find one anywhere. I would like to be able to have at least custom panel colors, and a custom applications menu button. I have no knowlage of any computer code at all, so sorry about that. Thanks!

---

### Post by alwayshere on 2010-01-19
[http://blog.golden-ratio.net/2008/05/compiz-and-emerald-in-xubuntu/]("http://blog.golden-ratio.net/2008/05/compiz-and-emerald-in-xubuntu/")

---

### Post by sliketymo on 2010-01-19
[http://xfce-look.org/](http://xfce-look.org/)

---

### Post by Urhungry on 2010-01-19
No, I meant customising it, not using pre made ones. So I can draw my own icon for the applications menu, for example.

---

### Post by alwayshere on 2010-01-19
KIconEdit

sudo apt-get install kiconedit

---

### Post by Urhungry on 2010-01-20
Thank you, but I already solved that probem. Sorry!

---

### Post by dzon65 on 2010-01-20
Might wanna start using an existing theme and change the theme's gtkrc.

---

### Post by Urhungry on 2010-01-20
I tried that, but it won't save it. Sorry if this is obvious.

---

### Post by dzon65 on 2010-01-20
?????Should save it.Whatever changes you do to a script(wheteher it's css or bg/png),just save as such.Probably will have to log out/in.

---

### Post by Urhungry on 2010-01-20
The scripts won't save in the original folder at all, as the same name or not. I can only save to my desktop or something like that. Can the os read it anyway? Thanks!

---

### Post by dzon65 on 2010-01-20
If it's a gtk theme:home>show hidden files>themes>whatever theme you use>gtk2>gtkrc.
Now,whatever you change in there,whether it's text-color,buttons.........is saved by closing (x) the gtkrc.A window will pop up asking you to close without saving........Like this.

---

### Post by Urhungry on 2010-01-20
I will try that. Thank you.

---

### Post by Urhungry on 2010-01-20
Ok, I do that, and it retire an error and says it can't save.

---

### Post by durand on 2010-02-11
Are you trying to edit the theme in a system folder? In that case, you need to copy it to ~/.themes first.

---


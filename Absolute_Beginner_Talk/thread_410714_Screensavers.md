---
title: "Screensavers?"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by swey on 2007-04-16
My screensavers don't seem to be working properly. I can preview them all  - inc fullscreen, but when the Pc goes idle it just goes black whatever saver I have selected.

---

### Post by DougieFresh4U on 2007-04-16
Can you supply a little more info - What version of Ubuntu are you using? :D

---

### Post by swey on 2007-04-16
6.10

Geforce 2 ultra graphics card. athlon 500

---

### Post by FuriousLettuce on 2007-04-16
Check your power management settings (System -> Preferences -> Power Management), make sure that the options to blank the screen are set to 'never'.

---

### Post by swey on 2007-04-17
Yes they are set to never.

---

### Post by swey on 2007-04-20
Still can't get this to work??

---

### Post by mh114 on 2007-04-21
I have the same problem with Feisty.. I have disabled the power management, even disabled the services.. :?

EDIT: Solved it. It was because of Xgl, like most of my problems so far.. ;)

---

### Post by swey on 2007-04-21
> **mh114 said:**
> I have the same problem with Feisty.. I have disabled the power management, even disabled the services.. :?

EDIT: Solved it. It was because of Xgl, like most of my problems so far.. ;)

What's XGL and how did you fix it?

---

### Post by mh114 on 2007-04-21
> **swey said:**
> What's XGL and how did you fix it?
Xgl is for using the composite desktop effects, it's not the preferred way (AIGLX is) and many things sort of break when it's used.. So I just tried a normal Gnome session instead of Xgl session, and booom it worked. :D

---

### Post by swey on 2007-04-21
How do you do that? I thought Ubuntu used KDE

---

### Post by mh114 on 2007-04-21
> **swey said:**
> How do you do that? I thought Ubuntu used KDE
No, Ubuntu has Gnome by default. And the Xgl session isn't there by default, so chances are your problem isn't related to Xgl at all.. Unless you have manually set it up. :)

---


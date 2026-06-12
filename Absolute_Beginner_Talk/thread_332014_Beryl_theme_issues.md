---
title: "Beryl theme issues"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2007-01-05
Hey folks. I've just installed Beryl (successfully) and I've got to say, I'm not as impressed as I thought I'd be . . .it's kinda cool, I guess, but I thought there would be some more function to it, instead of just pretty colours. ~LOL~ But if that's all it is, I can live with that . . .I just want the colours to be of my choosing. ~LOL~ My issue is with the cube's background and that stupid Christmas tree image on the cube . . .how do I change that, and the black backing?

---

### Post by Sasa_Ivanovic on 2007-01-05
download emerald-themes :
```

sudo apt-get install emerald-themes

```
run beryl-manager, go to beryl settings.

---

### Post by CheshireMac on 2007-01-05
> **Sasa_Ivanovic said:**
> download emerald-themes :
```

sudo apt-get install emerald-themes

```
run beryl-manager, go to beryl settings.

mac@mac-desktop:~$ sudo apt-get install emerald-themes
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

 Any thoughts on that? ~LOL~

---

### Post by MkfIbK7a on 2007-01-05
that means you are running synaptic or apt-get or add-remove at the same time...
~LOL~

---

### Post by CheshireMac on 2007-01-05
> **wert613 said:**
> that means you are running synaptic or apt-get or add-remove at the same time...
~LOL~

Oh . . .I'm updating the system (Done now) . . .that uses Synaptic or Apt_Get? Learn something new every day . . .~LOL~

---

### Post by MkfIbK7a on 2007-01-05
it certainly uses apt-get 
but what i meant is you cant install things from two places at one

---

### Post by CheshireMac on 2007-01-05
> **wert613 said:**
> it certainly uses apt-get 
but what i meant is you cant install things from two places at one

I understand. I got it to work now. Thanks. :)

---

### Post by MkfIbK7a on 2007-01-05
no problem:D

---

### Post by macogw on 2007-01-05
To change the endcaps on the cube, go into Beryl settings, go into Desktop, Desktop Cube, then click the "caps" tab.  Change the pictures that are in those boxes.

---

### Post by mahiyar on 2007-01-05
I thought when u install beryl emerald themes comes with it. To change the cubes background (if i understand u right) go to beryl settings manager > Desktop > Desktop cube >Options> Cube colour. If you mean the background while rotating that's skydome u can access it by beryl settings manager > Desktop > Desktop cube >Options>Skydome

---

### Post by macogw on 2007-01-05
> **mahiyar said:**
> I thought when u install beryl emerald themes comes with it. To change the cubes background (if i understand u right) go to beryl settings manager > Desktop > Desktop cube >Options> Cube colour. If you mean the background while rotating that's skydome u can access it by beryl settings manager > Desktop > Desktop cube >Options>Skydome

Only if you use aptitude.  If you use apt-get, Emerald doesn't go with it.

---


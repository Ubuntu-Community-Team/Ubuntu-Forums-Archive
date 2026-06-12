---
title: "compiz theme"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by athiwatc on 2007-11-17
How do i install the compiz theme

i got ccsm runing but i can't find where to install

---

### Post by DutyDuty on 2007-11-17
You install it in emerald. Then highlight it and close emerald. Run ```
emerald --replace &
``` and then ```
compiz --replace &
``` in terminal. If that doesn't work, run them in the opposite order.

---

### Post by atomkarinca on 2007-11-17
if you have installed emerald then hit alt+f2 and type

```
emerald-theme-manager
```

it should open up emerald theme manager. themes settings > themes > import. browse through the directory you saved your emerald theme file. that's it. if you haven't selected emerald as your your default window decorator then you can do it via fusion icon or again hit alt+f2 and type

```
emerald --replace
```

---

### Post by athiwatc on 2007-11-17
> **atomkarinca said:**
> if you have installed emerald then hit alt+f2 and type

```
emerald-theme-manager
```

it should open up emerald theme manager. themes settings > themes > import. browse through the directory you saved your emerald theme file. that's it. if you haven't selected emerald as your your default window decorator then you can do it via fusion icon or again hit alt+f2 and type

```
emerald --replace
```

How do i install emerald ??

---

### Post by DutyDuty on 2007-11-17
```
sudo apt-get install emerald
```

---

### Post by athiwatc on 2007-11-17
I got it working thanks everyone..!!!

---

### Post by meindian523 on 2007-11-17
Jumping in,but doing sudo apt-get install emerald also tries to install beryl.....I already have C-F,why should I install Beryl again??

---

### Post by atomkarinca on 2007-11-17
> **meindian523 said:**
> Jumping in,but doing sudo apt-get install emerald also tries to install beryl.....I already have C-F,why should I install Beryl again??

then you can installing it via synaptic package manager. it should be in the repositories.

---

### Post by DutyDuty on 2007-11-17
Sorry, maybe find a way to get the compiz version then. If you find a better solution, please tell. Thanks.

---

### Post by athiwatc on 2007-11-17
got a problems again by title bar is gone
:confused::confused:

---

### Post by DutyDuty on 2007-11-17
```
emerald --replace
``` then```
compiz --replace &
``` (Two separate commands in separate terminals.)

---

### Post by atomkarinca on 2007-11-17
> **athiwatc said:**
> got a problems again by title bar is gone
:confused::confused:

try whether

```
gtk-window-decorator --replace
```

or

```
emerald --replace
```

after hitting alt+f2. or if you have fusion icon, right-click and select "default window decorator" and change back and forth.

---

### Post by meindian523 on 2007-11-17
Should I be installing compiz-gtk?It will remove the metapackages compiz and compiz-gnome.

---

### Post by athiwatc on 2007-11-17
> **meindian523 said:**
> Should I be installing compiz-gtk?It will remove the metapackages compiz and compiz-gnome.

what your theme name on your display i like it a lots thanks

---

### Post by meindian523 on 2007-11-17
It's actually a number of windows open with varying degrees of transparency....no theme.....using C-F.....

---


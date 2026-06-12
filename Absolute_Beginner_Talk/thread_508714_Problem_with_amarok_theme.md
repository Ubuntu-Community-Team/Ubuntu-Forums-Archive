---
title: "Problem with amarok theme"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by czepluch on 2007-07-24
Hi, i've got this problem with amarok that i can't get any themes to work. can anyone tell me why it isnt working.?

I've just thrown in a screenshot maybe that can help a little.

---

### Post by testube_babies on 2007-07-24
Looks like you're using Gnome?  Amarok won't take your gnome themes.  I use kcontrol to change the themes of my KDE apps.
```
sudo apt-get install kcontrol
```

---

### Post by Dan Hammond on 2007-07-24
I can't reallytell if you are using KDE or gnome from that screenshot. I presume you are using gnome in which case the full amaroK themes will not work, however you can use context browse themes. if you are using KDE then i cannot help

oops someone said that while i was writing

---

### Post by czepluch on 2007-07-24
> **testube_babies said:**
> Looks like you're using Gnome?  Amarok won't take your gnome themes.  I use kcontrol to change the themes of my KDE apps.
```
sudo apt-get install kcontrol
```

Yes im using GNOME so if i do the command then what ?

---

### Post by testube_babies on 2007-07-24
Then open kcontrol (ALT+F2 and enter kcontrol, I'm not sure if it shows up in the menus).  You can customize your KDE theme in the first few settings.

---

### Post by czepluch on 2007-07-24
> **testube_babies said:**
> Then open kcontrol (ALT+F2 and enter kcontrol, I'm not sure if it shows up in the menus).  You can customize your KDE theme in the first few settings.

Yeah but i dont understand how i can make the themes work for amorok?

---

### Post by czepluch on 2007-07-24
> **Dan Hammond said:**
> I can't reallytell if you are using KDE or gnome from that screenshot. I presume you are using gnome in which case the full amaroK themes will not work, however you can use context browse themes. if you are using KDE then i cannot help

oops someone said that while i was writing

Context browse themes ?

---

### Post by testube_babies on 2007-07-24
> **czepluch said:**
> Yeah but i dont understand how i can make the themes work for amorok?

Gnome applications are build on GTK, and Gnome has the power to apply its theme across all GTK apps.  Amarok is NOT built on GTK, it is built on Qt.  KDE has the power to apply its theme across all Qt apps.  So, if you install a KDE theme switcher, you can change the theme of Amarok.

I'm not sure there is a way to make your KDE theme mimic your Gnome theme without manually setting it.

---

### Post by testube_babies on 2007-07-24
> **czepluch said:**
> Context browse themes ?

Click the "Context" button with the little "i" logo.  You can choose the theme of this browser from within Amarok (It looks like you've chosen d_u_s_t_blue_round).

---

### Post by czepluch on 2007-07-24
> **testube_babies said:**
> Gnome applications are build on GTK, and Gnome has the power to apply its theme across all GTK apps.  Amarok is NOT built on GTK, it is built on Qt.  KDE has the power to apply its theme across all Qt apps.  So, if you install a KDE theme switcher, you can change the theme of Amarok.

I'm not sure there is a way to make your KDE theme mimic your Gnome theme without manually setting it.

Really dont understand how to make it work though ?

---

### Post by czepluch on 2007-07-24
bump

---

### Post by czepluch on 2007-07-24
please

---

### Post by testube_babies on 2007-07-24
Install kcontrol, open it up, change your theme, hit apply.  That's it!  Without installing some sort of KDE theme switcher, you CANNOT change the theme of Amarok!

In Kcontrol, change these to whatever you want and you will see a difference in Amarok:
Appearance & Themes
-> Colors
-> Fonts
-> Icons
-> Style

---


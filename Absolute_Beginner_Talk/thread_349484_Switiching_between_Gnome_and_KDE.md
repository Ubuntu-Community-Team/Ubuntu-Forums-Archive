---
title: "Switiching between Gnome and KDE"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by stoney39 on 2007-01-30
I was wondering if there is a easier way to move between the KDE desktop and Gnome other than logging out to switch. I still have not made up my mind on witch to stay with. I find something works better in one or the other. Any help would be welcomed.

---

### Post by ComplexNumber on 2007-01-30
> **stoney39 said:**
> I was wondering if there is a easier way to move between the KDE desktop and Gnome other than logging out to switch. I still have not made up my mind on witch to stay with. I find something works better in one or the other. Any help would be welcomed.
install fast-user-switch-applet. i think that does the trick.

---

### Post by Wikzo on 2007-01-30
A little off topic: Is there any easy guides to install KDE in Ubuntu? A kind of a newbie guide, please.

**EDIT:** Found this Just forget my message ...

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by taurus on 2007-01-30
> **Wikzo said:**
> A little off topic: Is there any easy guides to install KDE in Ubuntu? A kind of a newbie guide, please.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---

### Post by Ubuntu Joe on 2007-01-30
[FONT="Comic Sans MS"][SIZE="3"]So, I installed Kubuntu-desktop . . . didn't really like it . . . removed it . . . but now, I can't get Ubuntu Fonts to go back to the size I like . . . !!   I have horrible eye-sight, and I need the font size around 22 . . . for some reason, since installing KDE, the font size stays stuck at around 16 . . . what gives?![/SIZE][/FONT]

---

### Post by ComplexNumber on 2007-01-30
> **Ubuntu Joe said:**
> [FONT=Comic Sans MS][SIZE=3]So, I installed Kubuntu-desktop . . . didn't really like it . . . removed it . . . but now, I can't get Ubuntu Fonts to go back to the size I like . . . !!   I have horrible eye-sight, and I need the font size around 22 . . . for some reason, since installing KDE, the font size stays stuck at around 16 . . . what gives?![/SIZE][/FONT]
go to the kde control centre(if its not in your menu, type in 'kcontrol' from ther terminal) and type in "fonts" in the search. change the fonts from there.

---

### Post by stoney39 on 2007-01-30
I install the fast switch applet and it is working great. Thanks for the help

---

### Post by Ubuntu Joe on 2007-01-30
> **ComplexNumber said:**
> go to the kde control centre(if its not in your menu, type in 'kcontrol' from ther terminal) and type in "fonts" in the search. change the fonts from there.

Is kcontrol still there?  Even though I deleted the kubuntu-desktop?  Lemme see . . .

---

### Post by taurus on 2007-01-30
Can you change the size in System -> Preference -> Font?

---

### Post by Ubuntu Joe on 2007-01-31
Sigh . . . naturally:

```
thom@ubuntu-joe:~$ kcontrol
bash: kcontrol: command not found

```

And, no, I'm afraid I can't change the font the old fashioned way in the Preferences . . . it's KILLING me . . .

---

### Post by undertakingyou on 2007-01-31
Could you have apt or synaptic reinstall the regular ubuntu-desktop?  Might work :???: 

UNDERTAKINGYOU--
------------------------

---

### Post by Ubuntu Joe on 2007-01-31
Great minds think alike . . . but that didn't work either . . .

Frustrations . . .

---


---
title: "Where do i find my icons?"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by ajmorris on 2007-01-12
I was running kool dock and when you add an application to it and you choose an icon it has "system icons." I am now running another dock from gdesklets. My question is how do i get the "system icons" it displays in kool dock to display in gdesklets?

(it is not /usr/share/pixmaps, i have already checked there)

Attatched is what i am talking about.

---

### Post by sardion on 2007-01-12
Most (not all unfortuantely but most) live in either /usr/share/pixmaps (as you know of) or in /use/share/icons which has a lot of subdirectories.

If looking for something in particular (such as office icons) I generally do:

find /usr/share/icons | grep office

to see what's where.

---

### Post by jem7v on 2007-01-12
And sometimes the icons you download hide in ~/.icons

---

### Post by ajmorris on 2007-01-12
> **sardion said:**
> Most (not all unfortuantely but most) live in either /usr/share/pixmaps (as you know of) or in /use/share/icons which has a lot of subdirectories.

If looking for something in particular (such as office icons) I generally do:

find /usr/share/icons | grep office

to see what's where.


Thanks. Worked perfectly.

---

### Post by ComplexNumber on 2007-01-12
**ajmorris**
although you have already solved the problem, another place to look is in /usr/share/icons/hicolor. most icon themes don't contain all the icons. for those icons that are missing, the system will look in any icon theme that the selected icon theme inherits. most distros have a default icon theme (this is stated in /usr/share/icons/default). what it can't find in there, it will look in /usr/share/icons/hicolor. basically it looks down the 'chain'. the chain is as follows:

selected icon theme -> icon theme that the selected icon theme inherits(this is stated in the index.theme file in the selected theme) -> theme stated in /usr/share/icons/default -> hicolour.


i may have got a slight detail wrong, but thats basically how it works.

---


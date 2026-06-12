---
title: "Make Gnome-Shell themes compact"
date: 2011-11-22
forum: Art &amp; Design
---

### Post by jastonas on 2011-11-22
I would like to make gnome-shell more compact.
I tried reducing the font size but that's is all there is to it.

Is there any other way to maybe edit the theme settings and make them compact?

Too much space used :/

---

### Post by ShodanjoDM on 2011-11-22
Like in Activities/Applications view?

You can edit the gnome-shell.css file and find these lines (from Ambiance Blue gnome-shell theme for example):

> .icon-grid {
    spacing: 48px;
    -shell-grid-item-size: 118px;
}

.contact-grid {
    spacing: 48px;
    -shell-grid-item-size: 284px; /* 2 * -shell-grid-item-size + spacing */
}

.icon-grid .overview-icon {
    icon-size: 80px;
}


And change them to something like this:

> .icon-grid {
    spacing: 24px;
    -shell-grid-item-size: 70px;
}

.contact-grid {
    spacing: 24px;
    -shell-grid-item-size: 70px; /* 2 * -shell-grid-item-size + spacing */
}

.icon-grid .overview-icon {
    icon-size: 36px;
}


Now I have my Applications view a lot more compact and nicer to look.

---

### Post by jastonas on 2011-11-22
That's a nice tip! But I would like it to be global. Like for menus in every windows, fonts, everything!

Look the example [here]("http://askubuntu.com/questions/23523/how-can-i-make-ubuntu-gnome-look-better-i-e-more-smaller-and-compact").
How much space ubuntu is using and how much windows.

---


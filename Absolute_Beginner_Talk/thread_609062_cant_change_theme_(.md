---
title: "cant change theme :("
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-11-10
whenever i try to change my deasktop theme to 'Darker Theme' or anything, it stays the same,

since i restarted, i dont now whats cuased this.

ideas of the problem?

from the logs its starting BEFORE Dbus, how do i make it start after dbus?

---

### Post by skymera on 2007-11-10
anyone?

it seems my threads never get answered =*(

---

### Post by Drakkor on 2007-11-10
If you have CompizFusion,just hit the windoze...super key and m , and the whole thing will be a negative,very dark and easy on the eyes !  :)

---

### Post by Pumalite on 2007-11-10
You also have this:

[http://technology.desktopnexus.com/tags/all/ubuntu/](http://technology.desktopnexus.com/tags/all/ubuntu/)

---

### Post by skymera on 2007-11-10
ermm no thats not what i mean, but thanks.

like if i click one theme, it will stay default. 
if i  click qanother, it wil still be default.

gnome settings daemon is starting before dbus, i need it to start after, what do i do?

---

### Post by jordank on 2007-11-10
how do you get compiz fusion? i like the look of that dark theme, how could i go about getting it?  I'm using the default gnome look right now, with the orange title bars and such.
I dont really understand the concept of themes.

---

### Post by Drakkor on 2007-11-10
What version of Ubuntu are you using ?

---

### Post by Pumalite on 2007-11-10
This might help?:

[http://ubuntuforums.org/archive/index.php/t-339318.html](http://ubuntuforums.org/archive/index.php/t-339318.html)

---

### Post by jordank on 2007-11-10
gutsy

---

### Post by jordank on 2007-11-10
Like how would i get my theme sort of like drakkors there? where i can get a dark look to my taskbars and such?
do i need compiz? if so what would i search in synaptics?

---

### Post by skymera on 2007-11-10
why you hijacking my thread? =@

pumalite - thanks for link i check it out

---

### Post by skymera on 2007-11-10
ok the logs say that the Gnome-settings-daemon

which controls all the looks, themes etc is starting before DBUS, thus causing it not to work.

i nedd to make it start after dbus or make dbus start before.

thanks for your help

---

### Post by skymera on 2007-11-10
dont qworry, sorted it on my own ¬.¬

added dbus to run levels 2,3,4,5 and S

---


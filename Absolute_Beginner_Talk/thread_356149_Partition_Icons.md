---
title: "Partition Icons"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-02-08
i have added all my partitions to /etc/fstab and even doen the mount -a as usual, but now i am becoming greedy, i want to have icons of those partitions if not on desktop then atlast in Storage Media

---

### Post by xpod on 2007-02-08
I think you want to use the configuration editor to check the  "volumes visible" box.

Open the configuration editor and navigate to "apps>nuatilus>desktop and check the things you want visible on your desktop.:)

EDIT:or is that something else?

---

### Post by renzokuken on 2007-02-08
for me, automounting the partitions at boot using fstab automatically put drive icons on my desktop for me.

you using gnome or KDE?

---

### Post by shoaibi on 2007-02-08
using GNOME
[EID[:
where is the conf editor?

---

### Post by renzokuken on 2007-02-08
in the system menu somewhere i think

---

### Post by shoaibi on 2007-02-08
nope, nothing like that....

---

### Post by xpod on 2007-02-08
You can enable it via the menu editor,Just right click your menu to access.
It`ll show up in system tools:)

---

### Post by shoaibi on 2007-02-08
sorry can't understand what menu editor?
System>>Preferences>Menu Layout??
Can't find to enable it there...

---

### Post by shoaibi on 2007-02-08
its already seleceted i.e.e already checked the visible option...

---

### Post by xpod on 2007-02-08
You can just run "gconf-editor" to bring configuration editor up if your having trouble finding it.

You`ll fiind it in the menu editor if you look under the "system tools" section too though

---

### Post by xpod on 2007-02-08
Sorry...to run "gconf editor" hit ALT-F2 and type it in there or open a terminal and type it in there.
You should get the thing shown below

[ATTACH]24814[/ATTACH]

I`m not sure if it`s menu editors or gconf editors your having trouble with now...:)

---

### Post by renzokuken on 2007-02-08
i think the menu editor is called A La Carte or something in the applications menu

---

### Post by xpod on 2007-02-08
It is alacarte in Dapper right enough but still just right clicking the menus and "edit menu" will bring it up regardless of what it`s called i think.

---

### Post by shoaibi on 2007-02-08
but volumes_visible is already set to true :(
what do i do? i ahev even restarted :(

---

### Post by dannyboy79 on 2007-02-08
the other guy is most likely thinking of the icons that appear on his desktop when he has usb drives plugged in at bootup. cause I use gnome and have my extra drives and partitions mounted automagically within fstab and there are no icons on my desktop. if you really want a shortcut to that partition, you can create a launcher on your desktop. I tyhink you can right click on your desktop, chose create launcher, then go from there. 

here is a link to help you, I simply found it by using the **search** function using "desktop launcher" right here in the forums.

[http://www.ubuntuforums.org/showthread.php?t=355001&highlight=desktop+launcher](http://www.ubuntuforums.org/showthread.php?t=355001&highlight=desktop+launcher)

---

### Post by shoaibi on 2007-02-08
I was talking about the Fixed HD Partitions that i have inserted into fstab,
anways after a few restart the problem has been solved strangely...

---


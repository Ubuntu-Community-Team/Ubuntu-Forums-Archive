---
title: "mouse pointers"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by rob1984 on 2007-12-22
can anyone tell me how to change my mouse pointers?

like select which pointer i want for each action ie. resize, text, busy...

i found where to change the general pointer but nothing else

any help would be greatly appreciated.

---

### Post by Pumalite on 2007-12-22
System>Preferences>Appearance>Customize>Pointers

---

### Post by Pumalite on 2007-12-22
You can use Synaptic to install icons and themes related to cursors.

---

### Post by Sbarton on 2007-12-22
Pumalite has shown you the place for changing cursers but I think you need to download a curser theme/s for what you are after, as well as synaptic.
regards

---

### Post by fenixfox on 2008-01-10
I have a cursor theme downloaded. I go to system>appearance>customize>pointers. I have tried dragging and dropping the extracted and unextracted version of the pointers file.

---

### Post by Fabiano Shark on 2008-01-10
You must have to paste the extracted folder of mouse theme in 

```
/usr/X11R6/lib/X11/icons/
``` 

then you can go to the "Mouse Preferences". ;)

---

### Post by fenixfox on 2008-01-10
I'm not exactly sure how to do that. What are all the commands involved?

---

### Post by Fabiano Shark on 2008-01-10
try this:
```
sudo cp /place/where/mouse_theme_is /usr/X11R6/lib/X11/icons/
password:
```

then go to menu System->Preferences->Mouse->Pointers

---

### Post by chucker on 2008-01-11
Im new to linux im using ubuntu 7.10 im wantint to get the mouse wheel to work.

---

### Post by Niniel on 2008-01-11
The wheel should work out of the box... the interesting part is trying to configure additional buttons... :(

---

### Post by Fabiano Shark on 2008-01-12
> **chucker said:**
> Im new to linux im using ubuntu 7.10 im wantint to get the mouse wheel to work.

Please, copy here the mouse's section from your xorg.conf, maybe it's only add these two stronged lines on it:

```

eg.: $ gedit /etc/X11/xorg.conf

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
[B]	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
[/B]EndSection
```

---

### Post by philinux on 2008-01-12
> **rob1984 said:**
> can anyone tell me how to change my mouse pointers?

like select which pointer i want for each action ie. resize, text, busy...

i found where to change the general pointer but nothing else

any help would be greatly appreciated.


I've been using these for a while. Really good effect.

[http://www.gnome-look.org/content/show.php/Silver+XCursors+3D?content=5533&PHPSESSID=b0b8df580189d1852d1bb7db0539a400](http://www.gnome-look.org/content/show.php/Silver+XCursors+3D?content=5533&PHPSESSID=b0b8df580189d1852d1bb7db0539a400)

---


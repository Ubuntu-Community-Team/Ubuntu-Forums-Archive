---
title: "How to change startup splash screen ?"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by tomaasj on 2007-07-09
Anyone,

how to change startup splash screen ?

Tomaasj

---

### Post by zanazzi on 2007-07-09
u can find it in; control settings/apearance and themes

---

### Post by tomaasj on 2007-07-09
Hi zanazzi,

how do I get there ? Under System Preferences ?  or Administration ?

Tomaasj

---

### Post by Rui Pais on 2007-07-09
Hi, at least 3 ways:

Run 
```
gconf-editor
```
go apps->gnome-session->options->splash_image. Double-click and change path.

Manually change path for the splash you want. Ubuntu defaults is /usr/share/pixmaps/splash/ubuntu-splash.png

Get some gui to do that:
```
sudo apt-get install gnome-splashscreen-manager
```

then run:
```
gksudo gnome-splashscreen-manager
```

:)

---

### Post by overdrank on 2007-07-09
> **Rui Pais said:**
> Hi, at least 3 ways:

Run 
```
gconf-editor
```
go apps->gnome-session->options->splash_image. Double-click and change path.

Manually change path for the splash you want. Ubuntu defaults is /usr/share/pixmaps/splash/ubuntu-splash.png

Get some gui to do that:
```
sudo apt-get install gnome-splashscreen-manager
```

then run:
```
gksudo gnome-splashscreen-manager
```

:)

Great thanks cool tip!:guitar:

---

### Post by tomaasj on 2007-07-09
Hi,

thanks for the info,

again a step forward !

gr. Tomaasj

---


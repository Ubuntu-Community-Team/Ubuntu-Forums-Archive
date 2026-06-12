---
title: "Lucid style Gnome-Do icon"
date: 2010-05-08
forum: Art &amp; Design
---

### Post by Minipalmer on 2010-05-08
Hey champs,

I'd like to create a Lucid style Gnome-Do tray icon, so as the fit in with everything else in my tray. Does anyone know where this is found? I've been looking everywhere and can't find it.

If you can help me find it, I'd be happy to share.

---

### Post by shafin on 2010-05-09
The icons for gnome do are already there, you only need to activate them.

1. run gksu nautilus (Alt+F2)

2.Go to the following folders one by one:
/usr/share/icons/ubuntu-mono-dark/apps/22
/usr/share/icons/ubuntu-mono-dark/apps/24
/usr/share/icons/ubuntu-mono-light/apps/22
/usr/share/icons/ubuntu-mono-light/apps/24

3.And rename the icon gnome-do-symbolic to gnome-do

You'll get your lucid style panel icons :)

---

### Post by Minipalmer on 2010-05-10
Thank you good sir, problem solved.

Wait, no it didn't... Did what you said but it's not working.

---

### Post by AJCF on 2010-05-11
It didn't work for me neither. Does anyone know how to solve this riddle? :P

---

### Post by AJCF on 2010-05-14
Anyone?

---

### Post by Minipalmer on 2010-05-14
It is interesting that the icon is there but I can't get it to work.

Maybe it needs a different name other than just "gnome-do"?

HMMMMMMMM

---

### Post by AJCF on 2010-05-14
It depends, do we know the name of the icon it's currently using? We could just replace it.

---

### Post by Minipalmer on 2010-05-18
That was what I was originally asking. Someone has to know!

---

### Post by debdiesel on 2010-06-10
If you installed gnome-do using a .deb file, you can simply run:
```
dpkg -L gnome-do
```
The output will show you all files installed with the package.

My icons for gnome-do are in the following locations:
```
/usr/share/icons/hicolor/16x16/apps/gnome-do.png
/usr/share/icons/hicolor/22x22/apps/gnome-do.png
...

```

---

### Post by Minipalmer on 2010-06-11
Great tip, thanks

---


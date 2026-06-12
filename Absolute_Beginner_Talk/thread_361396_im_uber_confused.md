---
title: "im uber confused"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by 006rocks on 2007-02-14
im totaly new to this whole thing...i got the 6.06. something server installed on my pc. (im using windows 95/ME right now since ubuntu is not working). after i log in and it says something about sudu command and administrator...what am i supposed to type in to get to the desktop?

---

### Post by Bachstelze on 2007-02-14
You installed the server edition (i.e. command line only), which is obviously not what you want. You can install a graphical insterface with

```
sudo aptitude install ubuntu-desktop
```

(You can replace ubuntu wuth kubuntu, xubuntu or edubuntu depending on the desktop you want )

---

### Post by charles.g.moore on 2007-02-14
If you wanted to install the desktop version of ubuntu then I think you installed the wrong one. You want the Desktop version not the server version.

If you purposely installed the server version then I think there is no gui installed by default, you have to
sudo aptitude update
sudo aptitude install ubuntu-desktop (i think thats the package)

---

### Post by Vorian on 2007-02-14
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start 
```

---

### Post by oilchangeguy on 2007-02-14
ok, can you provide the correct version of ubuntu you have? and your computers specs. and what operating system are you now running? there's no 95/ME it's either or, but not both.

---

### Post by 006rocks on 2007-02-14
i feel so stupid!

---

### Post by charles.g.moore on 2007-02-14
Don't sweat it all of us started at the beginning, just be sure to read everyone's questions carefully.

---


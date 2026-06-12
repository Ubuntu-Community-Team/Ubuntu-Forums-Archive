---
title: "ubuntu login"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by sfx113 on 2008-01-17
hi im having problems loging in 

after i enter my user name and password i get 

myusername@ubuntuhome:~$

what do i do there ??

any help

---

### Post by lgambett on 2008-01-17
This is Linux without graphical interface... Try to start the interface writing
[SIZE="2"][COLOR="Black"]startx[/COLOR][/SIZE]
Most likely you will receive an error message, post it there.

---

### Post by bodhi.zazen on 2008-01-17
sounds like you have logged in. Are you wanting a gui ?

type :

```
startx
```

Did you install the server version ?

Videocard ?

---

### Post by sfx113 on 2008-01-17
> **lgambett said:**
> This is Linux without graphical interface... Try to start the interface writing
[SIZE="2"][COLOR="Black"]startx[/COLOR][/SIZE]
Most likely you will receive an error message, post it there.


hi im in windows now i installed ubuntu studio i did try startx with an errro im not sure but i think it was 

could not find startx???

---

### Post by sfx113 on 2008-01-17
> **bodhi.zazen said:**
> sounds like you have logged in. Are you wanting a gui ?

type :

```
startx
```

Did you install the server version ?

Videocard ?

i installed ubuntu studio

im wanting just to get to the desktop ??

---

### Post by lgambett on 2008-01-17
Possibly you have installed the server version, i.e. without the graphical interface.

---

### Post by sfx113 on 2008-01-17
how do i get to the desktop or graphical interface.

---

### Post by lgambett on 2008-01-17
Personally I would repeat the installation using the Desktop version, because I do not know exactly what are the packages missing in the server version.
Anyway if you want to try to install the desktop environment you can try
[COLOR="Black"]sudo aptitude install gnome-desktop-environment[/COLOR]

---

### Post by bodhi.zazen on 2008-01-17
Try :

```
sudo apt-get install ubuntu-desktop
```

If it is already installed we need to know more about your hardware. videocard in particular.

---


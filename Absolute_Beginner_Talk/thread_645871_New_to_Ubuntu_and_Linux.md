---
title: "New to Ubuntu and Linux"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by kokomonjo on 2007-12-20
Hi I need some help.

I have recently installed Ubuntu 7.10 amd64 version. I have been successful with installing a few thing s though I am not totally sure how I have done a few of them. Anyway I have downloaded a few things and I am not sure how to install them and would appreciate any help. 

First off I downloaded a new icon set from gnome-look.org it is .bz2 file and all i can do is exctract it. I do not have a tab for icons under my themes and do not know how to install.

Secondly I have downloaded the walpapoz application and do not know how to install it either anyway any and all help would be welcome

---

### Post by kokomonjo on 2007-12-20
Also the wallpapoz is a tar.bz2 file if this is helpful.

---

### Post by TheLions on 2007-12-20
to get wallpaper changer go to synaptec (system->administration->synaptec) and type in search box "wallpaper tray"

to install any app , unpack it to some folder (usualy /home) and open the terminal (programs->applications)
and type 
```

sudo su
```

to get superuser privileges

then 

```
cd /home/nameofyourprogram
```

to open dir

then

```
./configure
./install
```

and app will install if there is install script

hope i helped:lolflag:

---

### Post by intensely on 2007-12-20
IF you want a good overview for installing themes icons and that sort of thing you should go to [http://tuxenclave.wordpress.com/2007/11/23/ubuntu-customization-guide-v2/](http://tuxenclave.wordpress.com/2007/11/23/ubuntu-customization-guide-v2/)

---

### Post by intensely on 2007-12-20
> **TheLions said:**
> to get wallpaper changer go to synaptec (system->administration->synaptec) and type in search box "wallpaper tray"

to install any app , unpack it to some folder (usualy /home) and open the terminal (programs->applications)
and type 
```

sudo su
```

to get superuser privileges

then 

```
cd /home/nameofyourprogram
```

to open dir

then

```
./configure
./install
```

and app will install if there is install script

hope i helped:lolflag:

also if that is kind of confusing just go to the file where you saved the wall paper, icon, theme (etc) and go to the file menu and click on open terminal then it is basically the same.

---

### Post by Joeb454 on 2007-12-20
I'm sure that for icons and themes you open System > Preferences > Appearance

And then you can either drag and drop the theme or icon set into there, or click install :)

---

### Post by chips24 on 2007-12-20
cd [location]
./configure
make
make install
make clean

for cd you can click and drag the folder into the terminal after you extracted it.

---

### Post by kokomonjo on 2007-12-20
Case Closed! Thanks Guys! Figured it out, hopefully oneday i can help someone

---

### Post by asmiller-ke6seh on 2007-12-20
Please remember to mark the thread SOLVED when done.

---


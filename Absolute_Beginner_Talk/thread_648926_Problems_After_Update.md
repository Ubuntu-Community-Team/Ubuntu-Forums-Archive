---
title: "Problems After Update"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by thomas.hoyland on 2007-12-24
Hi People,
I did a fresh install of gutsy using the alternate cd.
all goes well, install apps once up and running and then attempt an update

updates go through, then when i start up the machine i get my login screen,
enter credentials and login

login screen disapears and desktop almost appears.
i see the desk bars appear for a second but then they flicker and disapear.
im left with a blank screen and a cursor

i can get into terminal, but nothing else

ive tried reinstalling GDM but to no avail.

Any help?

Regards,
Tom

---

### Post by thomas.hoyland on 2007-12-24
bump

---

### Post by PmDematagoda on 2007-12-24
Not a real solution, but try using another DE like KDE or Xfce:-

install KDE using:-
```
sudo aptitude install kubuntu-desktop
```
install xfce using:-
```
sudo aptitude install xubuntu-desktop
```
After either KDE or Xfce is installed, you can run one of them by going to Sessions in the login screen.

---

### Post by blueridgedog on 2007-12-24
Well, I would try and kill the X server with CTR+ALT+Backspace.  

Look for errors in the terminal that might be a clue and try and start X again with startx.

---

### Post by SOULRiDER on 2007-12-24
I suggest you try reinstalling ubuntu desktop first.
```
sudo aptitude update
sudo aptitude dist-upgrade
sudo aptitude install ubuntu-desktop
```

---

### Post by thomas.hoyland on 2007-12-24
ive already tried a ubuntu desktop reinstall and im not after using another desktop manager, im after ubuntu.

this happened just after the update i did, do you or anyone else know of a workaround?

Regards.
Tom

---

### Post by PmDematagoda on 2007-12-24
Try clearing your configuration files:-

```
rm -rf ~/.gnome
rm -rf ~/.gnome2
```

---

### Post by thomas.hoyland on 2007-12-24
nope, that rm hasnt helped matters at all

when i login, the bars appear, but then flicker and vanish!! (spooky) lol

---

### Post by PmDematagoda on 2007-12-24
Well, I am sorry, but I cannot help you further than installing another DE, I do hope you will find a solution to your problem.

---

### Post by bumanie on 2007-12-24
This may be off track completely, but what sort of video card do you have?

---

### Post by thomas.hoyland on 2007-12-24
a nice old radeon 9550, lol

---

### Post by Croathack on 2007-12-25
I have same problem. Yesterday I installed Ubuntu 7.10 and all new updates. After I restart my computer, something go wrong... Now I can use lower resoulution and refresh rate, and yes I have too problem with login manager... :(

---


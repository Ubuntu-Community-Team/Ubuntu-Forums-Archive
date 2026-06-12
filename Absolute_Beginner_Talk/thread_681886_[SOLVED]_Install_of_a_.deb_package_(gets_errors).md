---
title: "[SOLVED] Install of a .deb package (gets errors)"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Thorun on 2008-01-29
I'm trying to install a program i use at my work (primary windows).
It's called SkoleKom and is a Danish program. 

It's available for Linux too as an .deb package. 
I have found that i could install .deb packages with: sudo dpkg -i package.deb
But i only get errors. I have installed the danish version of Ubuntu v7.10 but i hope that you can understand the errors


```
x1lina@x1lin1:~/Dokumenter$ sudo dpkg -i fcc.deb
Vælger tidligere fravalgt pakke fcc.
(Læser database... 88932 filer og mapper aktuelt installeret.)
Udpakker fcc (fra fcc.deb)...
dpkg: afhængighedsproblemer forhindrer konfiguration af fcc:
 fcc afhænger af libqt3-mt | libqt3c102-mt, men:
  Pakken 'libqt3-mt' er ikke installeret.
  Pakken 'libqt3c102-mt' er ikke installeret.
dpkg: fejl under behandling af fcc (--install):
 afhængighedsproblemer - efterlader den ukonfigureret
Der opstod fejl under behandlingen:
 fcc
x1lina@x1lin1:~/Dokumenter$ 
```

It says something like: the package 'libq3-mt' is not installed
the package 'libqt3c102-mt' is not installed.. 
an error occurred.

Could someone please help me with those errors?
I have a fresh install of Ubuntu v7.10.

---

### Post by emarkd on 2008-01-29
Open System > Administration > Synaptic and search for the missing software to install it.

---

### Post by FuturePilot on 2008-01-29
```
sudo apt-get install -f
```
Will install missing dependencies. That's one of the problems with installing using dpkg, it doesn't handle dependencies.

---

### Post by stump138 on 2008-01-29
try this
```
sudo apt-get install libqt3-mt
```
then you can try and re-install the .deb package.

---

### Post by Thorun on 2008-01-29
I'm sorry to tell, that no one of the 3 solutions above worked. 

Synaptic doesn't have the libqt3-mt files

Install -f didn't do anything:
```
x1lina@x1lin1:~/Dokumenter$ sudo apt-get install -f
Indlæser pakkelisterne... Færdig
Opbygger afhængighedstræ        
Reading state information... Færdig
0 opgraderes, 0 nyinstalleres, 0 afinstalleres og 0 opgraderes ikke.
x1lina@x1lin1:~/Dokumenter$ 

```

and the last one didn't work either. 
"Couldn't find the package". 
```
x1lina@x1lin1:~/Dokumenter$ sudo apt-get install -f
Indlæser pakkelisterne... Færdig
Opbygger afhængighedstræ        
Reading state information... Færdig
0 opgraderes, 0 nyinstalleres, 0 afinstalleres og 0 opgraderes ikke.
x1lina@x1lin1:~/Dokumenter$ 
```


If it would help you (or me) if i have installed an US-version of Ubuntu v7.10 i could do that. I just did the Danish install for fun - to see how well the Danish language was integrated in ubuntu.

---

### Post by emarkd on 2008-01-29
The package is in Synaptic.  Do you have all of the extra repositories enabled?  From Synaptic, click Settings, Repositories and check Everything except Source.  Save and hit Reload.  Then search again.

---

### Post by Thorun on 2008-01-29
Now I've got it installed. :)

I did check everything except the system-stuff in synaptic. And suddenly there was a lot more packages - and the missing one too. I installed it, installed my fcc.deb package and the program was installed in less than 2 seconds. 

I will give a really big thank-you to you all to help me out. I like this ubuntu-forum very much! As a new linux-user (have used it on and off for 3 months now) it's really great that you guys/girls is answering approxamitely  all questions almost instantaneous. 

Keep up the spirit. And thank you again for the really fast and helpfull replys.

/Rune
Denmark.

---

### Post by emarkd on 2008-01-29
You're welcome.  Glad we could help.

---

### Post by polmir on 2008-01-29
This is old stable Debian package:
[http://packages.debian.org/libqt3c102-mt]("http://packages.debian.org/libqt3c102-mt")
[http://download.gna.org/pdbv/demo_html/demo_2.0.10/package/libqt3c102-mt_3:3.3.3-8.html]("http://download.gna.org/pdbv/demo_html/demo_2.0.10/package/libqt3c102-mt_3:3.3.3-8.html")

---

### Post by bromatt on 2008-01-31
Just wanted to thank you for solving my problem also.  I just installed ubuntu today and am loving it!

---


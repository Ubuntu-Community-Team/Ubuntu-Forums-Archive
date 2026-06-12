---
title: "Wine Step By Step Install"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by Cooleo on 2006-04-08
I am a linux newbie. Has anyone got clear step by step instructions on how to install WINE? as I still want to use some windows programs.*I dont have an internet connection,So its been downloaded*

Cooleo

---

### Post by mostwanted on 2006-04-08
Erhm. I don't know. I just installed it through apt-get.
```
apt-get install wine 
```
That's it.

If you don't have an Internet connection (not really ideal with Linux), I guess you could download the wine package DEB-file along with dependencies and then install them with ```
dkpg -i nameofpackage1.deb nameofpackage2.deb .... and so on
```

When you want to run it, you just do a 
```
wine /path/to/appname.exe
```
in the terminal.

Don't you have an Internet connection in general or doesn't it work with your linux box?

---

### Post by Cooleo on 2006-04-08
I have an internet connection,I have an WIFI enabled house :P but i cant afford to buy a reciever yet.Im currently on my spare XP machine. Ive only found one WINE .deb file called "wine_0.9.11~winehq1-1_i386.deb" Where should i put this on my computer? and would i load it like "dkpg -i wine_0.9.11~winehq1-1_i386.deb"

---

### Post by izmaelis on 2006-04-08
Is it hard to use a forum search? You can find loads of useful stuff there. For example this fine wine installation [how-to]("http://www.ubuntuforums.org/showthread.php?t=149585").
I hope it will help!

---

### Post by Cooleo on 2006-04-08
It comes up with Errors:
Failed to write to pipe in copy
Subprocess paste returned error exit status 2

Whats wrong with it?

---

### Post by sands on 2006-04-08
install it thru synaptic package manager..
If u do not find it in the list..then open synaptic
settings->repositories
There u can add wine repository
click add and then enter this

type: binary
uri: [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/)
distribution: binary/


After this hit reload button and u can see wine in the package list..
then install it..

---

### Post by Cooleo on 2006-04-08
I dont have the internet on my machine,and i cant add repostiories.

---


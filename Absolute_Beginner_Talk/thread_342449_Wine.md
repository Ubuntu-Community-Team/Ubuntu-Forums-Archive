---
title: "Wine"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-01-20
I wanna have a complete newbie guide to wine.
I have its deb file, i have installed, now what next?

---

### Post by energiya on 2007-01-20
after installing using
```

sudo dpkg -i wine*.deb

```
try running in a terminal
```

winecfg

```
to setup wine for your needs.

To use it, simply cd to the directory in wich you have a program, and
```

wine program_name.exe

```
or you can make a launcher and use
```

wine "path/to/file.exe"

```
as the command.

---

### Post by jared234 on 2007-01-20
im using ubuntu efty and when try to install wine it tells me: "dependency is not satisfiable" libartsc0.  how am doing this wrong?

---

### Post by energiya on 2007-01-20
> **jared234 said:**
> im using ubuntu efty and when try to install wine it tells me: "dependency is not satisfiable" libartsc0.  how am doing this wrong?
libartsc0 is "aRts sound system C support library"
try
```

sudo aptitude install libartsc0

``` and then installing wine again.

---

### Post by jared234 on 2007-01-20
it said: "no candidate version found for libartsc0"

The wine version is: wine_0.9.29~winehq0~ubuntu~6.10-1_i386.deb

---

### Post by dorcssa on 2007-01-20
Why don't you install it trough synaptic? ```
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
``` Just put this line into your sources.list by typing into terminal ```
sudo gedit /etc/apt/sources.list
``` Then update, and now you can install it by synaptic.

---

### Post by jared234 on 2007-01-20
that is a great question. behind me is my linux box. i dont have internet on it, and i dont understand the APT line.  I was reading some of this: [http://beans.seartipy.com/2006/11/03/simple-way-to-update-ubuntu-edgy-with-slowno-internet-connection/](http://beans.seartipy.com/2006/11/03/simple-way-to-update-ubuntu-edgy-with-slowno-internet-connection/)

in hopes of finding an answer. any suggestions would be really appreciated, i want to break from windows

---

### Post by YokoZar on 2007-01-23
It's possible you didn't install Wine right.

Follow the (JUST UPDATED) instructions here to get all the dependencies using APT:

[http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

---


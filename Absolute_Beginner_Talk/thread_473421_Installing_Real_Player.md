---
title: "Installing Real Player"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by MacScotland on 2007-06-14
Just downloaded the .bin file for Real Player to my desktop.

What do I do with it now?

---

### Post by spin2cool on 2007-06-14
make it executable 'chmod +x filename', then run it:  ./filename

Alternately, you can install realplayer with automatix (getautomatix.com)

---

### Post by wieman01 on 2007-06-14
You need to execute it but before you do so, you probably need to change the permission in order to be able to execute it:
> sudo chmod +x [COLOR="Red"]your_file.bin[/COLOR]
> sudo [COLOR="Red"]./your_file.bin[/COLOR]
Do you know how to use the command line?

---

### Post by FuturePilot on 2007-06-14
You could also add ```
deb http://archive.canonical.com/ubuntu feisty-commercial main
```to your sources list. Then ```
sudo apt-get update
```
and finally ```
sudo apt-get install realplayer
```

---

### Post by wieman01 on 2007-06-14
> **FuturePilot said:**
> You could also add ```
deb http://archive.canonical.com/ubuntu feisty-commercial main
```to your sources list. Then ```
sudo apt-get update
```
and finally ```
sudo apt-get install realplayer
```
That's what I would probably do. :-) Nice & clean.

---

### Post by vancheese on 2007-09-15
btw Its now 

sudo apt-get install realplay

---


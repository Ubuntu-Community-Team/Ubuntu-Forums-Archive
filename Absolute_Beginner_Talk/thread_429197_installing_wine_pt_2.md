---
title: "installing wine pt 2"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by thelegionnaire on 2007-05-01
so someone told me to paste this:


sudo dpkg --force-architecture -i wine_0.9.36~winehq0~ubuntu~*insert ubuntu version here*-1_i386


into the terminal, but i dont know what to put where it says *insert ubuntu version here* im using fesity, will someone help me out?

---

### Post by nanotube on 2007-05-01
to install latest wine, just add the following lines to your /etc/apt/sources.list:

```
# WineHQ repositories
deb http://wine.budgetdedicated.com/apt dapper main
deb-src http://wine.budgetdedicated.com/apt dapper main

```

(replace dapper with whatever ubuntu version you are running, of course.)

then, just run updates in your favorite package manager (e.g. synaptic), and you can install the latest wine from there.

---

### Post by koconnor100 on 2007-05-01
Silly Rabbit. Command line is for kids !

Go to the Applications Menu at the top right of your screen.
Bottom Entry is Add / Remove
It's defaulted to "All"
Do a search on "Wine"

Put a check mark beside wine when it shows up
Enter your super user password
Watch the pretty blinking lights.

---

### Post by teddybairs1 on 2007-05-01
now now, the cli does have it's uses; but it is easier to just head into synaptic and check off the box. If you want the latest version though head to [http://wine.budgetdedicated.com/apt/pool/main/w/wine/](http://wine.budgetdedicated.com/apt/pool/main/w/wine/) and select your wine version from the list to download. Download it to your desktop and then right click to open it with the Gdebi package installer or the Kubuntu package manager (whichever is default), and then follow the instructions.

---

### Post by hyperair on 2007-05-01
It all boils down to user preference. I use a mixture of GUI and terminal, whichever is faster. I tend to love the terminal though, even in Windows due to an above average typing speed. ^^

---


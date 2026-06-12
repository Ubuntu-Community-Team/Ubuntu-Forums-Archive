---
title: "wine wont install"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by Nolander on 2007-03-29
im trying to install wine but i cant find libartsc0. its knowere. can someone plz tell me were it is.

ta,
nolander.

---

### Post by houstonbofh on 2007-03-29
Unless you need to compile it for some reason, just install it from the WineHQ repositories.
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by NicoleM on 2007-03-29
all you need to install it is 3 lines
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list -O /etc/apt/sources.list.d/winehq.list
```
then 
```
sudo apt-get update
```
then
```
sudo apt-get install wine
```
this worked for me...getting my games to work to my satisfaction was a whole new issue altogether, but installing was relatively straightforward

---

### Post by Nolander on 2007-03-29
ive done that it tells me:
```

The following packages have unmet dependencies:
  wine: Depends: libartsc0 (>= 1.5.0-1) but it is not installable
E: Broken packages
```

i checked [http://packages.ubuntu.com/](http://packages.ubuntu.com/) 

i cant find it nor can synaptic package manager

ta,
nolander.

---

### Post by EliteHacker on 2007-03-29
Hey there I'm verry new to linux and ubuntu and currently I'm jumping from one platform to another i.e. instaling ubuntu and uninstaling windows and visa versa any way I downloaded wine but what do I do next I tryid to read documentation but it wont work nor guide help so is there step by step guide or anyone can explain how to do it exactly?!

Thanx in Advance...

---

### Post by david_kt on 2007-03-29
> **Nolander said:**
> ive done that it tells me:
```

The following packages have unmet dependencies:
  wine: Depends: libartsc0 (>= 1.5.0-1) but it is not installable
E: Broken packages
```


Try below 3 lines, one at a time:

[PHP]sudo apt-get update
sudo apt-get upgrade
sudo apt-get install wine[/PHP]

If still could not install, open synaptic. On the menu, choose:
 edit>Fix broken packages

After that, once again try to install wine, either from synaptic or from terminal.

DK

---

### Post by Nolander on 2007-03-29
Elite hacker,

there is a guide on ubuntu wiki. get it out.

Nolander.

---

### Post by david_kt on 2007-03-29
> **EliteHacker said:**
> Hey there I'm verry new to linux and ubuntu and currently I'm jumping from one platform to another i.e. instaling ubuntu and uninstaling windows and visa versa any way I downloaded wine but what do I do next I tryid to read documentation but it wont work nor guide help so is there step by step guide or anyone can explain how to do it exactly?!

Thanx in Advance...

What package did you downloaded? I suggest you open synaptic:
System>Administration>synaptic package manager

and then on the menu:

setting>repositories

enable all repositories. But you could disable all cd rom support so that you do not need to keep your CD in CD ROM all the time.

After that click reload. After reload, select wine, and apply.

If everything ok, you will have wine in your system. To use wine, open terminal and type:

[INDENT]wine your_program.exe[/INDENT]

Please take not that you have to be on the same folder, other wise give full path to your program. For example, if you copy your program on your Desktop, then you must go to your dekstop after open terminal:

[INDENT]cd Desktop[/INDENT]
[INDENT]wine your_program.exe[/INDENT]

You can also try to open nautilus, go to the folder of your program, and then right click and choose to run with wine.

DK

---


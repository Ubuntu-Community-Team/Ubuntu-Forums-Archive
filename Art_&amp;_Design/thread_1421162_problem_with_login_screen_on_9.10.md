---
title: "problem with login screen on 9.10"
date: 2010-03-03
forum: Art &amp; Design
---

### Post by beliyyal on 2010-03-03
I recently upgraded from ubuntu 8.04 to 9.10, and now the login screen says xubuntu. it is indeed ubuntu 9.10, but it says xubuntu at the login screen and loading screen. Does anyone have an idea of how to fix this?

---

### Post by s.fox on 2010-03-04
Hello,

I think [this]("http://ubuntuforums.org/showpost.php?p=8518766&postcount=6") post should be of help to you.

-Silver Fox

---

### Post by beliyyal on 2010-03-05
> **Silver_fox_ said:**
> Hello,

I think [this]("http://ubuntuforums.org/showpost.php?p=8518766&postcount=6") post should be of help to you.

-Silver Fox
Well, that changed the background image, but it didn't change the loading screen or the symbol. It's still xubuntu. But thanks anyways.

---

### Post by 23dornot23d on 2010-03-05
You could add Ubuntu-Studio .... that changes the full startup look plus the login scree ,,,,,

Its in the Synaptic Package Manager .....

---

### Post by beliyyal on 2010-03-05
> **23dornot23d said:**
> You could add Ubuntu-Studio .... that changes the full startup look plus the login scree ,,,,,

Its in the Synaptic Package Manager .....

[IMG]http://img638.imageshack.us/img638/5143/screenshotlv.png[/IMG]

I'm afraid that doesn't do much....

---

### Post by 23dornot23d on 2010-03-06
You seem to have just loaded in part of it the controls .........

There is a full package is either called **ubuntustudio-desktop or ****ubuntustudio-graphics**

It changes the full look though .... I hope it's what you want ........ 

[http://i49.tinypic.com/34gke1e.jpg](http://i49.tinypic.com/34gke1e.jpg)

---

### Post by nerdy_kid on 2010-03-06
i dont see what this issue has to do with ubuntustudio...

try
```

sudo apt-get install ubuntu-desktop
sudo apt-get autoremove

```

if that doesnt work:

```

sudo dpkg-reconfigure gdm

```
select gdm at the dialog.

---

### Post by beliyyal on 2010-03-06
> **nerdy_kid said:**
> i dont see what this issue has to do with ubuntustudio...

try
```

sudo apt-get install ubuntu-desktop
sudo apt-get autoremove

```

if that doesnt work:

```

sudo dpkg-reconfigure gdm

```
select gdm at the dialog.


```
sudo dpkg-reconfigure gdm
```

This doesn't open a dialog, and the other commands didn't change it. It still says xubuntu at the loading screen during boot up. Also, at the login screen, the symbol is the xubuntu symbol.

---

### Post by nerdy_kid on 2010-03-07
> **beliyyal said:**
> ```
sudo dpkg-reconfigure gdm
```

This doesn't open a dialog, and the other commands didn't change it. It still says xubuntu at the loading screen during boot up. Also, at the login screen, the symbol is the xubuntu symbol.

the dialog is inside the terminal.  the terminal should turn all blue with a box and ask you to select default display manager.

---

### Post by beliyyal on 2010-03-07
> **nerdy_kid said:**
> the dialog is inside the terminal.  the terminal should turn all blue with a box and ask you to select default display manager.

It just went back to ```
root@Astaroth
``` But I got it fixed. I just went into synaptic and removed the xubuntu GDM theme and a few other xubuntu packages. But thanks to everyone for your help.

---

### Post by nerdy_kid on 2010-03-07
glad you got it fixed!  sorry about that, i thought you were using karmic (didnt see your sig) and its gdm doesnt have theming support, so i figured you mustve switched display managers.

---


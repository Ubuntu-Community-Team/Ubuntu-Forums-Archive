---
title: "Application execution problem"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by greatdeadeye on 2007-03-02
When I download something off the internet, I can't actually install it after I download it. So far I've tried aMSN and some linux NVidea drivers for my graphics card. Below is a link to a screenshot of my problem.

[http://i30.photobucket.com/albums/c318/Malaran/Screenshot.png]("http://i30.photobucket.com/albums/c318/Malaran/Screenshot.png")

Any help would be appreciated :D

---

### Post by mikewhatever on 2007-03-02
You are trying to open the amsn installation package with gedit editor, as if it was a text document. I'll search for instructions on how to install amsn in a sec, but here is a good overview [http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

### Post by joselin on 2007-03-02
To install amsn just type the following:

```
sudo apt-get install amsn
```When the installation finish you will have a new shortcut on internet menu.

---

### Post by steven8 on 2007-03-02
> **joselin said:**
> To install amsn just type the following:

```
sudo apt-get install amsn
```When the installation finish you will have a new shortcut on internet menu.

You may want to use:

```
sudo aptitude install amsn
```

Aptitude handles dependencies more efficiently and makes removal of a program more complete.  If you ever want ot remove the program that is. :)

That would be:

```
sudo aptitude remove amsn
```

---

### Post by mikewhatever on 2007-03-02
Right, I don't know why download stuff if amsn is in the repositories. You can install it through Applications->Add/Remove Programs, see the screenshot.
For nvidia drivers, I'd recommend envy [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---


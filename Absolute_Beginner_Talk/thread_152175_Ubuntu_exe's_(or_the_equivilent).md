---
title: "Ubuntu exe's (or the equivilent)"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by fionn on 2006-03-29
I have a dial up conection to the internet and would like to install WINE and Amarok.

Everywhere I've searched (eg: WINE & Ubuntu wiki's) say to add them to the repository which will then (presumably) download them

However, on my connection this would take forever. Is there an equivilent I can download in work (where I can access) broadband and install them

If so, where do I get them from as all I could find was information on adding them to repositories, and secondly how are they installed

Any help would be appreciated

---

### Post by endersshadow on 2006-03-29
[http://wine.sourceforge.net/apt/binary/](http://wine.sourceforge.net/apt/binary/)

You can grab them here.  Grab all of them, bring them home, open up the folder where they are in, and (assuming they are the only .deb files in that folder):

```
sudo dpkg -i *.deb
```

Hope this helps!

---

### Post by hentaidan on 2006-03-29
Go to [http://packages.ubuntu.com/]("http://packages.ubuntu.com/"), and search for the packages you are after. Its a web interface to the repositories, so it's all official.

Some packages require others to be downloaded as well (dependencies - with red bullets next to them), so you will need to get those as well.

Then install as endersshadow suggested.

---

### Post by aysiu on 2006-03-29
An [Add-On CD](http://www.ubuntuforums.org/showthread.php?t=136955) will surely serve you better.

---

### Post by fionn on 2006-03-30
Thanks for the help - seems so simple when it's pointed out!!!!!

---


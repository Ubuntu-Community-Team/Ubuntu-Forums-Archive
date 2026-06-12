---
title: "New Edubuntu programs"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by Ceinstein on 2006-05-07
Where can I get new Edubuntu open-source software.  Especially the one enabling you to watch dvd's   PLEASE HELP!!!:confused:

---

### Post by ubuntu27 on 2006-05-07
[QUOTE=Ceinstein]Where can I get new Edubuntu open-source software. [/QUOTE]

Ahh, [Edubuntu](http://www.edubuntu.org/) is Ubuntu with Educational packages preinstalled. 

You can get Edubuntu at [http://www.edubuntu.org/](http://www.edubuntu.org/)

[QUOTE=Ceinstein]Especially the one enabling you to watch dvd's   PLEASE HELP!!!:confused:[/QUOTE]

In either Ubuntu Breezy Badger or Edubuntu Breezy Badger:

Open the_ terminal _ which is located at "Applications" menu/Accesories/Terminal

and type the following [you can copy and paste too!]:

```
 sudo apt-get install libdvdread3 
```

then:

```
 sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```

---


---
title: "Changed from Kubuntu to Ubuntu."
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by Rackerz on 2005-12-14
Well i changed seeing as Gnome suited my computer a little better thab KDE did. So i have a few questions;

1. I have installed the Sun Java package but i cannot seem to get my browsers to locate it. How would i go about doing that?

2. Kopete, how would i get the latest version and install it? Would i need to get the correct libraries or will it tell me they are missing?

Thanks!

---

### Post by carlosqueso on 2005-12-14
1. [http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-java](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-java) worked for me.  I don't know if it'll work for you.

2.  You should be able to go into a terminal and type ```
sudo apt-get install kopete
```, but have you tried gaim?  I've tried both, and gaim seems to be a bit more cooperative on my comp.

---

### Post by Kyral on 2005-12-14
Java should be in the same place...

As for Kopete, I don't know what the latest version is but you should be able to install it with ```
sudo apt-get install kopete
```

---

### Post by NotJustANewbie on 2005-12-14
For JRE, add these two lines to your sources.list:
```
deb http://ftp.debian-unofficial.org/debian sarge main contrib non-free restricted
deb-src http://ftp.debian-unofficial.org/debian sarge main contrib non-free restricted
```

and:
```
sudo apt-get install sun-j2se5.0-jre-binary
```

Worked for me!

---

### Post by Rackerz on 2005-12-14
Ok installing kopete worked, thanks :). But i don't know were to direct my browsers too for finding the java plugin. In KDE i had to find the folder it was in and tell my browser, but i've forgotten.

---

### Post by carlosqueso on 2005-12-14
If you follow the starter-guide howto, firefox should be able to find it.

---


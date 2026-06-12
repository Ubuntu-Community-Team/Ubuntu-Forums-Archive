---
title: "Limewire Question"
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by hobnobsandtea on 2005-12-09
Hi Guys!

want to install limewire on ubuntu ...  how do I do it, also, will it run?  i presume it would since its written in java and the JVM and all that.

-thanks

---

### Post by bored2k on 2005-12-09
[list=1][*]Open up a terminal window and type the following:
```
wget http://packages.freecontrib.org/ubuntu/plf/pool/non-free/java/sun-j2re1.5_1.5.0%2bupdate05_i386.deb -c
```

After the 30MB download is done, do the following:
```
sudo dpkg -i *.deb
```

Enter your password, and now you have Java installed.

[*]Download Limewire from their website (the source file or the RPM, preferably the RPM).

[*]If you downloaded the packaged Limewire (.zip or .tar.gz I believe), unpack and run runLime.sh by double clicking on it on your file browser and selecting Run from the new menu. 

[*]If you downloaded the RPM.
```
sudo apt-get install alien
```
```
sudo alien -d *.rpm
```
Now you can install Limewire with
```
sudo dpkg -i limewire*whatever*.deb
```[/list]

---

### Post by canadianwriterman on 2005-12-09
You can also install LimeWire with Automatix, which I believe is now available again (search Forum for Automatix). That's what I used and LimeWire works great!

---

### Post by hobnobsandtea on 2005-12-09
thanks guys thats great stuff !

---

### Post by bored2k on 2005-12-09
Indeed. Automatix is better. Just happened to forget about it for a sec :-s.

---

### Post by nitricacid on 2005-12-09
YOu can check out this HOW-To i made for installing limewire from an RPM file aswell.
[http://ubuntuforums.org/showthread.php?t=97334&highlight=limewire+how-to](http://ubuntuforums.org/showthread.php?t=97334&highlight=limewire+how-to)

---

### Post by bored2k on 2005-12-09
This is what makes this community so good. Every has their own easy and willing to share method to do things :D.

---


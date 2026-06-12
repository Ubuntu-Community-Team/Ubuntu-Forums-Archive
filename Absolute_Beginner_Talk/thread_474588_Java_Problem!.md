---
title: "Java Problem!"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by virtualani on 2007-06-15
Hi all. Im runnin feisty, 7.04. Im findng that java applets are having all kinds of problems loading and if they do, its very slow and 'lumpy'. Its the same on Firefox & epiphany browsers

Ive been to the synaptics package manager and installed everything i can see to do with java runtime. but still its the same.

can anyone help??

---

### Post by Kobalt on 2007-06-15
Hello,

If you installed many java related packages you may have installed old and new version of Java. And so, you may be using an old one instead of a new one, even though you have both installed. The newest packages you need to keep are *sun-java6-jre* and *sun-java6-plugin*. To list the installed JVM use ```
update-java-alternatives -l
```And to use a particular one if you have more than one installed enter for example ```
sudo update-java-alternatives -s java-1.6.0-sun
```

---

### Post by virtualani on 2007-06-15
hi, thanx 4 ur reply. This is the termial msg. I just dont understand!!

andi@rainbow:~$ update-java-alternatives -l
java-1.5.0-sun 53 /usr/lib/jvm/java-1.5.0-sun
java-6-sun 63 /usr/lib/jvm/java-6-sun
java-gcj 1041 /usr/lib/jvm/java-gcj
andi@rainbow:~$ udo update-java-alternatives -s java-1.6.0-sun
The program 'udo' is currently not installed.  You can install it by typing:
sudo apt-get install udo
Make sure you have the 'universe' component enabled
bash: udo: command not found
andi@rainbow:~$

---

### Post by virtualani on 2007-06-15
, do i need to find and uninstall all the old java stuff?

---

### Post by Gwasanaethau on 2007-06-15
> **virtualani said:**
> hi, thanx 4 ur reply. This is the termial msg. I just dont understand!!

andi@rainbow:~$ update-java-alternatives -l
java-1.5.0-sun 53 /usr/lib/jvm/java-1.5.0-sun
java-6-sun 63 /usr/lib/jvm/java-6-sun
java-gcj 1041 /usr/lib/jvm/java-gcj
andi@rainbow:~$ udo update-java-alternatives -s java-1.6.0-sun
The program 'udo' is currently not installed.  You can install it by typing:
sudo apt-get install udo
Make sure you have the 'universe' component enabled
bash: udo: command not found
andi@rainbow:~$

It looks like you missed the first 's' off the second command, that's all. It looks like it should have been:
```
sudo update-java-alternatives -s java-1.6.0-sun
```
(Apologies Kobalt if I jumped in there a bit;)).

---

### Post by Kobalt on 2007-06-15
> **Gwasanaethau said:**
> (Apologies Kobalt if I jumped in there a bit;)).
You're very welcome my Dubliner friend :)

---

### Post by virtualani on 2007-06-15
oh lore! now what hav i done!


andi@rainbow:~$ sudo update-java-alternatives -s java-1.6.0-sun
Password:
update-java-alternatives: directory does not exist: /usr/lib/jvm/java-1.6.0-sun
andi@rainbow:~$ sudo apt-get install udo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gnome-icon-theme-gartoon kwin-style-crystal
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  udo
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
andi@rainbow:~$ sudo apt-get install udo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gnome-icon-theme-gartoon kwin-style-crystal
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  udo
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 177kB of archives.
After unpacking 532kB of additional disk space will be used.
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe udo 6.4.1-1 [177kB]
Fetched 177kB in 0s (183kB/s)
Selecting previously deselected package udo.
(Reading database ... 167176 files and directories currently installed.)
Unpacking udo (from .../archives/udo_6.4.1-1_i386.deb) ...
Setting up udo (6.4.1-1) ...
andi@rainbow:~$ sudo update-java-alternatives -s java-1.6.0-sun
update-java-alternatives: directory does not exist: /usr/lib/jvm/java-1.6.0-sun
andi@rainbow:~$

---

### Post by Kobalt on 2007-06-15
> **virtualani said:**
> , do i need to find and uninstall all the old java stuff?
Yes, you should remove anything but sun-java6 I think, and then retry to open your website...

---

### Post by virtualani on 2007-06-15
so, ive tried many things, been baffled with all of them! i tho i feel im nearly there.

ive had java verify my java install, and although i think id unistalled the old stuff, they say its still out of date! So, ive downloaded the new jre 6...bin. now what do i do!? iv printed off the instructions. i cant get passed typing: su. it says it cant authenticate me. Im a real real beginner, and i cant face goin back 2 the darkside! someone please explain like they were talkin 2 a 6 year old please! (no offence, 6 yr olds!)

---

### Post by Gwasanaethau on 2007-06-15
Hmm - I think you might need to uninstall anything Java related and then install Java 6 from scratch. From the code you provided from the commands earlier you might want to try:
```
sudo apt-get remove java-common java-gcj-compat libgcj7-jar fastjar
```
to remove all the Java stuff, then:
```
sudo apt-get install sun-java6-jre
```
to reinstall Java 6 from the repositories (it'll probably work better, not to mention easier to install, than the '.bin' file you got from the website).
If you want to check it, you can try the command:
```
update-java-alternatives -l
```
again to see what Java modules are installed. Hopefully (fingers crossed) it'll just say 'java-6-sun 63 /usr/lib/jvm/java-6-sun' (like it did before without all the extra bits).

I hope that works for you now! ;)

> **Kobalt said:**
> You're very welcome my Dubliner friend :)

Yey! Someone who knows what my banner means! :D

---


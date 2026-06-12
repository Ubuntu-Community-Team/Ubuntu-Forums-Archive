---
title: "So many beryl problems"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by CorranSW on 2007-03-19
I recently setup a dual boot with ubuntu and windows, realy i got ubuntu for 2 reasons. 1-I wanted to try linux, 2-Beryl. Now i read a couple tutorials about installing beryl, well i installed beryl, downloaded the correct nvidia drivers. But i cant enable them because terminal doesent seem to display the file when i try to access and edit Xorg through it. Also if i try to use text editor to enable the drivers it wont give me permission to, i know my password but text editor doesent let me log in as super admin. Well i have spent a couple days trouble shooting but nothing seems to work please somone help me, if anyone in here has ventrilo, it would be alot easier for somone to explain it to me by talking. My xfire is CorranSW.
Also my system specs are Nvidia 7900GTX, AMD 4800+, 2 gigs of ram, etc....

---

### Post by jbayone on 2007-03-19
How did you install the Nvidia driver?  If you use the Envy script, it will install the drivers and gives you the option to configure xorg for you.

---

### Post by CorranSW on 2007-03-19
i used envy and i am pretty sure i ticked the box to automatically configure Xorg

---

### Post by Waappu on 2007-03-19
Hi

To edit xorg.conf type in terminal
```
gksudo gedit /etc/X11/xorg.conf
```

And you can post that file if someone see problem there

---

### Post by BoredOutOfMyMind on 2007-03-19
CorranW did you try this site for directions?

Worked like a charm for me. 

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)

---

### Post by noob_saioke45601 on 2007-03-19
if you installed beryl correct, it should be in applications>system tools. here's the directions i used to install beryl...

Type in terminal
```
gksudo gedit /etc/apt/sources.list
```

then add this line to the sources.list

```
deb http://ubuntu.beryl-project.org/ edgy main
```

last you must type this into terminal.

```
sudo echo && wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
sudo aptitude update
sudo aptitude install beryl emerald-themes
```

---

### Post by CorranSW on 2007-03-20
Ill go try that but i might mention i just managaged to crash my partiition lol

---


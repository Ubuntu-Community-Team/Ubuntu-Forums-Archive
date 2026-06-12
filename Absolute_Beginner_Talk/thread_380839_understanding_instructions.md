---
title: "understanding instructions"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by heatrag on 2007-03-10
Just a quickie, here are a couple of instructions off the wiki, how do I do execute them please
#

Open the terminal and navigate to the file "RealPlayer10Gold.bin". (Its on the desktop)
#

Verify that the file is executable.

---

### Post by Famicommie on 2007-03-10
What exactly are you having problems with? Opening a terminal? Navigating the directory structure?

---

### Post by bollix47 on 2007-03-10
To open a terminal click on:

Applications - Accessories - Terminal

To navigate to your desktop folder:

```
cd Desktop
```

To make file executable:

```
chmod +x Real*.bin
```

---

### Post by RomeReactor on 2007-03-10
Hi. If you're on Ubuntu Edgy, then [this guide]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Multimedia_Player_.28RealPlayer_10.29") walks you through it; if you're on Dapper, then it's [this page]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Multimedia_Player_.28RealPlayer_10.29")

The guide basically says:

1.- Download [Realplayer's Official Linux Version]("http://www.real.com/linux").

2.- Add execute permissions to the installer and execute it:

```
chmod +x RealPlayer10GOLD.bin
```

3.- Then:

```
sudo ./RealPlayer10GOLD.bin
```

---

### Post by Famicommie on 2007-03-10
If you want to learn how to use the terminal (I highly recommend it, you will find yourself using it all the time)

[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

---

### Post by heatrag on 2007-03-10
I can open the terminal and have given it a few basic instructions but navigating the structure from the terminal I dont have much of a clue about.

---

### Post by Famicommie on 2007-03-10
The link that I posted above has all kinds of information, for instance: [Shell Navigation](http://www.linuxcommand.org/lts0020.php)

;)

---

### Post by heatrag on 2007-03-10
I'll get onto that but for the minuet I'm installing and don't know the path-name where I should put plugins. It would appear the default is the desktop.

---

### Post by heatrag on 2007-03-12
Thanks for the above. The recomendation of [http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php) was most valuable. It was like trying to drive a car without knowing you had to start the engine my trying to use linux befor this.

---


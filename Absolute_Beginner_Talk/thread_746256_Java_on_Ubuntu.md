---
title: "Java on Ubuntu"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by HaemoLacria on 2008-04-05
I am attempting to install Sun Java 5.0 Plugin with Add/Remove Application.
But when it's finished how can I for example make browser games like RuneScape work?

---

### Post by superprash2003 on 2008-04-05
if any webpage requires a java plugin, firefox would automatically detect it and would ask you to install the java plugin.. once you install it, you should restart your browser and it should work

---

### Post by ghost_ryder35 on 2008-04-05
:confused:  they should work after the plugin is installed

---

### Post by HaemoLacria on 2008-04-05
it can't load the aplet

---

### Post by tubasoldier on 2008-04-05
Are you using Hardy Heron? If this is the case I had issues with the plugin installing into the correct directory.

---

### Post by Inxsible on 2008-04-05
you need to install the java plugin for the browser. Let me find out what the exact package name is.
```
sudo aptitude install sun-java6-jre sun-java6-plugin
``` java 6 is the latest one. If you need 5 for some reason you can just replace it with sun-java5-jre & sun-java5-plugin

You can also try out this link if things still don't work out.

[http://ubuntuforums.org/showthread.php?t=576487&highlight=sun+java+firefox+plugin](http://ubuntuforums.org/showthread.php?t=576487&highlight=sun+java+firefox+plugin)

---

### Post by HaemoLacria on 2008-04-05
'error loading applet' is all I get. I can't change anything

---

### Post by SOULRiDER on 2008-04-05
If youre trying to play runescape make sure you selected the Sun JVM when loading the game. Also, you might need to update the java alternatives. In a terminal run:
```
sudo update-alternatives --config java
```
And select suns JVM.

If you run into any problems just ask.

---

### Post by tubasoldier on 2008-04-05
You still haven't answerd some basic questions that will allow us to help you...
Like which version of Ubuntu do you have? Like I said, if your running Hardy Heron the plugin will not install correctly.

---

### Post by HaemoLacria on 2008-04-05
I have the most recent version of ubuntu.

---

### Post by gandaran on 2008-04-05
> **HaemoLacria said:**
> I have the most recent version of ubuntu.


what do you mean by most recent? 7.10 or 8.04, the 8.04 is still a beta in testing!

another question, 32-bit or 64-bit ubuntu?

---

### Post by Sinkingships7 on 2008-04-05
the following command has always been enough for me to install java:
```
sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
```

---


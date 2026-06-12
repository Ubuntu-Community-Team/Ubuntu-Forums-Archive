---
title: "Installing Java on Ubuntu"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by HcoJustin on 2007-06-06
When I install JDK 6 and JRE 6u1, they install fine, i have the jdk1.6.0 and jre1.6.0_01 folders on my desktop, but when i go to use firefox, i still get the "Install Additional Plugins" and when i go through it, it says It can't install, use the manual install.

If you can help, i would appreciate it.
Thanks,
~Justin

---

### Post by odiseo77 on 2007-06-06
Hi; first, on linux things are not installed just by saving them in a folder. In most of cases, you need packages (in ubuntu .deb packages) that are installed with *dpkg -i packagename.deb* or with *apt-get install packagename* (in this last case, you'll need an active internet connection to download/install the packages). 

So, in order to install the JDK 6 let's do it the easy way (the debian/ubuntu way); open a terminal and type:

```
sudo apt-get install sun-java6-jdk sun-java6-jre sun-java6-plugin
```

After the packages are downloaded and installed, execute:

```
sudo update-alternatives --config java
```

And select the number for Sun JVM at the prompt.

Restart firefox and open a website that requires the java plugin, et voilà!!

Regards.

---

### Post by HcoJustin on 2007-06-06
I Get This.....   I don't know if that is good or not...

[[IMG]http://img123.imageshack.us/img123/295/terminalscreenze5.th.jpg[/IMG]](http://img123.imageshack.us/my.php?image=terminalscreenze5.jpg)

---

### Post by Clay_Banger on 2007-06-06
have you [enabled the extra repositories?]("http://www.psychocats.net/ubuntu/sources")

---

### Post by HcoJustin on 2007-06-06
Not yet....I will right now

---

### Post by NeoLithium on 2007-06-06
A good place to get your java and codecs for multimedia installed is look through [http://www.ubuntuguide.org](http://www.ubuntuguide.org)
It's nice and laid out for many of the common install applications, and you can even just copy and paste the commands into a terminal window :)

---

### Post by HcoJustin on 2007-06-06
Thanks Odiseo77 and Clay_Banger, its installing now
[B]
EDIT:[/B]I get this when i do ```
sudo update-alternatives --config java
```

[[IMG]http://img474.imageshack.us/img474/3149/terminalerrorbf5.th.jpg[/IMG]](http://img474.imageshack.us/my.php?image=terminalerrorbf5.jpg)

**EDIT: EDIT:**FIXED Thank you all for your help

---


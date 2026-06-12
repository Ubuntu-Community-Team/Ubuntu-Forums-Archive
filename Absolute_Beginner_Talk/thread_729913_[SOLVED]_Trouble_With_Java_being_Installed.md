---
title: "[SOLVED] Trouble With Java being Installed"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by gecko113 on 2008-03-20
Well my problem is that i install jre-6-linux-i586.bin and it says thats its installed then i get an error once i open Frostwire..... i have to open it through the terminal and it says i must update JRE1.5X cause i have 1.4 but i looked it up on google and it says to install that i've looked for the plugin for mozilla but it brings me to the same one and i keep installing it but still nothing. Like i have eclipse and i can't run that program either

---

### Post by zerhacke on 2008-03-20
Don't install java with the bin file from Sun.  Use apt-get or Synaptic or whatever package manager you want.  It will do all the work of setting up a new Java version.

---

### Post by gecko113 on 2008-03-20
Like i have done it that way as well and still nothing what should i use the sudo apt-get .......... like i know its like java6-plugin or something like that

---

### Post by gecko113 on 2008-03-20
Like i mean is that it already says i have it installed like here is the JRE i installed
 sun-java6-jre is already the newest version.
sun-java6-jre set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by lswest on 2008-03-20
by the way, you can use ```
apt-cache search [search terms]
``` to search for programs through apt.  Also, you may have old java files installed, which means you'll have to uninstall it with ```
sudo apt-get remove sun-java5-jre
``` (i believe is the package name you'd have installed)

---

### Post by FuturePilot on 2008-03-20
Run
```
sudo update-alternatives --config java
```
and make sure sun-java6 is set as the default. If it isn't, make it default.

---

### Post by billgoldberg on 2008-03-20
Well, this won't help the java problem, but you can use "gtk-gnutella" to download from the gnutella network (same network frostwire uses), it's gtk based, not java based.

---

### Post by gecko113 on 2008-03-20
There are 7 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/bin/cacao
          3    /usr/lib/jvm/java-6-sun/jre/bin/java
*+        4    /usr/lib/j2se/1.4/bin/java
          5    /etc/alternatives/kaffe-system/bin/java
          6    /usr/lib/jvm/java-7-icedtea/jre/bin/java
          7    /usr/bin/java-sablevm
thoses are my 7 options which one should i choose

---

### Post by gecko113 on 2008-03-20
Thanks for all the help the problem have been solved

---

### Post by Diabolis on 2008-03-20
I had always prefer to download java directly from sun. Probably you installed correctly java. The problem is that ubuntu already comes with a java installation, which you already know is the version 1.4.

The operating systems has environment variables, one of them is **PATH**. This variable holds all the executables of your system. So every time you type a command in the terminal, the path variable is used to find the executable. Path uses always the first occurrence of the command that is looking for, thats why even if you install a new version of java it will keep using the old one.

You can change this in you **.bashrc** file which is stored in your home folder, it is hidden so press **ctrl + h** while in you home folder.

This is what I added to the file:
```
JAVAHOME=/home/gaston/jdk1.6.0_03/bin
PATH=$JAVAHOME:$PATH

```

JAVAHOME is a new environment variable that is created and assigned the path to the bin folder of the new installation, you can name it as you want. The use of capital letters in environment variables is not a must, but is a standard.

That will place your new java installation on front of path. Check if it worked by checking the java version with **java --version**

---


---
title: "Frostwire crashing"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by luke949 on 2007-04-12
Hi, I have Ubuntu 6.10  and I just recently installed frostwire. I can get frostwire to start up, but after the splash screen, it would just crash.

When I start Frostwire in the Terminal, I get this :

> ******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)


I have installed java, but it still crashes. Any ideas on how to fix this?
Thanks.

---

### Post by tonyr1988 on 2007-04-12
What method did you use to install Java?

---

### Post by luke949 on 2007-04-12
I followed this guide [http://www.javalobby.org/java/forums/t72809.html](http://www.javalobby.org/java/forums/t72809.html)

---

### Post by Nevis on 2007-04-15
I had that problem too, it appears to have been cured with a Java upgrade. I had 1.5.0.8 and upgraded to 1.6.0.

Check your Java version 
```
java -version
```
Follow [these instructions]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox") to update Java.

---

### Post by Franscisco on 2007-04-16
open the terminal and paste  **sudo update-alternatives --config java**
you will see what are your java options with that, I think Frostwire works with java 1.5 

then, remove Frostwire by pasting **sudo apt-get remove frostwire**

then, paste       [B] wget -c [http://www.users.on.net/~stubby/Fros...0.9-2.i586.deb](http://www.users.on.net/~stubby/Fros...0.9-2.i586.deb)
sudo dpkg -i FrostWire-4.10.9-2.i586.deb[/B]

This should work!

---

### Post by DougieFresh4U on 2007-04-16
> **Franscisco said:**
> open the terminal and paste  **sudo update-alternatives --config java**
you will see what are your java options with that, I think Frostwire works with java 1.5 

then, remove Frostwire by pasting **sudo apt-get remove frostwire**

then, paste       [B] wget -c [http://www.users.on.net/~stubby/Fros...0.9-2.i586.deb](http://www.users.on.net/~stubby/Fros...0.9-2.i586.deb)
sudo dpkg -i FrostWire-4.10.9-2.i586.deb[/B]

This should work!

You might want to check out Frostwire 4.13.1 BETA. It is fabulous, and great features

---


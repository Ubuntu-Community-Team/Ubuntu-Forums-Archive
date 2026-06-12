---
title: "last update killed java"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by buzzmandt on 2008-02-16
the last series of updates killed my java, my kid can't play teagames.com games anymore and yahoo web messenger no longer works.

I tried the following but none of the options works, please help
>  sudo update-alternatives --config java

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
 +        2    /usr/lib/j2se/1.4/bin/java
*         3    /usr/lib/jvm/java-6-sun/jre/bin/java
          4    /usr/bin/gij-4.2
          5    /usr/bin/gij-4.1

Press enter to keep the default[*], or type selection number: 



---

### Post by smartboyathome on 2008-02-16
Try completely removing java from your system using Synaptic, and then installing it again.

---

### Post by buzzmandt on 2008-02-16
didn't work, now when I  sudo update-alternatives --config jav 
it tells me there are no java alternatives........ouch

---

### Post by madjr on 2008-03-18
follow this:

> I don't know about Yahoo games, but it sounds like the same problem I had with Pogo games.First open Synaptic Package manager and remove all 3 of the java packages you have installed.

Go to system -> administration -> software sources and be sure that all extra resources are checked.

Then open a terminal and type:
sudo apt-get install sun-java6-jre sun-java-plugin sun-java-fonts

Reopen Firefox and it should work.

---


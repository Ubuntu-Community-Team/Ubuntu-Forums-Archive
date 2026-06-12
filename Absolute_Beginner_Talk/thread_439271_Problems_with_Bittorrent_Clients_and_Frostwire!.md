---
title: "Problems with Bittorrent Clients and Frostwire!"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by ChrisFodge on 2007-05-10
Hi! ok... first...I downloaded frostwire from their website. Came in a .deb file so easy to install. After I install it and go to run it nothing happens. It says loading Frostwire at for a second(only on the window selector, not a splash screen). Anything that I need to do to get it to work propperly???

And... I installed Azurues to do all my torrent downloading. It runs fine but after about 10 min of downloading all my torrents stop downloading

thats it... Thanks!

---

### Post by starcraft.man on 2007-05-10
Try ktorrent, I dunno what it is with Azureus but I tried for days to get it to run with no luck, maybe the Java program senses its users and stops working for some people :p

I don't know anything about frostwire >.>

Edit: Do remember to forward a port for DHT tracking if you want it.

---

### Post by smartalecks on 2007-05-10
If I'm not mistaken, frostwire and azureus both use java vm

uninstall both and try installing them using synaptic to make sure you have all the dependencies.


but before that start frostwire from the terminal (applications > accessories > terminal > then "$ frostwire" I think, or right click the frostwire icon and hit "run from terminal").
any errors should come out on the terminal, copy and paste them here please.

---

### Post by kbf on 2007-05-10
Hi

I use uTorrent 1.6.1 under wine and it works fast with no problem at all and it is a compact program no big installation.:guitar:

---

### Post by ChrisFodge on 2007-05-10
chris@ubuntu:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
1.4.2-02
OOPS, your java version is too old [java = 1.4.2-02]
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)

That is what i get when i try and run it in terminal. I went to javas website and got the update they said to download but it is a .bin fill and I dont know how to use them

---

### Post by rohan! on 2007-05-10
i'm having exactly the same problem with azureus, it downloads for about 10 minutes (if i'm lucky) and then all transfers come to an abrupt halt.

---

### Post by ChrisFodge on 2007-05-10
I tried that kTorrent and it does work very good

---

### Post by rohan! on 2007-05-10
knowing that azureus is a java dependant program i started poking around, looking for something that might be the problem. sure enough i realised that i was running gij, not actually java, despite having installed all the relevant packages (# apt-get sun-java6-jre sun-java6-plugin sun-java6-fonts)

```
$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)
```
so i ```
sudo update-alternatives --config java 
``` and selected the right one
and now it comes out with
```
$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

```
i restarted azureus and this ***seems*** to have fixed the problem i was having with my downloads starting and then stopping after a few minutes. i have to keep it running for a bit longer to be sure of the claims i'm making, but... :)

---

### Post by ChrisFodge on 2007-05-10
that help with frostwire some what. Now the program starts and you can set up the initial setup then when its time to load the accual program it is just an empty window.

This is what i type in the terminal to set java

> chris@ubuntu:~$ java -version
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

chris@ubuntu:~$ sudo update-alternatives --config java

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
          2    /usr/lib/jvm/java-gcj/jre/bin/java
*+      3    /usr/lib/j2se/1.4/bin/java
          4    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 4
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.

chris@ubuntu:~$ java -version
java version "1.5.0_11"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_11-b03)
Java HotSpot(TM) Client VM (build 1.5.0_11-b03, mixed mode, sharing)


i dont have an option for version 1.6... can that be my problem?

---

### Post by rohan! on 2007-05-10
possibly. which ubuntu dist are you using?

if you're using _feisty_ then it should be downloadable:

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

---


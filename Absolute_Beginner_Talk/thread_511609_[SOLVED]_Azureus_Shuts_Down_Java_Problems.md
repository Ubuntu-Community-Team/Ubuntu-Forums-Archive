---
title: "[SOLVED] Azureus Shuts Down/ Java Problems"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by WarholsGhost on 2007-07-28
So i have obtained the same problem with java as everyone else has with azureus, but i need someone to walk me through fixing it. 

Azureus shuts down after a few seconds, this started to happen after i downloaded the Ubuntu restricted extras (i now removed them to try to solve the problem, but it didn't help)

thank you in advance.

---

### Post by tomcheng76 on 2007-07-28
you could try Azureus alternative like KTorrent
you get Azureus by using Synaptic/ apt-get  or  via [http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php)  ?

---

### Post by WarholsGhost on 2007-07-28
ktorrent hates me and it doesn't save my downloads, i really liked azureus.

i wish bittorrent ran like it does in windows, i was really used to it.

---

### Post by G_force on 2007-07-28
it seems to be an issue with java 1.6.
after it is not shutdown properly it has trouble displaying the error "azuerus was shut down untidily"

The aternative is to download azuerus from their main site and run it out of the folder.
[http://azureus.sourceforge.net/download.php]("http://azureus.sourceforge.net/download.php")

---

### Post by Armman on 2007-07-28
You should download Deluge.

---

### Post by WarholsGhost on 2007-07-28
what is deluge based off of?

EDIT:
i downloaded deluge, i like it.

but will this java problem create any other problems?

---

### Post by Armman on 2007-07-28
Not that I'm aware of.

---

### Post by WarholsGhost on 2007-07-28
well i think this is SOLVED

---

### Post by tomcheng76 on 2007-07-28
just tried deluge, it is great
extreme fast speed  1MiB/s :) (i guess becoz it supports utorrent peer exchange)
its pretty good

---

### Post by cdwhit on 2007-08-12
Not quite solved.  I'm having the same problem with Azureus.  I have not tried downloading from the Azureus site, but I have the identical problem on at least one othe program.  A web editing program called Amarus (?).  Is there a fix for the Java?

---

### Post by Paul133 on 2007-08-12
Sorry to hijack the thread, but are people having problems with Java and Azureus?

---

### Post by swoskow on 2007-08-12
yes - do a search of azureus in the forum and almost all the problems are related to the one described in this thread.

---

### Post by meho_r on 2007-08-12
I've typed in console: **sudo update-alternatives --config java**

And get this: 

```
There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
          2    /usr/lib/jvm/java-6-sun/jre/bin/java
*         3    /usr/lib/jvm/ia32-java-6-sun/jre/bin/java
+         4    /usr/lib/jvm/java-gcj/jre/bin/java
```

(To many Javas? :) ) Azureus doesn't work with alternative 3 (ironically, FrostWire works ONLY with alternative 3). It seems that is veeeery difficult to make all this stuff to work (Azureus and FrostWire). At the end, I tried Transmission torrent client and I must admit that it works a way better than Azureus (it is a little ''spartan'', but it gets the job done ;))

---

### Post by Paul133 on 2007-08-13
Well, I have the latest Azureus and the java 6, installed following these guides: [http://ubuntu1501.blogspot.com/2007/06/feisty-fawn-starter-guide.html](http://ubuntu1501.blogspot.com/2007/06/feisty-fawn-starter-guide.html) I haven't noted any problems yet. Are those the versions that are causing the problems?

---

### Post by meho_r on 2007-08-13
It seems that Java causes all that problems. My Azureus works with Java 6 too, but when I want to use FrostWire, I must switch to ia32-java-sun, which isn't nice nor practical at all :(

---

### Post by Paul133 on 2007-08-13
All right.

---

### Post by jingo811 on 2007-08-14
I didn't have any problems with Azureus during 2 months of testing.  Just last night it started to shut down without notice indefinetely.  Java solutions is bad mojo  [-( I don't like them.

---

### Post by Crube on 2007-08-14
I had the same problem and I found another solution. It seemed to me like the problem was with Azureus. Here's the solution found from [http://languor.us/azureus-unexpected-error-has-been-detected-hotspot-virtual-machine]("http://languor.us/azureus-unexpected-error-has-been-detected-hotspot-virtual-machine")

```
Command line fix:

sudo wget http://superb-west.dl.sourceforge.net/sourceforge/azureus/Azureus2.5.0.0.jar

sudo mv Azureus2.5.0.0.jar /usr/share/java/Azureus2.jar
```

---

### Post by rytmisk on 2007-08-15
Thanks!! I really had problems with azureus (and I even tried Vuze, but it didn't work any better). The downgrade described here actually solved it!

Thanks!
Ketil

> **Crube said:**
> I had the same problem and I found another solution. It seemed to me like the problem was with Azureus. Here's the solution found from [http://languor.us/azureus-unexpected-error-has-been-detected-hotspot-virtual-machine]("http://languor.us/azureus-unexpected-error-has-been-detected-hotspot-virtual-machine")

```
Command line fix:

sudo wget http://superb-west.dl.sourceforge.net/sourceforge/azureus/Azureus2.5.0.0.jar

sudo mv Azureus2.5.0.0.jar /usr/share/java/Azureus2.jar
```

---

### Post by naughtykid on 2007-08-15
Thanks! This really solved my problem over Azureus.

There are now Azureus 2.5.0.4 which can be done this way too:

```

sudo mv Azureus2.5.0.4.jar /usr/share/java/Azureus2.jar

```

which is exactly the same.

---

### Post by frodon on 2007-08-15
For those who have this problem go in  your .azureus/logs directory (in your home directory) and delete all the log files.

After that you should be ok, i don't think this is a java problem but more an azureus bug because deleting the azureus log solve the issue.

---

### Post by Hachi on 2007-08-19
Thanks frodon,

Trying to fix Java didn't do anything for me, but deleting all the log files worked for me straight away.

---

### Post by Aishiko on 2007-08-19
does Azureus have a mem leak like it does under windows or is that not an issue in Linux environments?

---

### Post by Chris S. on 2007-08-19
Deleting the log files is still only a temporary fix.  Eventually, you'll get another log or error dialog and the problem will happen again.  If you go to the sourceforge page for Azureus, there is a page dedicated for downloading the latest Azureus .jar file.  If you follow the instructions here to replace Azureus2.jar with this file, that WILL solve the logging problem that nearly all of you are experiencing.

The reason the source Azureus works instead of the repo version is that the repos have the old .jar version with the logging problem.

---


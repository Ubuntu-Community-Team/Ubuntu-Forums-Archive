---
title: "Attempting to install TeleTeachingTool (Java app?) with no success. :("
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by sylvius on 2007-02-21
Hi there,

I am relatively new to Ubuntu, but have been successful in installing applications in several ways so far (Add/Remove, Synaptic, as well as compilation from source). However, I am having trouble installing one particular application.

It is called TeleTeachingTool, and is available for free on the following website: [http://ttt.uni-trier.de/ttt_download.en.html](http://ttt.uni-trier.de/ttt_download.en.html)

I have tried downloading the various packages and extracting the files from them, but am unsure of how to go about installing/running the files included. If someone could download the program and get it to work and show me how, I would greatly appreciate it.

This program is used to view recorded lectures at my university. Thanks in advance!

---

### Post by ashmew2 on 2007-02-21
im on a 256 kbps internet and im downloadig your package while posting this. ANyhow , what i think is that since its a .tar.bz2 its pretty much a  source file and since uve had experiece installing from source , whats the prob ?

---

### Post by igknighted on 2007-02-21
If it's a java program there is probably a .jar file in there.  That should be the executable.  Assuming you have installed sun's java packages (sudo aptitude install sun-java6-jre) then you just need to type this in the terminal:
```
java -jar <filename>.jar
```
after extracting the archive.

---

### Post by phossal on 2007-02-21
Trojan Horse? Sales Pitch?

---

### Post by sylvius on 2007-02-21
Holy crap, I must be the stupidest person in the world.

Thanks to all who responded. After exploring all possible folders in the archive, I found a file called "runttt" which ran the program!!

I guess this is why I am posting in the "Absolute Beginner Talk" forum. :)

Thanks again, everyone!

---


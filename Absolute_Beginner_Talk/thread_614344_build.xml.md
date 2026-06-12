---
title: "build.xml"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by m@@dL3s on 2007-11-15
I am trying to install FreeCol.

I have installed SunJava, jre bin and jdk successfully

I ran sudo apt-get install build-essential and also, as in the installation directions with FreeCol, installed Apache Ant.

When I am in the FreeCol directory and run "ant" to build the jar file for the game, it tells me that there is no file 

build.xml

I *think* this is supposed to be part of the FreeCol files? or is there a dependency that I am missing,..  thank you for your help

---

### Post by sgordon on 2007-11-18
Ok

FreeCol has a few download options, you need to ensure you get the package with the source included. The link I followed, took me to:
[http://prdownloads.sourceforge.net/freecol/freecol-0.7.2-src.zip?download](http://prdownloads.sourceforge.net/freecol/freecol-0.7.2-src.zip?download)
(note -src)

Note, you also need the ant-optionals package:
sudo apt-get install ant-optional

Then it was just a case of:
unzip freecol-0.7.2-src.zip
cd freecol
ant

Let me know how it goes.

  Si

---

### Post by m@@dL3s on 2007-11-20
Thank you, si! that was helpful. I won't have time to try it again until after the holiday, but I will post back when I do.

---


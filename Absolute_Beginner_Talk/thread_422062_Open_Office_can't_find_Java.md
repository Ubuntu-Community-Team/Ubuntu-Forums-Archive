---
title: "Open Office can't find Java"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Miguellint on 2007-04-24
Hi all...I'm using Open Office 2.0.4 and Java 1.6.0_01 under Xubuntu Edgy.

The java install is working fine (verified at java.com) but Open Office won't recognise it.

I've used Tools/Options/OpenOffice.org/Java to let OO know where the JRE is found but keep getting "The folder you selected does not contain a Java runtime environment" error message.

I've used different depths of the path as suggested in the OpenOffice.org forums, for example 
/usr/java/jre1.6.0_01 
or 
/usr/java/jre1.6.0_01/lib/i386
or 
/usr/java
but no luck.

Does anyone know which file in particular OO is looking for. Isn't it normally libjava.so

Any advice appreciated.

Regards
Miguel

---

### Post by stmiller on 2007-04-24
Openoffice only uses java for macros in the spreadsheet. So it's better if you do not enable it (openoffice will work faster!)

But if you need java for macros, it may be looking for java in /opt/java

---

### Post by Miguellint on 2007-04-25
I needed to install openoffice.org-java-common 2.0.4 which I found in Synaptic.

Live and learn :-)

Regards
Miguel

---

### Post by davedave on 2008-02-20
Installing openoffice.org-java-common worked for me too, I was then able to select my JRE.

Great, thanks!

---


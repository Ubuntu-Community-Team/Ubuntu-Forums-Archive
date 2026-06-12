---
title: "Limewire"
date: 2005-07-29
forum: Apple PPC Users
---

### Post by dasaivet on 2005-07-29
Hi there,
I was wondering if anyone got Limewire running on their ubuntu ppc.

I downloaded IBM's jdk (latest SR2) as I use it with Eclipse. I thought I'd install Limewire because it's pretty good. But no luck in getting it to run. It shows the splash screen and then it stops. No error code, just a classic freeze.

Any ideas out there?

Cheers

---

### Post by harryc on 2005-07-31
It runs fine here. I used the Ubuntu guide.

[http://powerpc.ubuntuguide.org/](http://powerpc.ubuntuguide.org/)

---

### Post by dasaivet on 2005-07-31
Thanks. But i already tried that...it just freezes when starting

Cheers

---

### Post by dasaivet on 2005-07-31
I finally managed to get an error message...

LimeWire version 4.9.11
Java version 1.4.2 from IBM Corporation
Linux v. 2.6.10-5-powerpc on ppc
Free/total memory: 1169416/4454912

com.limegroup.gnutella.gui.GUILoader$StartupFailedException: invalid logicrypto.jar
	at com.limegroup.gnutella.gui.GUILoader.sanityCheck(GUILoader.java:268)
	at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:40)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:85)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:58)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:60)
	at java.lang.reflect.Method.invoke(Method.java:391)
	at com.limegroup.gnutella.gui.Main.main(Main.java:44)

STARTUP ERROR!




FILES IN CURRENT DIRECTORY:
/home/dasa/bin/starteclipse
LAST MODIFIED: 1120083125000
SIZE: 318

/home/dasa/bin/javacore.20050626.173155.14259.txt
LAST MODIFIED: 1119799915000
SIZE: 93488

/home/dasa/bin/squeak
LAST MODIFIED: 1120429749000
SIZE: 98

/home/dasa/bin/java
LAST MODIFIED: 0
SIZE: 0

/home/dasa/bin/starteclipse~
LAST MODIFIED: 1120082927000
SIZE: 330

/home/dasa/bin/javaw
LAST MODIFIED: 0
SIZE: 0

/home/dasa/bin/LimeWireOther.zip
LAST MODIFIED: 1122817940000
SIZE: 4901697

/home/dasa/bin/LimeWire
LAST MODIFIED: 1122818211000
SIZE: 4096

/home/dasa/bin/2
LAST MODIFIED: 1122818098000
SIZE: 4096

/home/dasa/bin/LimeWireSoftOther.zip
LAST MODIFIED: 1122818180000
SIZE: 5409612

---

### Post by Jason-X on 2005-08-05
Sorry I can't help with the error message, but I'm having the same problem. Sometimes Limewire starts and sometimes it does not. It's a bit hit and miss really.

I followed the ubuntuguide to install Limewire (&java).

Has anybody got any ideas what the problem could be?

Thanks :)

---

### Post by slux on 2005-08-15
"Me too".

Might be a problem with IBM's Java implementation. I wish someone got Limewire up and running with GCJ/GIJ or Sun made theirs free software so Java would not be such a PITA.

I got a little further with the beta but still not working. I set up gtk-gnutella for the time being. It doesn't have such a nice UI but at least it works.

---


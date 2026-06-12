---
title: "Problem using Firefox Java Plugin @ pokerroom.com"
date: 2006-07-16
forum: Apple PPC Users
---

### Post by davidr00 on 2006-07-16
Hi,

I just installed Ubuntu Dapper on my Apple iBook G4 and it works great.  I installed the Java SDK 1.5 from IBM.  I set up the firefox plugin symbolic link and it works fine.  Except for one website.

When I go to pokerroom.com to play poker (which I do all the time under Mac OS X) I signon as usual and then run the java applet to play some poker. 

It might display the poker table correctly initially but after a few minutes the images are not drawn correctly or disappear and the colors displayed in the applet change color often to purple.

Could this be a problem with the IBM Java implementation or perhaps some type of setting related to the video driver?

Any help or suggestions would be greatly appreciated,
~D.

---

### Post by APU on 2006-07-17
Maybe the Java Applet on this website has some Problems with Java 1.5. You could try to additionally install a 1.4 JRE (not JDK) from IBM and use this for the Firefox plugin. It should be much more compatible that way and you don´t really need Java 1.5 for the grand majority of all Web Applets anyway.

APU

---

### Post by davidr00 on 2006-07-17
I have already installed the IBM 1.4 JDK but I couldn't find the Firefox plugin module libjavaplugin_oji.so to link to in the 1.4 release.  I don't know if the 1.4 JRE would be any different but I'll try it tonight when I get home from work.  Thanks for the suggestion.

~D.

---

### Post by davidr00 on 2006-07-17
Both the JDK and JRE versions of 1.4 are missing the libjavaplugin.so.  Any other suggestions?????

~D.

---


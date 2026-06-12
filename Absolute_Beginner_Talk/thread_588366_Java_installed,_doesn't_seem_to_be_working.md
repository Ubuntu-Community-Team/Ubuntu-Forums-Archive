---
title: "Java installed, doesn't seem to be working"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by asmodexx on 2007-10-23
Okay, so I just installed Java 6 using the advice that was given to someone else and it worked.  I'm trying to connect to a chat room, and while the different rooms available are shown in the java applett window, as soon as i try entering one of them a black grey window that says 'java applet' pops up.  help computer.

---

### Post by be4truth on 2007-10-23
Paste this into a terminal

```
sudo update-alternatives --config java
```

Choose here your default java.
Did you install 32 or 64 bit version?

---

### Post by asmodexx on 2007-10-23
> **be4truth said:**
> 
Did you install 32 or 64 bit version?

How do i find out which version i've installed?  oh, and i changed there were two options when i followed your suggestion, i changed the default to the one it wasn't set to and no change.

---

### Post by be4truth on 2007-10-23
You should get something like this:

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java
 +        3    /usr/lib/jvm/java-7-icedtea/jre/bin/java

Press enter to keep the default[*], or type selection number: 

The default is the one with the *.
Did you install the Firefox plugin for java?
I have gutsy 64 bit and similar problems. Haven't yet found a solution.

---

### Post by asmodexx on 2007-10-23
yeah, the firefox plugin has been installed, and the first java thing i opened worked, but opening something from within the java window itself didn't.

---


---
title: "Frostwire and Java problem"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by OptimusPrime on 2006-10-07
I thought I almost had Frostwire working, but when I go into the terminal and type "frostwire" I get this:

wesley@wesley-laptop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.4.2]
Configuring environment...
Loading FrostWire:
log4j:WARN No appenders could be found for logger (com.limegroup.gnutella.gui.Initializer).
log4j:WARN Please initialize the log4j system properly.
*** glibc detected *** free(): invalid pointer: 0x0000000002234780 ***
runFrost.sh: line 108:  6250 Aborted                 ${JAVA_PROGRAM_DIR}java -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. -jar FrostWire.jar


What is wrong?

---

### Post by OptimusPrime on 2006-10-07
I just installed Blackdown JRE,  I'm running on 64bit, and I have no idea what to do.

---

### Post by OptimusPrime on 2006-10-07
Now, the frostwire loading screen comes up, but it goes away and, hey, no frostwire. Here is what the terminal has to say:


Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.4.2]
Configuring environment...
Loading FrostWire:

(.:7427): Gtk-WARNING **: cannot open display:

******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(Frostwire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.4.2"
CACAO version 0.93

---

### Post by OptimusPrime on 2006-10-07
That last one was using terminal in super user mode. For some reason, they show different error messages.

---

### Post by taurus on 2006-10-07
See exactly what version of java you are using, run this command from a terminal...

```
java -version
```
And if you want to run frostwire as superuser, then you need to include the "gksudo" in front!!!

```
gksudo frostwire
```

---


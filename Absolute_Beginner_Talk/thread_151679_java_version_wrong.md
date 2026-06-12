---
title: "java version wrong?"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by wolfee on 2006-03-28
i ran this command and got this message

lou@c-67-163-247-106:~$ nice --adjustment=19 frostwire &
[1] 12375
lou@c-67-163-247-106:~$ Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_06]
Configuring environment...
Loading FrostWire:
log4j:WARN No appenders could be found for logger (com.limegroup.gnutella.gui.Initializer).
log4j:WARN Please initialize the log4j system properly.
/usr/share/themes/Simple/gtk-2.0/gtkrc:46: Engine "thinice" is unsupported, ignoring
/usr/share/themes/Simple/gtk-2.0/gtkrc:53: Engine "redmond95" is unsupported, ignoring
/usr/share/themes/Simple/gtk-2.0/gtkrc:57: Engine "redmond95" is unsupported, ignoring
runFrost.sh: line 109: 12407 Killed                  ${JAVA_PROGRAM_DIR}java -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. -jar FrostWire.jar

******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

I was told this will "free up" cpu by changintg the priority of frostwire (which can also be done in system monitor) Does anyone know what this message means?

---

### Post by Pragmatist on 2006-03-28
I would try this test:
1.) leave out the nice command (shouldn't be the problem, but simplify for now)
2.) use full path of java command
3.) use full path of program command.

See what that does and let us know what happens.

---

### Post by wolfee on 2006-03-28
This is what I got and then Frotwire ran

[B]lou@c-67-163-247-106:~$ adjustment=19 frostwire &
[1] 11430
lou@c-67-163-247-106:~$ [1] 12375Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_06]
Configuring environment...
Loading FrostWire:
log4j:WARN No appenders could be found for logger (com.limegroup.gnutella.gui.Initializer).
log4j:WARN Please initialize the log4j system properly.
/usr/share/themes/Simple/gtk-2.0/gtkrc:46: Engine "thinice" is unsupported, ignoring
/usr/share/themes/Simple/gtk-2.0/gtkrc:53: Engine "redmond95" is unsupported, ignoring
/usr/share/themes/Simple/gtk-2.0/gtkrc:57: Engine "redmond95" is unsupported, ignoring[/B]

Doesnt sound good.

---

### Post by Pragmatist on 2006-03-28
Not sure why your using the append=19 ?

My suggestion was to give the full path of the java command and the full path of the program.  For example:

/usr/bin/java -jar  /usr/local/share/frostwire-1-2-3-386/frostwire

This assumes your java excutable is located at /usr/bin
This also assumes that the frostwire executable is at /usr/local/share/frostwire-1-2-3-386

You need to find the actual locations.  To find the locations use the locate command.  First update locate's database so it can work:
```
sudo updatedb
```
this takes a little while.  When it is done, do this:
```
locate java |grep bin
```
and this
```
locate frostwire
```

---


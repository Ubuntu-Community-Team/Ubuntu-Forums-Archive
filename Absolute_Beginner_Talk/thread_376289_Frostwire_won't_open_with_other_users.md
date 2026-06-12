---
title: "Frostwire won't open with other users"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Nefi on 2007-03-04
I'm pretty new to the whole ubuntu scene, and since i have multiple people using one computer i'm trying to make two users use frostwire. Frostwire works when I log in with my user, but it doesn't even start up on any other users.

Also, when I type frostwire in termnial, I get this.
```
Fatal server error:
Could not create server lock file: /tmp/.X2-lock

Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_08]
Configuring environment...
Loading FrostWire:
bt::Display: failed to open display ''
java.lang.InternalError: Can't connect to X11 window server using ':2' as the value of the DISPLAY variable.
        at sun.awt.X11GraphicsEnvironment.initDisplay(Native Method)
        at sun.awt.X11GraphicsEnvironment.access$000(X11GraphicsEnvironment.java:53)
        at sun.awt.X11GraphicsEnvironment$1.run(X11GraphicsEnvironment.java:142)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.X11GraphicsEnvironment.<clinit>(X11GraphicsEnvironment.java:131)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:164)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:68)
        at sun.awt.X11.XToolkit.<clinit>(XToolkit.java:96)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:164)
        at java.awt.Toolkit$2.run(Toolkit.java:821)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:804)
        at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:67)
        at com.limegroup.gnutella.gui.Main.main(Main.java:39)


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)

Xephyr: no process killed

```

Any solutions?

---

### Post by lyceum on 2007-03-07
*bump*

I am not sure, but first question, is your user the master user? I think you have to set up other users sharing software, but I am not sure how (I am trying to help more by bumping the question than answering, sorry)

---


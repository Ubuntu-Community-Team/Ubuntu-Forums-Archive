---
title: "KISS aint going so great..."
date: 2008-05-13
forum: Arch and derivatives
---

### Post by b0uncyfr0 on 2008-05-13
Ive got my Arch system functional and its awesome so far. Its just a few applications that refuse to obey the rules.

1-Running gparted as root:

No protocol specified

(gparted:7913): Gtk-WARNING **: cannot open display: :0.0

2-Running frostwire (Java 1.6):

Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_05]
Configuring environment...
Loading FrostWire:
No protocol specified
java.lang.InternalError: Can't connect to X11 window server using ':0.0' as the value of the DISPLAY variable.
        at sun.awt.X11GraphicsEnvironment.initDisplay(Native Method)
        at sun.awt.X11GraphicsEnvironment.access$100(X11GraphicsEnvironment.java:52)
        at sun.awt.X11GraphicsEnvironment$1.run(X11GraphicsEnvironment.java:155)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.X11GraphicsEnvironment.<clinit>(X11GraphicsEnvironment.java:131)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:68)
        at sun.awt.motif.MToolkit.<clinit>(MToolkit.java:96)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at java.awt.Toolkit$2.run(Toolkit.java:836)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:828)
        at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:67)
        at com.limegroup.gnutella.gui.Main.main(Main.java:39)

3-And running nspluginwrapper -v -a -i

Auto-install plugins from /usr/lib/mozilla/plugins
Looking for plugins in /usr/lib/mozilla/plugins
Install plugin /usr/lib/mozilla/plugins/libflashplayer.so
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/libnpsoplugin.so: wrong ELF class: ELFCLASS64
Auto-install plugins from /home/jt/.mozilla/plugins
Looking for plugins in /home/jt/.mozilla/plugins
Install plugin /home/jt/.mozilla/plugins/libflashplayer.so

---

### Post by Barrucadu on 2008-05-13
The first two error messages ("cannot open display") suggest that X isn't running when you try to open them, is it?

---

### Post by b0uncyfr0 on 2008-05-13
Ive got the first problem working. Instead of using su it should be kdesu.

---


---
title: "Frostwire problems with Java RE 1.5"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by jaysondin87 on 2006-07-30
I can't get frostwire to work..

jayson@jays:/usr/bin$ ./frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)

however im sure that java is installed because...

jayson@jays:/usr/bin$ java
Usage: gij [OPTION] ... CLASS [ARGS] ...
          to invoke CLASS.main, or
       gij -jar [OPTION] ... JARFILE [ARGS] ...
          to execute a jar file
Try `gij --help' for more information.
jayson@jays:/usr/bin$


I think theres a problem with the configuration.. anyone have any idea on how to fix this?

---

### Post by bluevoodoo1 on 2006-07-30
See if this thread helps (especially the 2nd post)

[http://ubuntuforums.org/showthread.php?t=207477&highlight=frostwire](http://ubuntuforums.org/showthread.php?t=207477&highlight=frostwire)

---

### Post by taurus on 2006-07-30
> **jaysondin87 said:**
> I can't get frostwire to work..

jayson@jays:/usr/bin$ ./frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)

however im sure that java is installed because...

jayson@jays:/usr/bin$ java
Usage: gij [OPTION] ... CLASS [ARGS] ...
          to invoke CLASS.main, or
       gij -jar [OPTION] ... JARFILE [ARGS] ...
          to execute a jar file
Try `gij --help' for more information.
jayson@jays:/usr/bin$


I think theres a problem with the configuration.. anyone have any idea on how to fix this?

Sorry but you need to install the actual java from either Blackdown or Sun, not the one that comes with gcc!!!  You can use Automatix to install it if you wish...

[http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646)

---


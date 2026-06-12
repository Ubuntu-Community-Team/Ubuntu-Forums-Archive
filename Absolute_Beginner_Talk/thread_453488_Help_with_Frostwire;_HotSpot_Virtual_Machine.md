---
title: "Help with Frostwire; HotSpot Virtual Machine?"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by wastedfluid on 2007-05-24
Okay guys.

I was trying to install Frostwire last night.  Figured out I need SUN JAVA 1.5.  So I downloaded it.  Then it wasn't set default.. (I forgot the command I used) to choose between which version of the software you use when you have multiple copies(different versions) of software. 

So anyway, I finally got ubuntu to use the SUN JAVA 1.5.  Frostwire STARTED to run.  I get this error!

```

#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb102fd6f, pid=27932, tid=2967362480
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_06-b05 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x30d6f]
#
# An error report file with more information is saved as hs_err_pid27932.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
/usr/lib/frostwire/runFrostwire.sh: line 122: 27932 Aborted                 ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS

******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

wastedfluid@wastedfluid:~$ 

```

---


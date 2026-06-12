---
title: "frostwire doesnt launch"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by KezzerDrix on 2008-01-20
downloaded the newest frostwire from their site and installed it.  The icon is their  but when I click on it nothing happens.  

Any help?

---

### Post by CupofDice on 2008-01-20
Try running it from the terminal. It is probably a java problem (pretty common), so in the terminal also type " java -version ".

Edit- Just noticed you're running 64, so that may also be the problem.

---

### Post by KezzerDrix on 2008-01-20
this is the error I get

Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Loading FrostWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b5b00928e25, pid=17592, tid=1076017488
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0_03-b05 mixed mode)
# Problematic frame:
# C  [libc.so.6+0x2fe25]  catgets+0x15
#
# An error report file with more information is saved as hs_err_pid17592.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
/usr/lib/frostwire/runFrostwire.sh: line 125: 17592 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0_03-b05, mixed mode)

---

### Post by CupofDice on 2008-01-20
What is the output of " java -version ".

Edit- and what are the options given when you type " sudo update-alternatives --configure java ".

---


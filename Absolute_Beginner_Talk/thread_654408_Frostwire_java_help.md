---
title: "Frostwire java help"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by dnns123 on 2007-12-31
I have java (icedtea) installed but frostwire wants sun jre 1.5.x or better, what do I do? i tried some posts, but none helped. This is what I get:

> 
dnns@ubuntu:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.7.0]
Configuring environment...
Loading FrostWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002ad3dd87ee11, pid=10053, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /usr/lib/frostwire/hs_err_pid10053.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
/usr/lib/frostwire/runFrostwire.sh: line 125: 10053 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.7.0"
IcedTea Runtime Environment (build 1.7.0-b21)
IcedTea 64-Bit Server VM (build 1.7.0-b21, mixed mode)


---

### Post by Perfect Storm on 2007-12-31
You need to use sun java 32-bit layer. IcedTea /alternative to sun java) is still bugged/incomplete.

---

### Post by dnns123 on 2007-12-31
Any other? I have tried these

> 
dnns@ubuntu:~$ sudo update-alternatives --config java

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java
          3    /usr/lib/jvm/java-7-icedtea/jre/bin/java
 +        4    /usr/lib/j2se/1.4/bin/java
          5    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 


All dont work =/

---

### Post by Perfect Storm on 2007-12-31
As said you need to install sun java 32 bit.

---


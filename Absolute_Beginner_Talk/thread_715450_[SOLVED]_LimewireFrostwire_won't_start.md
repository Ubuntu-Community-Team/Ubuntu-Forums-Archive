---
title: "[SOLVED] Limewire/Frostwire won't start"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by indiana_crook on 2008-03-04
I'm trying to use Limewire/Frostwire and neither of them will start when I click the icons or try to open them from the applications menu.  I was just using limewire two hours ago.  what's going on??

---

### Post by kool_kat_os on 2008-03-04
> **indiana_crook said:**
> I'm trying to use Limewire/Frostwire and neither of them will start when I click the icons or try to open them from the applications menu.  I was just using limewire two hours ago.  what's going on??

go through synaptic and reinstall it. It may work

---

### Post by indiana_crook on 2008-03-04
already tried that and still... nothing

---

### Post by taurus on 2008-03-04
Do you have Sun java installed?  What does it say when you run this command from a terminal?

Applications -> Accessories -> Terminal
```
java -version
```

---

### Post by indiana_crook on 2008-03-04
caleb@caleb-desktop:~$ java -version
java version "1.7.0"
IcedTea Runtime Environment (build 1.7.0-b21)
IcedTea 64-Bit Server VM (build 1.7.0-b21, mixed mode)
caleb@caleb-desktop:~$ 
 
This is what I get...

---

### Post by kool_kat_os on 2008-03-04
> **indiana_crook said:**
> caleb@caleb-desktop:~$ java -version
java version "1.7.0"
IcedTea Runtime Environment (build 1.7.0-b21)
IcedTea 64-Bit Server VM (build 1.7.0-b21, mixed mode)
caleb@caleb-desktop:~$ 
 
This is what I get...

i guess that java is installed then...

EDIT: are you on 64 bit?

---

### Post by indiana_crook on 2008-03-04
Yeah I've reinstalled/downloaded everything i can think of, still nothing...Yes. Running a 64 bit...

---

### Post by santiagoward2000 on 2008-03-04
> **indiana_crook said:**
> I'm trying to use Limewire/Frostwire and neither of them will start when I click the icons or try to open them from the applications menu.  I was just using limewire two hours ago.  what's going on??

Hi!
Try opening them from a terminal and see if you get any errors. Open a terminal and type: ```
frostwire
```
or ```
limewire
``` (I'm actually guessing on LimeWire's command, I haven't ever used it in Ubuntu) If it doesn't open, post the result here, perhaps we can find the problem.
Cheers!

---

### Post by indiana_crook on 2008-03-04
This one with frostwire...


caleb@caleb-desktop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.7.0]
Configuring environment...
Loading FrostWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002aec10c54e11, pid=6793, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /usr/lib/frostwire/hs_err_pid6793.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
/usr/lib/frostwire/runFrostwire.sh: line 125:  6793 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.7.0"
IcedTea Runtime Environment (build 1.7.0-b21)
IcedTea 64-Bit Server VM (build 1.7.0-b21, mixed mode)

This one with limewire...

caleb@caleb-desktop:~$ limewire
Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.7.0]
Configuring environment...
Loading LimeWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b6dfe4b4e11, pid=6875, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /tmp/hs_err_pid6875.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
./runLime.sh: line 124:  6875 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar LimeWire.jar $ARGUMENTS

******************************************************************
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.5+)
The version of Java in your PATH is:
java version "1.7.0"
IcedTea Runtime Environment (build 1.7.0-b21)
IcedTea 64-Bit Server VM (build 1.7.0-b21, mixed mode

---

### Post by taurus on 2008-03-04
Try removing the IceTea version and install the Sun java 1.6 version!

---

### Post by odiseo77 on 2008-03-04
Some programs don't work fine with java 1.7. Try this (in a terminal):

```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
sudo update-alternatives --config java
```

Select java 1.6 at the menu prompt and start limewire after that to see what happens.

---

### Post by indiana_crook on 2008-03-04
> **taurus said:**
> Try removing the IceTea version and install the Sun java 1.6 version!

I'm sorry is that the Sun Java 6 Web Start or console or does it make a difference?

---

### Post by DarkZyzx on 2008-03-04
Correct me if I am wrong, but I thought you couldn't run limewire and frostwire together on the same computer.

---

### Post by indiana_crook on 2008-03-04
> **DarkZyzx said:**
> Correct me if I am wrong, but I thought you couldn't run limewire and frostwire together on the same computer.

You see the question I have is why was it working two hours ago and then all the sudden stop working???  I have the automatix2 program is that causing all this?

---

### Post by DarkZyzx on 2008-03-04
> **indiana_crook said:**
> You see the question I have is why was it working two hours ago and then all the sudden stop working???  I have the automatix2 program is that causing all this?

Automatix is pretty messed up sometimes... it could very well be the problem.

---

### Post by Dr.Ninethousand on 2008-03-10
I'm having this problem now too and I'm pretty sure it's because of automatix2..  I wish I had read a few more articles about it first..  :mad:


```
rick@Kutulu:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Loading FrostWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002afc6585a4bf, pid=19050, tid=1076017488
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0_03-b05 mixed mode)
# Problematic frame:
# C  [libc.so.6+0x304bf]  catgets+0x1f
#
# An error report file with more information is saved as hs_err_pid19050.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
/usr/lib/frostwire/runFrostwire.sh: line 125: 19050 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0_03-b05, mixed mode)

```

---

### Post by Dr.Ninethousand on 2008-03-10
I did   sudo update-alternatives --config java

and chose   /usr/lib/jvm/ia32-java-6-sun/jre/bin/java

(I'm on 64bit)

and now it works..  not sure if this is the best solution though..  I'm still wondering what broke it, since it worked a week ago..

---


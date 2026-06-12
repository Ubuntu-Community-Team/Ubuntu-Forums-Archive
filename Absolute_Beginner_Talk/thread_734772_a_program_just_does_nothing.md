---
title: "a program just does nothing?"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by tropdoug on 2008-03-25
I just downloaded and installed frostwire, having alreqady downloaded icedtea

I checked through the terminal *java -version* and got 

[I]Java version "1.7.0"
IcedTea Runtime Environment (build 1.7.0-b21)
IcedTea 64-Bit Server VM (build 1.7.0-b21, mixed mode)
[/I]
but when I click the menu item for 'frostwire' nothing happens. 

does this mean there is a missing link or something?
(I am running an amd 64 bit processor)

---

### Post by kpkeerthi on 2008-03-25
What happens when you type **frostwire** in a terminal window?

---

### Post by bumanie on 2008-03-25
Do you have java6 runtime environment installed? Frostwire needs it to operate (as far as I know).

---

### Post by tropdoug on 2008-03-25
This is what returns

douglas@desktop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.7.0]
Configuring environment...
Loading FrostWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002ac41e016e11, pid=5860, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /usr/lib/frostwire/hs_err_pid5860.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
/usr/lib/frostwire/runFrostwire.sh: line 125:  5860 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.7.0"
IcedTea Runtime Environment (build 1.7.0-b21)
IcedTea 64-Bit Server VM (build 1.7.0-b21, mixed mode)
[I]
Maybe the 1.7.0 build is too new for the frostware build, I wonder if I should try the 1.6.0 java version. 

I did not know that you could just use a name of a program to start it from a terminal, guys can you tell me where is the best place to get command explanations and how the terminals work?

I tried to upload the log file, but it isn't the right ext. 
Douglas[/I]

---

### Post by jan quark on 2008-03-25
some links for linux commnds:

[http://www.linuxcommand.org/index.php](http://www.linuxcommand.org/index.php)
[http://ubuntuhelp.piranho.de/commandtut.html](http://ubuntuhelp.piranho.de/commandtut.html)

---

### Post by tropdoug on 2008-03-25
Thanks jan, I think the next few days are going to be a steep learning curve.

---

### Post by jan quark on 2008-03-25
tropdoug

do not overdo it :)

the best teacher is practical doing, just by using linux you will remember the most important commands without even noticing when you have learned them

---


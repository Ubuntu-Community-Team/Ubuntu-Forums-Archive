---
title: "[SOLVED] Frostwire won't run"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by indiana_crook on 2008-03-05
I've done everything under the sun now.  Frostwire will not start when I click it. I've downloaded and redownloaded, double checked my java installation.  It's all good.  I type it in the terminal and get this:

 caleb@caleb-desktop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.7.0]
Configuring environment...
Loading FrostWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b416462ce11, pid=7303, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /usr/lib/frostwire/hs_err_pid7303.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
/usr/lib/frostwire/runFrostwire.sh: line 125:  7303 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.7.0"
IcedTea Runtime Environment (build 1.7.0-b21)
IcedTea 64-Bit Server VM (build 1.7.0-b21, mixed mode)

Who can tell me what's going on?

---

### Post by santiagoward2000 on 2008-03-05
It seems you are still using the icetea java, not the Sun. Have you uninstalled it?

---

### Post by indiana_crook on 2008-03-05
okay do i do that through add/remove or synaptic?  and how do I know which version is not the "icedtea" version?

---

### Post by indiana_crook on 2008-03-05
> **santiagoward2000 said:**
> It seems you are still using the icetea java, not the Sun. Have you uninstalled it?

you might also keep in mind that I was using limewire when this problem started, I just recently switched to Frostwire because I was told that it is better, but the problem originated when I was using Limewire...  I was using it yesterday afternoon, now it won't work...

---

### Post by santiagoward2000 on 2008-03-05
> **indiana_crook said:**
> okay do i do that through add/remove or synaptic?  and how do I know which version is not the "icedtea" version?

I'm not sure what the package is called, but open **System/Synaptic Package Manager** andd look for something like **icedtea-java7** and see if it's installed. If not, uninstall it. (My Xubuntu computer is not available right now, so I'm not enterily sure about the package's name).
Good luck!

---

### Post by arashiko28 on 2008-03-05
Install the 1.4 version and upgrade, I have the 1.6 and works like a charm. But did had that problem with 1.7.

---

### Post by arashiko28 on 2008-03-05
I forgot to specify, install sun-java6-jre, plugin, bin and fonts, you search it on synaptic.

---

### Post by indiana_crook on 2008-03-05
okay, done all that, this is what i'm getting...

caleb@caleb-desktop:~$ frostwire
Starting FrostWire...
Java exec not found in PATH, starting auto-search...
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
caleb@caleb-desktop:~$

---

### Post by arashiko28 on 2008-03-06
I told you to install the sun-java6-jre from synaptic package manager. After you do that, frostwire should run without any problem. you're stuck with the 1.4 version.

---

### Post by SQuark on 2008-03-08
@arashiko28: He probably did.

@indiana_crook: Try this:

```
sudo update-java-alternatives -s java-6-sun
```

It should work afterwards (assuming you did install sun-java6-jre).

---

### Post by Dr.Ninethousand on 2008-03-10
[http://ubuntuforums.org/showthread.php?p=4492012#post4492012](http://ubuntuforums.org/showthread.php?p=4492012#post4492012)

---


---
title: "[SOLVED] limewire type applications?"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by machosos on 2008-01-04
i was wondering if there is any limewire type program available for ubuntu???

---

### Post by picpak on 2008-01-04
[FrostWire](http://www.frostwire.com/).

---

### Post by machosos on 2008-01-04
thanks...i went to the site and at a glance it says install it everywhere but it has a windows icon....will i still be able to use this with ubuntu

---

### Post by Bufke on 2008-01-04
Did you go there while on an Ubuntu computer?  It seems to detect your OS and put a link for that on the front page, for me it has a ubuntu download link.  If that doesn't work you can just click on other systems.

---

### Post by RomeReactor on 2008-01-04
Hi. [LimeWire]("http://www.limewire.com/download/version.php") has a Linux version. For [FrostWire]("http://www.frostwire.com/?id=downloads"), get it here.

---

### Post by Gwijde on 2008-01-04
You know, Limewire actually has a linux version too, just go to 

[http://www.limewire.com/](http://www.limewire.com/) --> get it now --> Get basic --> say you wont use it for copyright infringment --> click linux(ubuntu, debian)

---

### Post by machosos on 2008-01-04
thanks everyone....i am going to try lime wire.....i didnt know there was a linux version!!! thanks for all of your help

---

### Post by Thunar on 2008-01-04
If you want something with a little more "Linux" flavor, you can try these:

aMule
Azureus
Nicotine-Plus
gtk-gnutella

All of which are available in your "Add/Remove" link in the "Applications" menu.

Make sure when you open your Add/Remove application that you set it to show "All available Applications, not just the "Supported Applications"

good luck.

---

### Post by sailor2001 on 2008-01-04
and nobody bothered to tell the op that it's in the repos?  shame

---

### Post by machosos on 2008-01-04
ok i tired the limewire and now when i click on it from applications nothing happens...any ideas???

---

### Post by RomeReactor on 2008-01-04
As far as I know both LimeWire and FrostWire use Java; make sure you have it installed:
```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-fonts
```
After installing those packages--if they weren't installed--run the program from the terminal, to see if it leaves any error messages:
```
limewire
```
or
```
frostwire
```

> **sailor2001 said:**
> and nobody bothered to tell the op that it's in the repos?  shame

I assume you're referring to the options Thunar suggested.

---

### Post by machosos on 2008-01-05
ran both commands and this is what i get when i run lime wire from terminal:

Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.7.0]
Configuring environment...
Loading LimeWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002af3d82aae11, pid=6178, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /tmp/hs_err_pid6178.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
./runLime.sh: line 124:  6178 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar LimeWire.jar $ARGUMENTS

******************************************************************
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.5+)
The version of Java in your PATH is:
java version "1.7.0"
IcedTea Runtime Environment (build 1.7.0-b21)
IcedTea 64-Bit Server VM (build 1.7.0-b21, mixed mode)

Thanks for your help so far

---

### Post by Taboo Mirage on 2008-01-05
Please run this:

> sudo update-alternatives --config java

Select the number which corresponds to the Sun Java installation and try and run it.

Recommend FrostWire over LimeWire.

Cheers.

---

### Post by intense.ego on 2008-01-05
I have Limewire installed and I have frostwire on my windows PC. Is there really any significant difference?

---

### Post by machosos on 2008-01-05
ok i was able to open it now and do a little configuring on it...not sure if it completely work yet but i will try and let you know...and i used the following option to install:

2    /usr/lib/jvm/java-6-sun/jre/bin/java

---

### Post by Taboo Mirage on 2008-01-05
> **intense.ego said:**
> I have Limewire installed and I have frostwire on my windows PC. Is there really any significant difference?

The difference is that Frostwire is essentially Limewire Pro for free.  It removes the ads and includes much of Limewire Pro's functionality without nagging you to "upgrade" from Limewire's free version each time you start it up.

---

### Post by intense.ego on 2008-01-05
thanks, i will replace limewire with frostwire right now

---

### Post by master_kernel on 2008-01-05
> **intense.ego said:**
> thanks, i will replace limewire with frostwire right now
I recommend Frostwire because:
1) It's open source
2) It has a turbo-charged connection free of charge
3) It's open source
4) It's open source

---

### Post by machosos on 2008-01-05
i had limewire working fine but wanted to try frsotwire...and so far i like it...thank you all!

---


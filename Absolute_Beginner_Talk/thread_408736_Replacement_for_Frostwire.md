---
title: "Replacement for Frostwire"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by kevindubrow on 2007-04-13
Hi, I have tried to install Frostiwre, but it never worked (even after help from the forums). So I was wondering if there was yet another program that connects to Limewire's network that runs on Ubuntu 6.10? Thanks.

---

### Post by VanHammersly on 2007-04-13
GTK-Gnutella is a replacement.  Go to add/remove and install that way.

---

### Post by HereInOz on 2007-04-13
You could try aMule.  You can install it using Automatix if you want to do it easily.

Oddly enough, I tried aMule, and could not really get my head around it, then installed Frostwire and it was fine.  Life is wonderful!!

You could also try Gtk-gnutella.  It is hosted on sourceforge.  

[http://gtk-gnutella.sourceforge.net/en/?page=news](http://gtk-gnutella.sourceforge.net/en/?page=news)

---

### Post by PurplePenguin on 2007-04-13
I had trouble installing Frostwire at first, too.  But Automatix installed it without a problem.

---

### Post by userundefine on 2007-04-13
How did you try to install it?  The instructions on the unofficial wiki work for me:

```
wget -c http://fuse.frostwire.com/frostwire/4.13.1/frostwire-4.13.1.5-1.i586.deb
sudo dpkg -i frostwire-4.13.1.5-1.i586.deb
```

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_Gnutella_Client_.28FrostWire.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_Gnutella_Client_.28FrostWire.29)

---

### Post by kevindubrow on 2007-04-13
I got the file from the Frostwire website itself. Ill try that code you gave me and the other programs everyone suggested and give it a shot. Also, I am very new to Ubuntu and Lunix, I installed the program by just double clicking on the .deb file i got off the internet, is there a better way? Thanks.

----------------------------------------------------
Ok I tried the code, I eventuallt get this error:
sudo dpkg -i frostwire-4.13.1.5-1.i586.deb
dpkg: error processing frostwire-4.13.1.5-1.i586.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 frostwire-4.13.1.5-1.i586.deb

---

### Post by Maestro23 on 2007-04-13
> **kevindubrow said:**
> I got the file from the Frostwire website itself. Ill try that code you gave me and the other programs everyone suggested and give it a shot. Also, I am very new to Ubuntu and Lunix, I installed the program by just double clicking on the .deb file i got off the internet, is there a better way? Thanks.

----------------------------------------------------
Ok I tried the code, I eventuallt get this error:
sudo dpkg -i frostwire-4.13.1.5-1.i586.deb
dpkg: error processing frostwire-4.13.1.5-1.i586.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 frostwire-4.13.1.5-1.i586.deb

Did you d/l the .deb to your Desktop?  If so:

> cd /home/username/Desktop

ls (should see the package)

sudo dpkg -i .....

If your java is correctly installed the program should start to install.  It will create a menu entry for you.

---

### Post by HereInOz on 2007-04-13
You have to run that code as two separate commands - one line at a time.  

The first line downloads the files(s) and the second line installs the program.

Did you perhaps enter the whole thing as one command?

---

### Post by kevindubrow on 2007-04-13
yes, sorry, ill try again. I'm still new to all of this.
------------------------------------------------
Ok, I tried the code in two separate lines and had the same error.

---

### Post by kevindubrow on 2007-04-13
and yes, I did get the .deb file on my desktop, i do have Java 5 installed and running and Froswtwire is in my menu. The program just wont open; no error messages, just wont open.

---

### Post by thefoolisme on 2007-04-13
Hi there, 

I had problems with Frostwire too at first.  Said it needed Java 1.5, so I installed Java 1.5, and it still didn't work.  I researched, and came across this link:  [http://daveshuck.instantspot.com/blog/index.cfm/2007/2/7/Installing-Java-6-16-in-Linux](http://daveshuck.instantspot.com/blog/index.cfm/2007/2/7/Installing-Java-6-16-in-Linux)

It's about installing java 1.6.  Was might be helpful is the part about making sure which java is chosen to run on the OS.  I had 1.4 and 1.5 installed, but 1.4 was the one Ubuntu was using.  I had to configure it.  Once I did that, Frostwire started right up.

---

### Post by kevindubrow on 2007-04-13
Thanks so much, I'll tell you how it goes when I'm done.

---

### Post by userundefine on 2007-04-13
Like others have said, Automatrix will install not only frostwire but java too.

If you don't want to go that route, however, the wiki also has a bit on installing java 1.6.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_JRE_v6.0](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_JRE_v6.0)

---

### Post by kevindubrow on 2007-04-13
Do you mind telling em how to use Automatrix? Sorry, Ive been using Ubuntu for only a week.

---

### Post by chalex on 2007-04-13
open a terminal and type "frostwire".  At least you'll see an error message.  Chances are you're trying to use the wrong java runtime.  You can change which java runtime you use by running "sudo update-alternatives --config java"

---

### Post by kevindubrow on 2007-04-13
wow that fixed it! thanks so much!
____________________________________
Wait, never mind, the program closes shortly after opening... any ideas?

---

### Post by chalex on 2007-04-13
run it in a terminal.  it should at least give you some output in the terminal when it quits; maybe a stack trace or maybe a useful error message.

---

### Post by kevindubrow on 2007-04-14
Ok, This is what I get:

#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb10cfb70, pid=6206, tid=2966940576
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x2eb70]
#
# An error report file with more information is saved as hs_err_pid6206.log
[thread -1329542240 also had an error]
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
/usr/lib/frostwire/runFrostwire.sh: line 122:  6206 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)

---

### Post by xpod on 2007-04-14
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

IF all else fails and you still need to take the AX route then just scroll down to "east direct installation" for your distro and off you go...:D 

Plenty other good stuff besides the file sharing apps it has to be said.

Good luck

---


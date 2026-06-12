---
title: "I can no longer launch LimeWire"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by x-ray vision on 2007-04-16
I'm not sure if this has anything to do with it, but earlier today I downloaded Azureus and followed the directions for opening a port on portforward.com, and now when I try to launch LimeWire, nothing happens. Anyone know why?

---

### Post by amaroKer on 2007-04-16
Did you open the ports on your firewall, or your router?

Either way, I'd say that is completely unrelated, and something else screwed it up.  I hate java programs...

Try reinstalling, or use a different client such as FrostWire, or GTK-Gnutella.

---

### Post by NeoLithium on 2007-04-16
Try opening a terminal and running limewire that way; and post the error messages. :)  Frostwire is a bit better to use though; limewire ultra, but free.

---

### Post by amaroKer on 2007-04-16
Agreed.  Usually the terminal will provide some useful information.  Even sometimes some instructions.

---

### Post by x-ray vision on 2007-04-16
Well, I tried uninstalling LimeWire and reinstalling it and it won't open again.

How do I run LimeWire by opening a terminal?

---

### Post by NeoLithium on 2007-04-16
Applications -> Accessories -> Terminal
 
Inside the window, type: limewire

It will attempt to open the program and there should have some text come across the terminal window with error messages or suggestions. Just copy and paste that result after it fails to open :)

---

### Post by x-ray vision on 2007-04-16
Hmm, this is weird. When type 'limewire' in the terminal, I get this message:


[b]Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)[/b]

I tried upgrading Java by typing "sudo apt-get install sun-java5-jre sun-java5-plugin" (which I already did weeks ago) and I get this message:

[b]Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java5-jre is already the newest version.
sun-java5-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/b]

But when IU check which version of Java I have by typing "java -version", I gt  this message:

[b]java version "1.4.2"
gij (GNU libgcj) version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)[/b]

---

### Post by NeoLithium on 2007-04-17
type in 
```

sudo update-alternatives --config java 

```
then select the alternative that includes "sun" in the name.

---

### Post by x-ray vision on 2007-04-17
> **NeoLithium said:**
> type in 
```

sudo update-alternatives --config java 

```
then select the alternative that includes "sun" in the name.

I got this:

**Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'**

I also installed and uninstalled Automatix2 today, if that means anything.

---

### Post by x-ray vision on 2007-04-17
Okay, now I got:

** "1.5.0_08"**

I'll try uninstalling and reinstalling LimeWire and see what happens.

---

### Post by x-ray vision on 2007-04-17
Thanks Neo, that did the trick. :)

Do you think this problem might have stemmed from me installing Automatix2 today?

---

### Post by NeoLithium on 2007-04-17
It could be, while it's a fast way to install programs; I usually refer people to [http://www.ubuntuguide.org](http://www.ubuntuguide.org) which goes the command line route; but that way you know absolutely everything that was done; and what was installed.  Either way;I'm glad it's all workin for ya now :)

---


---
title: "Frostwire help"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by Biciclettapc on 2008-02-29
Need  help in installing frostwire.

It wont do anything after I install it.  What I mean by that is nothing appears, happens or anything.....

I have installed the Java stuff, but maybe I am missing something.

D/l'd the latest version from froswire, and installed the package (easy to do) but nothing happens.  I have restarted the puter just to check that.

Thanks
Paul

---

### Post by taurus on 2008-02-29
What happens if you run it from a terminal to see what's up with it?

Applications -> Accessories -> Terminal
```
frostwire
```

---

### Post by stoneybroke on 2008-02-29
I have the same problem, I have 2 computers a 32bit and a 64bit I installed frostwire and the java on both computers exactly the same, it works on the 32bit comp but not on the 64bit so I suspect that they have not developed a 64bit version yet if you also have a 64bit comp

Terrible isn't it???

---

### Post by skymera on 2008-02-29
you need java 1.5 not 1.6

i have both installed, search for it in Synaptics

---

### Post by Biciclettapc on 2008-02-29
> **taurus said:**
> What happens if you run it from a terminal to see what's up with it?

Applications -> Accessories -> Terminal
```
frostwire
```

[I]Starting FrostWire...
Java exec found in PATH. Verifying...
1.4.2-02
OOPS, your java version is too old [java = 1.4.2-02]
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
[/I]

So I went to Java and d/l'd the latest Java "jre-6u3-linux-i586.bin" and installed, still same error message.

I removed frostwire, thinking its still seeing the old file structure and re-installed.  Same message.

So, Its obvious I dont know what I need to install.....  Help.

---

### Post by taurus on 2008-02-29
And which version of java are you using?

```
java -version
```
You probably need to configure it so it would use the latest one as default.

```
sudo update-alternatives --config java
```

---

### Post by Teber on 2008-02-29
java is in the repositories. i installed it from there and frostwire works. look in add/remove

hope this helps

---

### Post by Biciclettapc on 2008-02-29
1.4.2-02 
Version of Java

So I go to add/remove and I pretty much have everything with java or jre installed except for  Sun Java 6 Web Start (32bit).

I go to synaptic and same thing, pretty much everything installed except for a few java fonts  (JRE search)

---


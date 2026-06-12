---
title: "FrostWire installed, but won't open..."
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-09-04
I installed Frostwire-4.10.9-2.i586.deb. The GDebi Package Installer says it is installed. When I watched the terminal in the installer GUI, it said it was installing 4.9.2 or something. What's up with that?

When I go to Applications > Internet > Frostwire, and click, it acts like it is going to do something, but never does... No hard drive activity or anything...

Any suggestions?

---

### Post by Anonii on 2006-09-04
I smell a Java problem. Try running it from the terminal with the "frostwire" command, and paste the output here.

---

### Post by taurus on 2006-09-04
Why don't you run it from a terminal to see exactly what the error is.  Open a terminal with Applications -> Accessories -> Terminal and type

```
frostwire
```
Then, post the error message here.  By the way, do you have java install on your machine since frostwire needs java!!!

```
java -version
```

---

### Post by Papa-san on 2006-09-04
Yup... java issue...
```
john@laptop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
```

```
john@laptop:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

OK... just need to find java... Which is best version?

---

### Post by taurus on 2006-09-04
Use either Automatix or BUMP to install java on your machine...  You can also install it by hand by downloading, installing, and configuring it.  Then, run your frostwire again.

---

### Post by Papa-san on 2006-09-04
Kinda don't want Arnieboy to get into root... What is BUMP?

---

### Post by taurus on 2006-09-04
Enjoy...

[http://www.ubuntuforums.org/showthread.php?t=181248](http://www.ubuntuforums.org/showthread.php?t=181248)

---

### Post by Papa-san on 2006-09-04
Thanks Taurus!

---

### Post by taurus on 2006-09-04
> **Papa-san said:**
> Thanks Taurus!
You're welcome.

---

### Post by BatteryCell on 2006-09-04
Yea if you have any other problems make sure that the port it uses isnt blocked, and that lo (local loopback) is up.  Both can cause problems.

---

### Post by DougieFresh4U on 2006-09-04
I found java 6 and Sun java 1.4 in adsd/remove list as I had the same problem myself. taurus is a good helper!! I forgot to thank him. .hope this helps

---


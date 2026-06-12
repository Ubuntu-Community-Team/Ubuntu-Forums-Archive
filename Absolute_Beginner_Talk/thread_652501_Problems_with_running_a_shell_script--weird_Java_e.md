---
title: "Problems with running a shell script--weird Java errors?"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by hul on 2007-12-28
I'm trying to run this shell script.  It presumably installs the program Cronometer.  I keep getting these errors:

```
hul@hul-desktop:~/Desktop$ sudo sh cronometer.sh
: not foundsh: 2: 
: not foundsh: 8: 
cd: 9: can't cd to CRONoMeter.app/Contents/Resources/Java/
Exception in thread "main" java.lang.NoClassDefFoundError: ca/spaz/cron/CRONOMETER

```

I've looked up the individual errors and found little useful.  Could anyone help?  I'd greatly appreciate it.

---

### Post by hul on 2007-12-29
Anybody?  I'm still having issues with this.  :(

---

### Post by SOULRiDER on 2007-12-29
Could you give us a link to hte program?

---

### Post by ghostdog74 on 2007-12-29
> **hul said:**
> I'm trying to run this shell script.  It presumably installs the program Cronometer.  I keep getting these errors:

```
hul@hul-desktop:~/Desktop$ sudo sh cronometer.sh
: not foundsh: 2: 
: not foundsh: 8: 
cd: 9: can't cd to CRONoMeter.app/Contents/Resources/Java/
Exception in thread "main" java.lang.NoClassDefFoundError: ca/spaz/cron/CRONOMETER

```

I've looked up the individual errors and found little useful.  Could anyone help?  I'd greatly appreciate it.
the error gives you a hint,  you need to install cronometer class

---

### Post by hul on 2007-12-29
[This]("http://spaz.ca/cronometer/") is the link to the program.  Where would I find that class?  The download for Linux only has that shell script.  :/

---

### Post by JillSwift on 2007-12-29
Inside the shell script are these instructions: ```
# INSTRUCTIONS 
#  1) Install Java 1.4 or later for Linux (http://java.com/download/) 
#  2) Download Mac OS X Version and Unzip in desired location 
#  3) Place this launcher script next to the application bundle  
#  4) Execute script to launch CRON-o-Meter
```That'll likely fix all =^_^=

---

### Post by carlostenorio on 2008-04-20
In [http://spaz.ca/?p=283#comment-69216](http://spaz.ca/?p=283#comment-69216) I found the solution. 

What worked for me (In Gutsy), was replacing the cronometer.sh script with this:

#!/bin/bash
cd CRONoMeter.app/Contents/Resources/Java
java -cp cronometer.jar:jcommon-1.0.10.jar:jfreechart-1.0.6.jar:swingx-0.9.0.jar:cronometer.jar:usda_sr20.jar:crdb_003.jar:docs.jar ca.spaz.cron.CRONOMETER

I hope this helps!

---

### Post by SOULRiDER on 2008-04-20
The thread is kinda old but at least theres a solution. Maybe you could submit a small "tutorial" on how to run the program in the Tutorials and Tips forums, it may help other users.

---


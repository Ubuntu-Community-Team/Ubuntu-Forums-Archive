---
title: "HOWTO: Custom installation of Sun Java"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by samjh on 2006-12-14
This HOWTO has been moved to a more appropriate location:

[http://www.ubuntuforums.org/showthread.php?t=319138](http://www.ubuntuforums.org/showthread.php?t=319138)

Thanks. :)

---

### Post by xyz on 2006-12-14
Bravo!
Just a thought...you may want to suggest this howTo in the "Faqs, Howto, Tips & Tricks" so that a mod could look at it and post it in the appropriate section.
[http://www.ubuntuforums.org/forumdisplay.php?f=100](http://www.ubuntuforums.org/forumdisplay.php?f=100)

---

### Post by 9am1root on 2006-12-14
Hi, 
I installed java via synaptic and at first it wouldn't start because of
JAVA_HOME and PLUGIN_HOME variables were not set. 
Now they look like this:

$JAVA_HOME
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06

$PLUGIN_HOME
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/plugin

But, now the error showing up is:

java_vm process: could not find Java VM symbols

java_vm is correctly linked to sun java...
what should I do?

tnx

---

### Post by steve.horsley on 2006-12-14
Java 6.0 is out now.

---

### Post by jan247 on 2006-12-15
In the case of Java 6, it's more advisable to add java and javac to update-alternatives.

---

### Post by steve.horsley on 2006-12-15
How do you do that?

---

### Post by samjh on 2006-12-15
> **xyz said:**
> Bravo!
Just a thought...you may want to suggest this howTo in the "Faqs, Howto, Tips & Tricks" so that a mod could look at it and post it in the appropriate section.
[http://www.ubuntuforums.org/forumdisplay.php?f=100](http://www.ubuntuforums.org/forumdisplay.php?f=100)

Thanks for the suggestion.  I didn't know about that forum, as I am still a newbie here; there are so many sub-forums. :)  Hopefully I won't be whipped up for posting this in too many places.

---


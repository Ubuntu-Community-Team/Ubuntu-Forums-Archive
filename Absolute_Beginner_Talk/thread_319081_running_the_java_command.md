---
title: "running the java command"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by jamesstansell on 2006-12-15
> **9am1root said:**
> Hi, 
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

Just use 'java' by itself to run java.  It will automatically set the JAVA_HOME.  For example:

java -version

The java_vm command shouldn't normally be run.  That it was included in /usr/bin/ may be a packaging bug.

HTH,

-james.

---


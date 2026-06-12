---
title: "Java Machine VM"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by bcnme on 2007-06-29
2 things, 

1st: I installed jammvm using the "apt-get install jammvm" but now I dont know where it is installed.
 
2nd: how do I define a path as in "Please define INSTALL4J_JAVA_HOME to point to a suitable JVM".

Thanks for the help.. Bill

---

### Post by DBStevens on 2007-06-29
Bill,

If you use the synaptic package manager you can ask it where the files are.  You highlight the package, and then right click and select properties.

export or set  INSTALL4J_JAVA_HOME=location of the java vm from above  depending on the shell you are running

should be added to rc file for your shell.

[set, export, shells, and how to determine which you are running]("http://www.linuxheadquarters.com/howto/basic/path.shtml")

---


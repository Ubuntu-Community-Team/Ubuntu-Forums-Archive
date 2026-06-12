---
title: "Need mySQL 4.1, JDK1.5, not 5.0, 6"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Sgurd on 2007-02-16
How do I get older version of certain programs.  

I can't use mySQL 5.0 or JDK6.

I specifically need JDK1.5 and mysQL 4.1.

I may also need an older Tomcat, etc.

Thanks in advance - JD

---

### Post by igknighted on 2007-02-16
the package sun-java5-jre is the runtime environment for java 1.5 (they have some funny naming conventions...), and *-jdk is the jdk etc.  Look them up in synaptic and grab the ones you need.  As for mySQL, i have no idea.

---

### Post by Sgurd on 2007-02-16
Thanks for the reply.

I'm on a 6.06 server, command-line only.

When I 'apt-cache search jdk' it only returns the newest jdk (6).

Same with mySQL: only the newest is returned.

I haven't figured out how to use aptitude.

Any help?

   Thanks - JD

---

### Post by igknighted on 2007-02-16
hmm... they must have updated the repo's, I'm a little surprised by that.  Use the sun site to get the 1.5 version then: [http://java.sun.com/javase/downloads/index_jdk5.jsp](http://java.sun.com/javase/downloads/index_jdk5.jsp)

also, you can get mySQL 4.1 here: [http://downloads.mysql.com/archives.php](http://downloads.mysql.com/archives.php)

---


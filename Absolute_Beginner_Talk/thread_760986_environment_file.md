---
title: "environment file"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by cjnkns on 2008-04-20
Hi all - 

I am trying to $echo JAVA_HOME in order to get tomcat to run.
my tomcat install is located in /usr/local/tomcat

I have put this line in /etc/environment 
JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.05"

But, when I do the $echo I get a command not found .. even after I log out...any ideas ?

Thanks for the help.

---

### Post by PeterJS on 2008-04-20
try:
```

echo $JAVA_HOME

```

---

### Post by cjnkns on 2008-04-20
DOH! 

thanks

---

### Post by cjnkns on 2008-04-20
When starting tomcat i get this.

./catalina.sh: 338: /usr/lib/jvm/java-6-sun-1.6.0.05/bin/java: not found

But, I do see the echo $JAVA_HOME

---


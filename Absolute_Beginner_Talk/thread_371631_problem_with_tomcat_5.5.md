---
title: "problem with tomcat 5.5"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by ivantufa on 2007-02-27
Hi
I have a problem with start apache-tomcat-5.5.20.
What do I write in file .bashrc,exactly.
In file is write path for java_home.
When I try start tomcat message **catalina.sh not found** or **permission denied.**
Help me please

---

### Post by ziggykg on 2007-02-28
How are you trying to start Tomcat?

It may be that the files in <tomcat_home>/bin folder are not marked as executable  (<tomcat_home> is the location where you've installed Tomcat).

To mark the files in <tomcat_home>/bin as executable, type the following from the terminal:

```
chmod +x <tomcat_home>/bin/*.sh
```

---


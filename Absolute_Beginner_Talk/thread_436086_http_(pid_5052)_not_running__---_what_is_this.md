---
title: "http (pid 5052?) not running  --- what is this?"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by sgg on 2007-05-07
Hello,

apache2 restart issues this:

```
*Forcing reload of apache 2.0 web server...
httpd (pid 5052?) not running

```

Server is online but I'm concerned about this message.
Anyone know what service pid 5052 is?


Thx

---

### Post by Skrynesaver on 2007-05-07
The PID of a running process is the **P**rocess **ID**entity Apache stores this in a PID file.

When you issue a restart to apache it tries to kill the process with the PID in this file and start a new process.  In this instance the previous process had died/been killed already

---


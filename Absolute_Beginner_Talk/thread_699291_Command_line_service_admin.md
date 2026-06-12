---
title: "Command line service admin"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by jflarm on 2008-02-17
I want to know if there is a command line way to administer the services?
I don't want to use the graphical tool to do it.

---

### Post by jken146 on 2008-02-17
Do you mean processes?  Try ```
top
```

---

### Post by mrsteveman1 on 2008-02-17
If by services you mean daemons etc (things you would otherwise start with init scripts), then yes.

you can directly use the init scripts like this:

```
sudo /etc/init.d/ssh restart|stop|start
```

or you can use the sysv service program like this

```
service ssh restart

```
i believe the service program is in the sysvutils package, but if you type service on an ubuntu system itll tell you if its installed or not and how to install it.

---

### Post by jflarm on 2008-02-17
I know about specific services but...if you want to know about the status of ALL the running services (not processes)...how do you do it?

---

### Post by vikasmk on 2008-02-17
use " top "
 it gives you a list of services running.
 if you find something you dont need 
 just say  "kill " followed by the pid number. and thats it
 just be careful what you kill

---

### Post by Nythain on 2008-02-17
ps is mighty powerfull, though i dont think its gonna tell you anything top wont

---

### Post by mrsteveman1 on 2008-02-17
This works on suse, i don't know about ubuntu but this is the sort of thing you want i think.

```
service --status-all

Checking for Samba NMB daemon                                        running
Checking for UPS monitoring service                                  unused
Checking for service powersaved                                      unused
Checking for random generator (always true)                          running
Checking for rsync daemon:                                           running
```


etc

---

### Post by jflarm on 2008-02-17
Tried your suggestion and had to install these two packages:
sudo apt-get install debian-helper-scripts sysvconfig

but it fails with the sysvconfig package:

dpkg: error processing /var/cache/apt/archives/sysvconfig_0.70_all.deb (--unpack):
 trying to overwrite `/usr/share/man/man8/service.8.gz', which is also in package debian-helper-scripts
Errors were encountered while processing:
 /var/cache/apt/archives/sysvconfig_0.70_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

when I do the command "service --status-all" I get this answer:

/usr/bin/service: 5: /etc/init.d/--status: not found

This is running it as root.
Suggestions?

---

### Post by mrsteveman1 on 2008-02-17
I think you can only install one or the other, sysvconfig, or debian-helper-scripts.

In my server (ubuntu-server) it tells me --status-all does nothing on debian because the init scripts debian uses don't support it.

There are other ways to check the status of services though, try sysv-rc-conf or sysvconfig itself

---


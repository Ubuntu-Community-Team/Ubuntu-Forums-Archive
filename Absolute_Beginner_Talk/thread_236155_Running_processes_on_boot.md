---
title: "Running processes on boot"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by Snoopy381 on 2006-08-14
im sure this will be a very sipmle one line answer but iv had a look and can't find the answer, so your help would be appreicated.

im just looking for the command/file to edit to make a process run on boot.
last time i tried to do this i used 
```
[root@bigboy tmp]# chkconfig mysqld on
```

but im pretty sure that was on redhat (note mysql is just an example)

so if someone could tell me the ubuntu equivilent command that would be great, thanks.

---

### Post by kebes on 2006-08-14
In Ubuntu if you go:
```

sudo /etc/init.d/mysql start

```

This will start the process. I believe the default behavior is that this will also set the process to start at boot time. If you go to "System Settings" (or whatever) if your control panel, you'll find a subsection called "system services" which also lets you modify what services start at runtime.

---

### Post by bruce89 on 2006-08-14
You can set commands to run on boot with Preferences>Sessions>Startup Programs.

---

### Post by moma on 2006-08-14
If it's a service script, do as "Kebes" says.
$ sudo /etc/init.d/servicename  start|restart|stop|status 

You can also manage services with "BUM" bootup and service manager.
$ sudo apt-get install bum 
$ [COLOR="Green"]sudo bum [/COLOR]
(Click Advanced mode, Services tab-page)
----

This said,
/etc/rc.local is the place where to put other programs and scripts to be executed at startup.
$ [COLOR="Green"]sudo gedit /etc/rc.local[/COLOR]

---


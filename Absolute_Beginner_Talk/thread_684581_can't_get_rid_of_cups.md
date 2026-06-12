---
title: "can't get rid of cups"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by randomjohn on 2008-02-01
How do I get rid of these cups errors that I'm seeing throughout my syslog?
 
```
Feb  1 10:05:43 white smbd[4876]: [2008/02/01 10:05:43, 0] printing/print_cups.c:cups_connect(69) 
Feb  1 10:05:43 white smbd[4876]:   Unable to connect to CUPS server localhost:631 - Connection refused 
Feb  1 10:05:43 white smbd[4876]: [2008/02/01 10:05:43, 0] printing/print_cups.c:cups_connect(69) 
Feb  1 10:05:43 white smbd[4876]:   Unable to connect to CUPS server localhost:631 - Connection refused 
```
 
There's no printer attached to that machine and there never will be. 
 
I removed cups and cupsys with aptitude, but 4 packages remained...
 
 
```
 
Failed to uninstall libcupsimage2 : dpkg: dependency problems prevent removal of libcupsimage2: libgs8 depends on libcupsimage2 (>= 1.3.0). splix depends on libcupsimage2 (>= 1.3.0).dpkg: error processing libcupsimage2 (--remove): dependency problems - not removingErrors were encountered while processing: libcupsimage2
Failed to uninstall libcupsys2 : 
dpkg: dependency problems prevent removal of libcupsys2: libcupsimage2 depends on libcupsys2 (>= 1.3.4). python-cups depends on libcupsys2 (>= 1.3.4). libgs8 depends on libcupsys2 (>= 1.3.4). splix depends on libcupsys2 (>= 1.3.0). libgnomecups1.0-1 depends on libcupsys2 (>= 1.2.3). libgtk2.0-0 depends on libcupsys2 (>= 1.3.4). libgnomeprint2.2-0 depends on libcupsys2 (>= 1.3.0). samba depends on libcupsys2 (>= 1.3.4).dpkg: error processing libcupsys2 (--remove): dependency problems - not removingErrors were encountered while processing: libcupsys2
Failed to uninstall libgnomecups1.0-1 : 
dpkg: dependency problems prevent removal of libgnomecups1.0-1: libgnomeprint2.2-0 depends on libgnomecups1.0-1 (>= 0.2.0).dpkg: error processing libgnomecups1.0-1 (--remove): dependency problems - not removingErrors were encountered while processing: libgnomecups1.0-1
Failed to uninstall python-cups : 
dpkg: dependency problems prevent removal of python-cups: system-config-printer-common depends on python-cups (>= 1.9.27).dpkg: error processing python-cups (--remove): dependency problems - not removingErrors were encountered while processing: python-cups
```
**and I need help doing this from the command line or from webmin. I don't have gui access to that computer.thanks in advance **

---

### Post by (((X))) on 2008-02-01
add --force option to your command to uninstall

---


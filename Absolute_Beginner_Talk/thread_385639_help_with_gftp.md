---
title: "help with gftp"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by progrockusa on 2007-03-15
ok i was trying to setup gftp awhile back but decided against it.
So i removed it with add/remove.
Now when i install things such as just recently i tried to install screenlets and i get this
```
Setting up proftpd (1.3.0-9ubuntu0.1) ...
 * Starting ftp server proftpd                                                   - IPv4 getaddrinfo 'prog-desktop' error: Name or service not known
 - warning: unable to determine IP address of 'prog-desktop'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'
                                                                         [fail]
invoke-rc.d: initscript proftpd, action "start" failed.
dpkg: error processing proftpd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 proftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
I want to completely remove this program
can anyone tell me what is going on here?
ty

---

### Post by heimo on 2007-03-15
Title says gftp, but the problem seems to be with proftpd? Try removing it with
```
sudo aptitude --purge remove proftpd
```And if necessary remove or move away /var/lib/dpkg/info/proftpd.*

EDIT: To move the files to your homedir, use:

```
 sudo mv /var/lib/dpkg/info/proftpd.* ~
```

---

### Post by progrockusa on 2007-03-16
tyvm that did the trick :)

---


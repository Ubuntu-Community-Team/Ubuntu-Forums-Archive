---
title: "How do I fix this error"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by eisle89 on 2006-10-19
I get this error message everytime I install something, how do I go about fixing it ?? ....... TIA

Errors were encountered while processing:
 postfix
 courier-pop
 courier-pop-ssl
 postfix-ldap
 postfix-dev

---

### Post by Grey on 2006-10-19
Open up a terminal, and try this command:

```

sudo apt-get -f install

```

It looks like there's some broken packages on your system, for some reason or another.  The above command will attempt to fix them.

---

### Post by eisle89 on 2006-10-19
OK, thank you. Now I have this

Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up postfix (2.2.10-1ubuntu0.1) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: fatal: myorigin parameter setting must not contain multiple values: John R. Dignan
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of courier-pop:
 courier-pop depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing courier-pop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of courier-pop-ssl:
 courier-pop-ssl depends on courier-pop; however:
  Package courier-pop is not configured yet.
dpkg: error processing courier-pop-ssl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postfix-dev:
 postfix-dev depends on postfix (>= 2.2.10-0); however:
  Package postfix is not configured yet.
 postfix-dev depends on postfix (<< 2.2.10.0-0); however:
  Package postfix is not configured yet.
dpkg: error processing postfix-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postfix-ldap:
 postfix-ldap depends on postfix; however:
  Package postfix is not configured yet.
 postfix-ldap depends on postfix (= 2.2.10-1ubuntu0.1); however:
  Package postfix is not configured yet.
dpkg: error processing postfix-ldap (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postfix
 courier-pop
 courier-pop-ssl
 postfix-dev
 postfix-ldap
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by eisle89 on 2006-10-19
And when I run postfix reload I get this

eisle89@eisle89-desktop:~$ sudo /etc/init.d/postfix reload
 * Reloading Postfix configuration... postfix: fatal: myorigin parameter setting must not contain multiple values: John R. Dignan

---

### Post by nickpaton on 2006-10-19
This post also deals with the same problem (& no solution either) 

[http://www.ubuntuforums.org/showthread.php?p=1637784]("http://www.ubuntuforums.org/showthread.php?p=1637784")

Worth keeping an eye on it for your answer maybe.

---


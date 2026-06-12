---
title: "mt-daapd not working after feisty upgrade"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by thewump on 2007-06-05
On one of my machines after a feist upgrade I'm getting this when I launch mt-daapd

Starting with debuglevel 2
Starting rendezvous daemon
*** WARNING *** The programme 'mt-daapd' uses the HOWL compatiblity layer of Avahi.
*** WARNING *** Please fix your application to use the native API of Avahi!
*** WARNING *** For more information see <http://0pointer.de/avahi-compat?s=howl&e=mt-daapd>
Starting signal handler
Error opening db: No backend database support for type: sqlite
Signal handler started
Stopping signal handler
Got shutdown signal. Notifying daap server.


Anybody know what is going on?  This doesn't make sense to me.  I'm still using the original mt-daapd.conf file from before upgrade.

TIA

Keith

---

### Post by Inxsible on 2007-06-05
the new kernel does give a lot of different problems to ppl. I would suggest you use the older version if you do not find a solution.

---


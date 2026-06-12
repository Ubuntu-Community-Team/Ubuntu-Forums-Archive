---
title: "SIOCADDRT: No such process"
date: 2008-04-12
forum: Arch and derivatives
---

### Post by AzraelUK on 2008-04-12
```
[root@peter-arch ~]# route add default gw 192.168.1.1
SIOCADDRT: No such process
[root@peter-arch ~]# /etc/rc.d/network restart
:: Stopping Network        [BUSY]
SIOCDELRT: No such process [FAIL]
:: Starting Network        [BUSY]
SIOCADDRT: No such process [FAIL]
[root@peter-arch ~]# WHY, LINUX, WHY!?
-bash: !?: event not found
```

---

### Post by fwojciec on 2008-04-12
This could be relevant to your problem: [http://bugs.archlinux.org/task/9960?string=network+restart&project=1&type%5B0%5D=&sev%5B0%5D=&pri%5B0%5D=&due%5B0%5D=&reported%5B0%5D=&cat%5B0%5D=&status%5B0%5D=open&percent%5B0%5D=&opened=&dev=&closed=&duedatefrom=&duedateto=&changedfrom=&changedto=&openedfrom=&openedto=&closedfrom=&closedto=]("http://bugs.archlinux.org/task/9960?string=network+restart&project=1&type%5B0%5D=&sev%5B0%5D=&pri%5B0%5D=&due%5B0%5D=&reported%5B0%5D=&cat%5B0%5D=&status%5B0%5D=open&percent%5B0%5D=&opened=&dev=&closed=&duedatefrom=&duedateto=&changedfrom=&changedto=&openedfrom=&openedto=&closedfrom=&closedto=")
See the comments for some workaroud suggestions -- or just use [netcfg2]("http://wiki.archlinux.org/index.php/Network_Profiles") instead of initscripts to connect to the network.

---

### Post by TheOrangePeanut on 2008-04-12
The bug that fwojciec posted is probably the reason.  If you have your network properly configured in rc.conf, restarting will give you the SIOCADDRT error, however, if you reboot the machine it will work on startup.  Give that a try?  It worked for me and I had the exact same error message.

---

### Post by AzraelUK on 2008-04-13
I've already got netcfg installed, but not netcfg2. They both use network profiles, though.

Now (ie. after `netcfg wlan0`) `route add default gw 192.168.1.1` says 'SIOCADDRT: File exists'. `route` will tell me that there's a route for .1.0, but not .1.1. And `iwconfig wlan0` hangs until I Ctrl+C.

Also, it seems NDISwrapper is upset: [URL="http://bbs.archlinux.org/viewtopic.php?pid=354913#p354913"]_[COLOR=Red]Main thread on Arch forums[/COLOR]_
[/URL]

---

### Post by AzraelUK on 2008-04-15
Still no luck. Using netcfg2, things still end up screwing up.

---

### Post by fwojciec on 2008-04-15
Sorry, I've no experience with NDISwrapper at all -- are you positive that there is no proper linux driver for your wifi card available?

---


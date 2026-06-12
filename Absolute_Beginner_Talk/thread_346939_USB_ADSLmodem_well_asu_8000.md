---
title: "USB ADSLmodem well asu 8000"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by pitrs on 2007-01-26
hello,
I have USB modem. I read some few threads about modem well asu 8000(accessRunner DSL) but no action.
I make: file cxacru-fw.bin copy to /lib/firmware, in file /etc/ppp/pap-secrets I write my ISP login and password and edit file /etc/ppp/options to:

```

plugin pppoatm.so 8.48
defaultroute
noipdefault
noauth
hide-password
nodetach
noccp
nobsdcomp
nodeflate
nopcomp
novj
novjccomp
user "my login"
lcp-echo-interval 20
lcp-echo-failure 10
persist
logfile /var/log/pppd.log

```

sudo pppd

In /var/log/pppd.log I get:

```

ussing interface ppp0
Connect: ppp0<-->8.48
connect(8.48): Address already in use
LCP: timeout sending Config-Reguests
Connection terminated
Modem hangup

```

LED USB and LINK shining but LED RX is ligtless.
Can anybody help me? and sorry,my english is horible, Im from Czech :D

I have Kubuntu 6.06

---

### Post by lee.eden on 2007-03-05
I'm stuck too.  I've got the same modem and even though I've tried to understand the detail at [http://ubuntuforums.org/showthread.php?t=10995]("http://ubuntuforums.org/showthread.php?t=10995") and [http://www.zullinux.it/linux/accessrunner.html]("http://www.zullinux.it/linux/accessrunner.html")  I have to admit I gave up after downloading [most of] the files I could find in step 1.  It just looks too complicated.  I'm pretty computer literate, but new to linux.

Is it just the AccessRunner modems which are so difficult to use in ubuntu or all USB modems?  Getting connected to the internet is now the main barrier to me starting to take ubuntu seriously as an alternative to XP (otherwise it looks great).

Can anybody offer a step-by-step guide for people like me?   (I think that most people with PCs at home are connecting via cheapest USB ADSL modems...)

[SIZE="1"]*dej mi vedet Pitre, jestli to rozlustis...*[/SIZE]

---


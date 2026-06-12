---
title: "SNMP and rrdtool"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by dpippin on 2008-02-11
When I try to install SNMP it says it is already installed and that it's at the newest version.  However, I cannot find it in /etc/default or /etc.  Same with rrdtool which also says it's installed is there a way to use the find command and find both programs?  I looked at the man page for find and I can't get it to search more than the current directory "find snmp"  etc.  Anyways running 7.10 gutsy SERVER.

---

### Post by wirelessmonkey on 2008-02-12
Well, if you want to have an snmp server, you&#314;l need to install snmpd
 # sudo apt-get install snmpd

the configuration file will be found in /etc/snmp/snmpd.conf

The snmpd is in /usr/sbin the snmp binary is in /usr/bin

The rrdtool binary is in /usr/bin


 (I highly suggest using cacti instead!)
Best of luck.

---


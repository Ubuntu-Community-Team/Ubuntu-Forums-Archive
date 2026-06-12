---
title: "db4-devel"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by m_well on 2008-03-18
when i  ran the make command for resiprocate/resip/repro
i was getting db_cxx.h not found error.....
but when i installed db4-devel package i.e. 
yum install db4-devel, it worked...there was no error.....

but if i try sudo apt-get install db4-devel,
i get "couldnt find package db4-devel" error....
what is that package name in ubuntu???
i have already installed db4.4-util in ubuntu....plz help.

---

### Post by kpkeerthi on 2008-03-18
You might need one of [these]("http://packages.ubuntu.com/source/gutsy/db4.2") **dev** packages

---

### Post by m_well on 2008-03-18
i installed the following packages:

db4.4-doc
db4.4-util
libdb4.4
libdb4.4++
libdb4.4++-dev
libdb4.4-dev
libdb4.4-tcl

my program has .cxx extensions so did not install those java packages....

now the make works without error...
but this is what i get when i try to run...

root@ubuntu710desktop:/home/user/resip2/repro#./repro
INFO | 20080318-055856.010 | repro | RESIP:DNS | 3080898240 | dns/AresDns.cxx:114 | DNS initialization: found  1 name servers
INFO | 20080318-055856.022 | repro | RESIP:DNS | 3080898240 | dns/AresDns.cxx:117 |  name server: 192.168.147.2
INFO | 20080318-055856.024 | repro | REPRO:APP | 3080898240 | repro.cxx:203 | V4 enabled
INFO | 20080318-055856.024 | repro | RESIP:TRANSPORT | 3080898240 | UdpTransport.cxx:42 | Creating UDP transport host= port=5060 ipv4=1
INFO | 20080318-055856.025 | repro | RESIP:TRANSPORT | 3080898240 | TcpTransport.cxx:28 | Creating TCP transport host= port=5060 ipv4=1
INFO | 20080318-055856.025 | repro | RESIP:TRANSPORT | 3080898240 | TlsTransport.cxx:38 | Creating TLS transport for domain  interface= port=5061
INFO | 20080318-055856.026 | repro | REPRO:APP | 3080898240 | BerkeleyDb.cxx:59 | Using BerkeleyDb prefixed with repro
terminate called after throwing an instance of 'DbException'
  what():  Dbc::get: Invalid argument
Aborted (core dumped)
root@ubuntu710desktop:/home/user/resip2/repro#


what shall i do now??:confused::(

---

### Post by m_well on 2008-03-18
those smilies above are not funny smilies.....its RESIP: DNS

HELP PLZZZZZ....HELP PLZZZZZ:(:(:(:(

---


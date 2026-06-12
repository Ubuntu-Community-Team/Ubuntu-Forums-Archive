---
title: "[SOLVED] no ip .com"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by ronaldor9 on 2007-11-19
does anyone know the protocol server name and all the other things i would have to replace with this file beacuse im using to no ip i tried looking and i couldint find it help please

syslog=yes
This gives you the ability to have a nice entry in your syslog-files.

use=if,   if=ppp0
By this, you specify that ddclient needs to look to the ppp0 interface. For normal DSL or Cable connections this will be your external interface.

protocol=dyndns2
Use the DYNDNS2 protocol (default)

server=members.dyndns.org   server=members.easydns.org
Update your account at dyndns.org or easydns.org


login=xxxxx   password=xxxxxx
Use these as your default login and password for the service that needs to be updated.

server=members.dyndns.org,   protocol=dyndns2, mydomain.dyndns.org
Update 'mydomain.dyndns.org' at dyndns.org (don't forget the comma's). You can add as many domains as you want. Just follow the same syntax for every seperate domain. Off course, the same goes for easydns :
   server=members.easydns.org,
   protocol=easydns,

---

### Post by tzulberti on 2007-11-20
To configure no-ip, y use "sudo no-ip -C" . But before that I install de package no-ip "sudo apt-get install no-ip".

---


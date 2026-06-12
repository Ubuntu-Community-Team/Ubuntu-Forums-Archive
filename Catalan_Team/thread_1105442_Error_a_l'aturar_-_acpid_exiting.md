---
title: "Error a l'aturar - acpid: exiting"
date: 2009-03-24
forum: Catalan Team
---

### Post by jinglada on 2009-03-24
Fa uns dies que a l'aturar l'Ubuntu es quedava bloquejat parpallejant amb les següents paraules: *acpid: exiting*

He cercat i he trobat la solució a:

[http://ubuntuforums.org/showthread.php?t=987699](http://ubuntuforums.org/showthread.php?t=987699)

Es tracta de fer:

*sudo gedit /etc/init.d/alsa-utils*
 
localitzar l'apartat *stop)* i afegir:

[I]ifconfig wlan0 down
ifconfig eth0 down[/I]

davant d'*EXITSTATUS=0*

---

### Post by CarlesOriol on 2009-03-25
Pot ser funcioni... però aturar la xarxa al autrar el servidor de so... em sembla una mica matusser.

---

### Post by jinglada on 2009-03-27
> **CarlesOriol said:**
> Pot ser funcioni... però aturar la xarxa al autrar el servidor de so... em sembla una mica matusser.

Què vol dir **acpid: exiting**?

Què s'hauria de fer que no fos matusser?

---

### Post by PatrickVogeli on 2009-03-28
es matusser, si, pero funciona... i total, quasi mai, pero no dir absolutamente mai, atures el servidor de so, excepte a l'apagar, per tant, tampoc es massa problema

salut!

---

### Post by jinglada on 2009-03-31
> **PatrickVogeli said:**
> es matusser, si, pero funciona... i total, quasi mai, pero no dir absolutamente mai, atures el servidor de so, excepte a l'apagar, per tant, tampoc es massa problema

salut!

Després de solucionar el tema del fil dels [auriculars/altaveus]("http://ubuntuforums.org/showthread.php?t=1108438") vaig treure les línies
[B]ifconfig wlan0 down
ifconfig eth0 down[/B]
del /etc/init.d/alsa-utils de l'apartat stop) davant d'EXITSTATUS=0 i ara no dóna l'error del títol d'aquest fil.:o

---


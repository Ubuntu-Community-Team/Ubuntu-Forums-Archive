---
title: "No arranca el MySQL"
date: 2011-07-07
forum: Catalan Team
---

### Post by jinglada on 2011-07-07
He instal·lat el LAMP amb el Synaptic i el el MySQL no arranca. Vet ací la seqüència del que ha passat:

joan@joan-laptop:~$ sudo /etc/init.d/mysql start mysql
[sudo] password for joan: 
Rather than invoking init scripts through /etc/init.d, use the service( 8 ) utility, e.g. service mysql start

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the start( 8 ) utility, e.g. start mysql
joan@joan-laptop:~$ service mysql start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.181" (uid=1000 pid=12115 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
joan@joan-laptop:~$ start mysql
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.182" (uid=1000 pid=12118 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

Em podeu orientar si us plau?

---

### Post by Kette on 2011-07-07
Amb la comanda que has posat demanes que s'executi un escript a /etc/init.d/ que es diu mysql i que rep com a argument start. Amb aquesta comanda l'hi sobra l'últim mysql. Ara aquests scripts, que servien per fer start, restart o stop els diferents serveis de la màquina com apache, ssh...,usen una sintaxi diferent, en aquest cas seria:
```
sudo service mysql start
```
Fes la prova a veure com va.
Salut

---

### Post by jinglada on 2011-07-07
> **Kette said:**
> Amb la comanda que has posat demanes que s'executi un escript a /etc/init.d/ que es diu mysql i que rep com a argument start. Amb aquesta comanda l'hi sobra l'últim mysql. Ara aquests scripts, que servien per fer start, restart o stop els diferents serveis de la màquina com apache, ssh...,usen una sintaxi diferent, en aquest cas seria:
```
sudo service mysql start
```
Fes la prova a veure com va.
Salut

Gràcies per la resposta, Kette. Mira què diu:
joan@joan-laptop:~$ sudo service mysql start
[sudo] password for joan: 
start: Job is already running: mysql

He reiniciat i em dóna el mateix.

---

### Post by wgarcia on 2011-07-08
I no està realment funcionant? Per exemple:

ps -ef | grep mysql

t'ho pot mostrar.

---

### Post by jinglada on 2011-07-08
> **wgarcia said:**
> I no està realment funcionant? Per exemple:

ps -ef | grep mysql

t'ho pot mostrar.

gràcies wgarcia. Mira què diu:

joan@joan-laptop:~$ ps -ef | grep mysql
mysql     1228     1  0 09:35 ?        00:00:00 /usr/sbin/mysqld
joan      3577  3505  0 11:41 pts/0    00:00:00 grep mysql

---

### Post by wgarcia on 2011-07-08
Doncs això vol dir que s'està executant, d'acord amb la primera línia. Què et fa pensar que no està corrent?

---

### Post by jinglada on 2011-07-08
> **wgarcia said:**
> Doncs això vol dir que s'està executant, d'acord amb la primera línia. Què et fa pensar que no està corrent?

Primer de tot: Gràcies. 
Segon, dir que és la primera vegada que el faig servir. 
Tercer, que em pensava que l'havia d'arrencar jo i tot sembla indicar que arrenca quan s'inicia l'ordinador.

---


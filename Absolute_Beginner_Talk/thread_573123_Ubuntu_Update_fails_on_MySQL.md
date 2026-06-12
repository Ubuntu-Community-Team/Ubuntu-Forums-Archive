---
title: "Ubuntu Update fails on MySQL"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by Nizzle on 2007-10-11
Yesterday I installed LAMP on my Ubuntu 7.04 Desktop through Synamptic.. for testing some stuff..
all went fine.. worked perfectly.. I abused the MySQL all day with trying to learn queries

now today ubuntu says there's an update.. or alot of updates.. and all worked except 2.. which are "mysql-server" and "mysql-server-5.0"

the Update-manager tells me this:
> E: /var/cache/apt/archives/mysql-server_5.0.38-0ubuntu1.1_all.deb: subproces pre-installation script gaf een foutwaarde 1 terug
E: /var/cache/apt/archives/mysql-server-5.0_5.0.38-0ubuntu1.1_i386.deb: subproces nieuw pre-removal script gaf een foutwaarde 1 terug

and through terminal with the "sudo apt-get upgrade" I get this:
> niels@niels-desktop:~$ sudo apt-get upgrade
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
Reading state information... Klaar
De volgende pakketten zullen opgewaardeerd worden:
  mysql-server mysql-server-5.0
2 pakketten opgewaardeerd, 0 nieuwe pakketten geïnstalleerd, 0 verwijderen en 0 niet opgewaardeerd.
Er moeten 0B/25,8MB aan archieven opgehaald worden.
Na het uitpakken zal er 0B extra schijfruimte gebruikt worden.
Wilt u doorgaan [J/n]? j
Voorconfigureren van pakketten...
(Database inlezen ... 181928 bestanden en mappen geïnstalleerd.)
Voorbereiden om mysql-server 5.0.38-0ubuntu1 te vervangen (door .../mysql-server_5.0.38-0ubuntu1.1_all.deb) ...
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
invoke-rc.d returned 1
There is a MySQL server running, but we failed in our attempts to stop it.
Stop it yourself and try again!
dpkg: fout bij afhandelen van /var/cache/apt/archives/mysql-server_5.0.38-0ubuntu1.1_all.deb (--unpack):
 subproces pre-installation script gaf een foutwaarde 1 terug
dpkg: verwijdering van mysql-server ten gunste van mysql-server-5.0 wordt overwogen...
dpkg: ja, mysql-server wordt verwijderd ten gunste van mysql-server-5.0.
Voorbereiden om mysql-server-5.0 5.0.38-0ubuntu1 te vervangen (door .../mysql-server-5.0_5.0.38-0ubuntu1.1_i386.deb) ...
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: waarschuwing - verouderd pre-removal script gaf een foutcode 1
dpkg - script uit het nieuwe pakket wordt geprobeerd ...
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: fout bij afhandelen van /var/cache/apt/archives/mysql-server-5.0_5.0.38-0ubuntu1.1_i386.deb (--unpack):
 subproces nieuw pre-removal script gaf een foutwaarde 1 terug
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
 * Starting MySQL database server mysqld                                 [ OK ] 
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
Fouten gevonden tijdens behandelen van:
 /var/cache/apt/archives/mysql-server_5.0.38-0ubuntu1.1_all.deb
 /var/cache/apt/archives/mysql-server-5.0_5.0.38-0ubuntu1.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
niels@niels-desktop:~$ 

I've searched around the forums but nobody seems to have the same problem :confused:
or they just didn't post it yet.. :p

sooo.. does anyone have any idea what I should do?
oh and yeah I know my ubuntu is Dutch but I can try to translate it for you if you need it..

---

### Post by PhilOSparta on 2007-10-11
I just had the same problem with the update.  The error messages indicate that the update manager couldn't stop the mysql server.

I went into a terminal and did the following to stop the server:
**sudo cat /var/run/mysqld/mysqld.pid **    (it should return the process id of the mysql server if its running)
Then type '**sudo kill **' and the number you got from the command above.

Then go back and run the update manager.  That fixed it for me.

Good luck.

Phil

---

### Post by Nizzle on 2007-10-11
yup that worked :mrgreen:

thanks alot :)
here have some popcorn :popcorn:

---

### Post by Hajo Harts on 2008-01-02
I had the same problem. Stopping the mysql process as described solved it. So also soem popcorn from me!:popcorn:

---

### Post by hyper_ch on 2008-01-02
I think the "debian-sys-maint" isn't in the mysql DBs or does not have sufficient rights. That one is normally being used by apt.

---


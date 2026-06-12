---
title: "help on installing postgreSQL"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2007-05-23
need help on instlaling postgre SQL plz help
```
zerobinary@zerobinary:~$ sudo apt-get install postgresql-8.2
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
postgresql-8.2 is already the newest version.
postgresql-8.2 set to manual installed.
The following packages were automatically installed and are no longer required:
  artsbuilder python-kiwi libgtk-jni libpcrecpp0 libcairo-java
  libbluetooth2-dev libusb-dev librpcsecgss2 libjasper-runtime libgmp3c2
  libxml++2.6c2a libglib-java docker python-setuptools libpq4 gazpacho
  libgconfmm-2.6-1c2 mkvtoolnix libswt3.2-gtk-jni libimlib2 multisync
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up postgresql-8.2 (8.2.4-1~edgy1) ...
 * Starting PostgreSQL 8.2 database server                                       * The PostgreSQL server failed to start. Please check the log output:
2007-05-23 18:06:52 PDT LOG:  could not load root certificate file "root.crt": no SSL error reported
2007-05-23 18:06:52 PDT DETAIL:  Will not verify client certificates.
2007-05-23 18:06:53 PDT LOG:  could not translate host name "localhost", service "5432" to address: Name or service not known
2007-05-23 18:06:53 PDT WARNING:  could not create listen socket for "localhost"
2007-05-23 18:06:53 PDT FATAL:  could not create any TCP/IP sockets
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.2, action "start" failed.
dpkg: error processing postgresql-8.2 (--configure):

```
```
E: postgresql-8.2: subprocess post-installation script returned error exit status 1
E: postgresql-plpython-8.2: dependency problems - leaving unconfigured
E: glom: dependency problems - leaving unconfigured
E: postgresql-contrib-8.2: dependency problems - leaving unconfigured

```

---

### Post by Pragmatist on 2007-05-25
It looks  like you have the software, you just need to configure it.

Have you looked at this yet?:
[https://help.ubuntu.com/community/PostgreSQL](https://help.ubuntu.com/community/PostgreSQL)

---

### Post by zerobinary on 2007-05-25
but i seems like a bug to me i don't use sudo apt-get install command fter postgresql is installed nor is removed by the force command

---

### Post by Pragmatist on 2007-05-25
> **zerobinary said:**
> ...nor is removed by the **force command**

What was removed?  What is the "force command"?

---

### Post by zerobinary on 2007-05-25
```
zerobinary@zerobinary:~$  sudo apt-get install pgadmin3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  artsbuilder python-kiwi libgtk-jni libpcrecpp0 libcairo-java
  libbluetooth2-dev libusb-dev librpcsecgss2 libjasper-runtime libgmp3c2
  libglib-java docker python-setuptools gazpacho mkvtoolnix libswt3.2-gtk-jni
  libimlib2 multisync
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  pgadmin3-data
Recommended packages:
  pgagent
The following NEW packages will be installed:
  pgadmin3 pgadmin3-data
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 4693kB of archives.
After unpacking 18.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com feisty/universe pgadmin3-data 1.4.3-2ubuntu1 [2545kB]
Get:2 http://us.archive.ubuntu.com feisty/universe pgadmin3 1.4.3-2ubuntu1 [2148kB]
Fetched 4693kB in 1m10s (66.9kB/s)                                             
Selecting previously deselected package pgadmin3-data.
(Reading database ... 160492 files and directories currently installed.)
Unpacking pgadmin3-data (from .../pgadmin3-data_1.4.3-2ubuntu1_all.deb) ...
Selecting previously deselected package pgadmin3.
Unpacking pgadmin3 (from .../pgadmin3_1.4.3-2ubuntu1_i386.deb) ...
Setting up postgresql-8.2 (8.2.4-1~edgy1) ...
 * Starting PostgreSQL 8.2 database server                                       * The PostgreSQL server failed to start. Please check the log output:
2007-05-25 18:20:41 PDT LOG:  could not load root certificate file "root.crt": no SSL error reported
2007-05-25 18:20:41 PDT DETAIL:  Will not verify client certificates.
2007-05-25 18:20:41 PDT LOG:  could not translate host name "localhost", service "5432" to address: Name or service not known
2007-05-25 18:20:41 PDT WARNING:  could not create listen socket for "localhost"
2007-05-25 18:20:41 PDT FATAL:  could not create any TCP/IP sockets
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.2, action "start" failed.
dpkg: error processing postgresql-8.2 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of glom:
 glom depends on postgresql-8.2; however:
  Package postgresql-8.2 is not configured yet.
dpkg: error processing glom (--configure):
 dependency problems - leaving unconfigured
Setting up postgresql-8.1 (8.1.8-1ubuntu3) ...
 * Starting PostgreSQL 8.1 database server                                       * The PostgreSQL server failed to start. Please check the log output:
2007-05-25 18:20:42 PDT LOG:  could not load root certificate file "root.crt": No SSL error reported
2007-05-25 18:20:42 PDT DETAIL:  Will not verify client certificates.
2007-05-25 18:20:42 PDT LOG:  could not translate host name "localhost", service "5433" to address: Name or service not known
2007-05-25 18:20:42 PDT WARNING:  could not create listen socket for "localhost"
2007-05-25 18:20:42 PDT FATAL:  could not create any TCP/IP sockets
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.1, action "start" failed.
dpkg: error processing postgresql-8.1 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of postgresql-contrib-8.2:
 postgresql-contrib-8.2 depends on postgresql-8.2; however:
  Package postgresql-8.2 is not configured yet.
dpkg: error processing postgresql-contrib-8.2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql-plpython-8.2:
 postgresql-plpython-8.2 depends on postgresql-8.2; however:
  Package postgresql-8.2 is not configured yet.
dpkg: error processing postgresql-plpython-8.2 (--configure):
 dependency problems - leaving unconfigured
Setting up pgadmin3-data (1.4.3-2ubuntu1) ...
Setting up pgadmin3 (1.4.3-2ubuntu1) ...

Errors were encountered while processing:
 postgresql-8.2
 glom
 postgresql-8.1
 postgresql-contrib-8.2
 postgresql-plpython-8.2
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
the force command is sudo dpkg -r --force-all [stgreql-8.2

---

### Post by Pragmatist on 2007-06-01
In general, using the force option with any command is a bad idea unless you really know what your doing, and even then it still is usually a bad idea. :)

What happens if you use a GUI package manager such as Synaptic?  Can you try and reinstall (or even better, uninstall completely and then install) the postgreSQL packages?

---

### Post by Pragmatist on 2007-06-01
Nevermind, I see you've created more threads on this problem.

---

### Post by zerobinary on 2007-06-05
how do u configure it or remove it i need help

---

### Post by Pragmatist on 2007-06-05
Follow these instructions and "completely remove" postgreSQL:

[https://help.ubuntu.com/community/SynapticHowto?highlight=%28synaptic%29](https://help.ubuntu.com/community/SynapticHowto?highlight=%28synaptic%29)

then run these commands:
When you run this next command, you need to wait a few minutes for it to finish:
```
sudo updatedb
```

Now type this and post the output here (do this AFTER you completely uninstall postgreSQL):

```
locate postgresql
```

---

### Post by zerobinary on 2007-06-06
u mena this 
```
How to fix broken packages

warning.png 'Broken packages' are packages that have unsatisfied dependencies. If broken packages are detected, Synaptic will not allow any further changes to the system until all broken packages have been fixed.

    *

      To fix broken packages
          o

            Choose Edit > Fix Broken Packages from the menu.
          o

            Choose Apply Marked Changes from the Edit menu or press Ctrl + P.
          o

            Confirm the summary of changes and click Apply.

```
but which package should i remove apt ????but it say it will be unstable if i remove it

---

### Post by Pragmatist on 2007-06-06
Did you follow the instructions (i.e. fix the broken packages) that are contained in the post you just made?

---

### Post by zerobinary on 2007-06-06
i did try to complete removal but i got this
```
E: postgresql-8.2: subprocess post-installation script returned error exit status 1
E: glom: dependency problems - leaving unconfigured
E: postgresql-contrib-8.2: dependency problems - leaving unconfigured
E: postgresql-plpython-8.2: dependency problems - leaving unconfigured
```
and i don't get this 
   ```
 *

      To fix broken packages
          o

            Choose Edit > Fix Broken Packages from the menu.
          o

            Choose Apply Marked Changes from the Edit menu or press Ctrl + P.
          o

            Confirm the summary of changes and click Apply.

```
what do they mean by 
            Choose Apply Marked Changes from the Edit menu or press Ctrl + P.
when i choose fix broken packages nothing pops up
and which one to remove i mean there is a lot of postsql

---

### Post by Pragmatist on 2007-06-06
This is a quote from the dpkg man page:

>        --force-things | --no-force-things | --refuse-things

              Force or refuse (no-force and refuse mean the same thing) to do  some  things.  things  is  a  comma
              separated  list  of things specified below. --force-help displays a message describing them.  Things
              marked with (*) are forced by default.

[B]              Warning: These options are mostly intended to be used by experts  only.  Using  them  without  fully
              understanding their effects may _break your whole system_.[/B]

              all: Turns on (or off) all force options.


Since you used the force-all option, my advice is to reinstall Ubuntu and start over.

---

### Post by zerobinary on 2007-06-06
thx for ur help but i can't reinstall it now
dpkg - warning: ignoring request to remove postgresql which isn't installed.
and for the output of ur command u told me to use is 
```
/usr/share/postgresql/8.1/timezone/Europe/Vaduz
/usr/share/postgresql/8.1/timezone/Europe/Vilnius
/usr/share/postgresql/8.1/timezone/Europe/Chisinau
/usr/share/postgresql/8.1/timezone/Europe/Malta
/usr/share/postgresql/8.1/timezone/Europe/Amsterdam
/usr/share/postgresql/8.1/timezone/Europe/Monaco
/usr/share/postgresql/8.1/timezone/Europe/Bucharest
/usr/share/postgresql/8.1/timezone/Europe/Oslo
/usr/share/postgresql/8.1/timezone/Europe/Warsaw
/usr/share/postgresql/8.1/timezone/Europe/Lisbon
/usr/share/postgresql/8.1/timezone/Europe/Kaliningrad
/usr/share/postgresql/8.1/timezone/Europe/Moscow
/usr/share/postgresql/8.1/timezone/Europe/Volgograd
/usr/share/postgresql/8.1/timezone/Europe/Samara
/usr/share/postgresql/8.1/timezone/Europe/Belgrade
/usr/share/postgresql/8.1/timezone/Europe/Madrid
/usr/share/postgresql/8.1/timezone/Europe/Stockholm
/usr/share/postgresql/8.1/timezone/Europe/Zurich
/usr/share/postgresql/8.1/timezone/Europe/Istanbul
/usr/share/postgresql/8.1/timezone/Europe/Kiev
/usr/share/postgresql/8.1/timezone/Europe/Uzhgorod
/usr/share/postgresql/8.1/timezone/Europe/Zaporozhye
/usr/share/postgresql/8.1/timezone/Europe/Simferopol
/usr/share/postgresql/8.1/timezone/Europe/Nicosia
/usr/share/postgresql/8.1/timezone/Europe/Jersey
/usr/share/postgresql/8.1/timezone/Europe/Guernsey
/usr/share/postgresql/8.1/timezone/Europe/Isle_of_Man
/usr/share/postgresql/8.1/timezone/Europe/Mariehamn
/usr/share/postgresql/8.1/timezone/Europe/Vatican
/usr/share/postgresql/8.1/timezone/Europe/San_Marino
/usr/share/postgresql/8.1/timezone/Europe/Ljubljana
/usr/share/postgresql/8.1/timezone/Europe/Podgorica
/usr/share/postgresql/8.1/timezone/Europe/Sarajevo
/usr/share/postgresql/8.1/timezone/Europe/Skopje
/usr/share/postgresql/8.1/timezone/Europe/Zagreb
/usr/share/postgresql/8.1/timezone/Europe/Bratislava
/usr/share/postgresql/8.1/timezone/Europe/Belfast
/usr/share/postgresql/8.1/timezone/Europe/Tiraspol
/usr/share/postgresql/8.1/timezone/Factory
/usr/share/postgresql/8.1/timezone/HST
/usr/share/postgresql/8.1/timezone/Indian
/usr/share/postgresql/8.1/timezone/Indian/Antananarivo
/usr/share/postgresql/8.1/timezone/Indian/Comoro
/usr/share/postgresql/8.1/timezone/Indian/Mauritius
/usr/share/postgresql/8.1/timezone/Indian/Mayotte
/usr/share/postgresql/8.1/timezone/Indian/Reunion
/usr/share/postgresql/8.1/timezone/Indian/Mahe
/usr/share/postgresql/8.1/timezone/Indian/Kerguelen
/usr/share/postgresql/8.1/timezone/Indian/Chagos
/usr/share/postgresql/8.1/timezone/Indian/Maldives
/usr/share/postgresql/8.1/timezone/Indian/Christmas
/usr/share/postgresql/8.1/timezone/Indian/Cocos
/usr/share/postgresql/8.1/timezone/MET
/usr/share/postgresql/8.1/timezone/Mexico
/usr/share/postgresql/8.1/timezone/Mexico/BajaNorte
/usr/share/postgresql/8.1/timezone/Mexico/BajaSur
/usr/share/postgresql/8.1/timezone/Mexico/General
/usr/share/postgresql/8.1/timezone/Mideast
/usr/share/postgresql/8.1/timezone/Mideast/Riyadh87
/usr/share/postgresql/8.1/timezone/Mideast/Riyadh88
/usr/share/postgresql/8.1/timezone/Mideast/Riyadh89
/usr/share/postgresql/8.1/timezone/MST
/usr/share/postgresql/8.1/timezone/MST7MDT
/usr/share/postgresql/8.1/timezone/Pacific
/usr/share/postgresql/8.1/timezone/Pacific/Port_Moresby
/usr/share/postgresql/8.1/timezone/Pacific/Rarotonga
/usr/share/postgresql/8.1/timezone/Pacific/Fiji
/usr/share/postgresql/8.1/timezone/Pacific/Gambier
/usr/share/postgresql/8.1/timezone/Pacific/Marquesas
/usr/share/postgresql/8.1/timezone/Pacific/Tahiti
/usr/share/postgresql/8.1/timezone/Pacific/Guam
/usr/share/postgresql/8.1/timezone/Pacific/Tarawa
/usr/share/postgresql/8.1/timezone/Pacific/Enderbury
/usr/share/postgresql/8.1/timezone/Pacific/Kiritimati
/usr/share/postgresql/8.1/timezone/Pacific/Saipan
/usr/share/postgresql/8.1/timezone/Pacific/Majuro
/usr/share/postgresql/8.1/timezone/Pacific/Kwajalein
/usr/share/postgresql/8.1/timezone/Pacific/Truk
/usr/share/postgresql/8.1/timezone/Pacific/Ponape
/usr/share/postgresql/8.1/timezone/Pacific/Kosrae
/usr/share/postgresql/8.1/timezone/Pacific/Nauru
/usr/share/postgresql/8.1/timezone/Pacific/Noumea
/usr/share/postgresql/8.1/timezone/Pacific/Auckland
/usr/share/postgresql/8.1/timezone/Pacific/Chatham
/usr/share/postgresql/8.1/timezone/Pacific/Niue
/usr/share/postgresql/8.1/timezone/Pacific/Norfolk
/usr/share/postgresql/8.1/timezone/Pacific/Palau
/usr/share/postgresql/8.1/timezone/Pacific/Pitcairn
/usr/share/postgresql/8.1/timezone/Pacific/Pago_Pago
/usr/share/postgresql/8.1/timezone/Pacific/Apia
/usr/share/postgresql/8.1/timezone/Pacific/Guadalcanal
/usr/share/postgresql/8.1/timezone/Pacific/Fakaofo
/usr/share/postgresql/8.1/timezone/Pacific/Tongatapu
/usr/share/postgresql/8.1/timezone/Pacific/Funafuti
/usr/share/postgresql/8.1/timezone/Pacific/Johnston
/usr/share/postgresql/8.1/timezone/Pacific/Midway
/usr/share/postgresql/8.1/timezone/Pacific/Wake
/usr/share/postgresql/8.1/timezone/Pacific/Efate
/usr/share/postgresql/8.1/timezone/Pacific/Wallis
/usr/share/postgresql/8.1/timezone/Pacific/Honolulu
/usr/share/postgresql/8.1/timezone/Pacific/Easter
/usr/share/postgresql/8.1/timezone/Pacific/Galapagos
/usr/share/postgresql/8.1/timezone/Pacific/Samoa
/usr/share/postgresql/8.1/timezone/Pacific/Yap
/usr/share/postgresql/8.1/timezone/PST8PDT
/usr/share/postgresql/8.1/timezone/US
/usr/share/postgresql/8.1/timezone/US/East-Indiana
/usr/share/postgresql/8.1/timezone/US/Pacific-New
/usr/share/postgresql/8.1/timezone/US/Alaska
/usr/share/postgresql/8.1/timezone/US/Aleutian
/usr/share/postgresql/8.1/timezone/US/Arizona
/usr/share/postgresql/8.1/timezone/US/Central
/usr/share/postgresql/8.1/timezone/US/Indiana-Starke
/usr/share/postgresql/8.1/timezone/US/Eastern
/usr/share/postgresql/8.1/timezone/US/Hawaii
/usr/share/postgresql/8.1/timezone/US/Michigan
/usr/share/postgresql/8.1/timezone/US/Mountain
/usr/share/postgresql/8.1/timezone/US/Pacific
/usr/share/postgresql/8.1/timezone/US/Samoa
/usr/share/postgresql/8.1/timezone/WET
/usr/share/postgresql/8.1/timezone/Cuba
/usr/share/postgresql/8.1/timezone/Egypt
/usr/share/postgresql/8.1/timezone/Eire
/usr/share/postgresql/8.1/timezone/GB
/usr/share/postgresql/8.1/timezone/GB-Eire
/usr/share/postgresql/8.1/timezone/GMT
/usr/share/postgresql/8.1/timezone/GMT+0
/usr/share/postgresql/8.1/timezone/GMT-0
/usr/share/postgresql/8.1/timezone/GMT0
/usr/share/postgresql/8.1/timezone/Greenwich
/usr/share/postgresql/8.1/timezone/Hongkong
/usr/share/postgresql/8.1/timezone/Iceland
/usr/share/postgresql/8.1/timezone/Iran
/usr/share/postgresql/8.1/timezone/Israel
/usr/share/postgresql/8.1/timezone/Jamaica
/usr/share/postgresql/8.1/timezone/Japan
/usr/share/postgresql/8.1/timezone/Kwajalein
/usr/share/postgresql/8.1/timezone/Libya
/usr/share/postgresql/8.1/timezone/Navajo
/usr/share/postgresql/8.1/timezone/NZ
/usr/share/postgresql/8.1/timezone/NZ-CHAT
/usr/share/postgresql/8.1/timezone/Poland
/usr/share/postgresql/8.1/timezone/Portugal
/usr/share/postgresql/8.1/timezone/PRC
/usr/share/postgresql/8.1/timezone/ROC
/usr/share/postgresql/8.1/timezone/ROK
/usr/share/postgresql/8.1/timezone/Singapore
/usr/share/postgresql/8.1/timezone/Turkey
/usr/share/postgresql/8.1/timezone/UCT
/usr/share/postgresql/8.1/timezone/Universal
/usr/share/postgresql/8.1/timezone/UTC
/usr/share/postgresql/8.1/timezone/W-SU
/usr/share/postgresql/8.1/timezone/Zulu
/usr/share/postgresql/8.1/man
/usr/share/postgresql/8.1/man/man1
/usr/share/postgresql/8.1/man/man1/clusterdb.1.gz
/usr/share/postgresql/8.1/man/man1/psql.1.gz
/usr/share/postgresql/8.1/man/man1/pg_controldata.1.gz
/usr/share/postgresql/8.1/man/man1/pg_dump.1.gz
/usr/share/postgresql/8.1/man/man1/pg_dumpall.1.gz
/usr/share/postgresql/8.1/man/man1/createdb.1.gz
/usr/share/postgresql/8.1/man/man1/createlang.1.gz
/usr/share/postgresql/8.1/man/man1/dropdb.1.gz
/usr/share/postgresql/8.1/man/man1/droplang.1.gz
/usr/share/postgresql/8.1/man/man1/dropuser.1.gz
/usr/share/postgresql/8.1/man/man1/reindexdb.1.gz
/usr/share/postgresql/8.1/man/man1/pg_restore.1.gz
/usr/share/postgresql/8.1/man/man1/vacuumdb.1.gz
/usr/share/postgresql/8.1/man/man1/createuser.1.gz
/usr/share/postgresql/8.1/man/man1/pg_resetxlog.1.gz
/usr/share/postgresql/8.1/man/man1/pg_ctl.1.gz
/usr/share/postgresql/8.1/man/man1/postgres.1.gz
/usr/share/postgresql/8.1/man/man1/initdb.1.gz
/usr/share/postgresql/8.1/man/man1/ipcclean.1.gz
/usr/share/postgresql/8.1/man/man1/postmaster.1.gz
/usr/share/postgresql/8.1/man/man7
/usr/share/postgresql/8.1/man/man7/alter_operator_class.7.gz
/usr/share/postgresql/8.1/man/man7/alter_conversion.7.gz
/usr/share/postgresql/8.1/man/man7/alter_database.7.gz
/usr/share/postgresql/8.1/man/man7/alter_domain.7.gz
/usr/share/postgresql/8.1/man/man7/alter_function.7.gz
/usr/share/postgresql/8.1/man/man7/alter_group.7.gz
/usr/share/postgresql/8.1/man/man7/alter_index.7.gz
/usr/share/postgresql/8.1/man/man7/alter_language.7.gz
/usr/share/postgresql/8.1/man/man7/alter_schema.7.gz
/usr/share/postgresql/8.1/man/man7/alter_role.7.gz
/usr/share/postgresql/8.1/man/man7/alter_tablespace.7.gz
/usr/share/postgresql/8.1/man/man7/alter_sequence.7.gz
/usr/share/postgresql/8.1/man/man7/alter_table.7.gz
/usr/share/postgresql/8.1/man/man7/create_aggregate.7.gz
/usr/share/postgresql/8.1/man/man7/alter_trigger.7.gz
/usr/share/postgresql/8.1/man/man7/alter_type.7.gz
/usr/share/postgresql/8.1/man/man7/analyze.7.gz
/usr/share/postgresql/8.1/man/man7/begin.7.gz
/usr/share/postgresql/8.1/man/man7/checkpoint.7.gz
/usr/share/postgresql/8.1/man/man7/close.7.gz
/usr/share/postgresql/8.1/man/man7/cluster.7.gz
/usr/share/postgresql/8.1/man/man7/comment.7.gz
/usr/share/postgresql/8.1/man/man7/commit.7.gz
/usr/share/postgresql/8.1/man/man7/copy.7.gz
/usr/share/postgresql/8.1/man/man7/create_conversion.7.gz
/usr/share/postgresql/8.1/man/man7/create_cast.7.gz
/usr/share/postgresql/8.1/man/man7/drop_cast.7.gz
/usr/share/postgresql/8.1/man/man7/delete.7.gz
/usr/share/postgresql/8.1/man/man7/create_constraint_trigger.7.gz
/usr/share/postgresql/8.1/man/man7/create_database.7.gz
/usr/share/postgresql/8.1/man/man7/create_domain.7.gz
/usr/share/postgresql/8.1/man/man7/create_function.7.gz
/usr/share/postgresql/8.1/man/man7/create_group.7.gz
/usr/share/postgresql/8.1/man/man7/create_index.7.gz
/usr/share/postgresql/8.1/man/man7/create_operator.7.gz
/usr/share/postgresql/8.1/man/man7/create_operator_class.7.gz
/usr/share/postgresql/8.1/man/man7/create_role.7.gz
/usr/share/postgresql/8.1/man/man7/create_rule.7.gz
/usr/share/postgresql/8.1/man/man7/create_schema.7.gz
/usr/share/postgresql/8.1/man/man7/create_sequence.7.gz
/usr/share/postgresql/8.1/man/man7/create_table.7.gz
/usr/share/postgresql/8.1/man/man7/create_table_as.7.gz
/usr/share/postgresql/8.1/man/man7/create_tablespace.7.gz
/usr/share/postgresql/8.1/man/man7/create_trigger.7.gz
/usr/share/postgresql/8.1/man/man7/create_type.7.gz
/usr/share/postgresql/8.1/man/man7/create_user.7.gz
/usr/share/postgresql/8.1/man/man7/create_view.7.gz
/usr/share/postgresql/8.1/man/man7/deallocate.7.gz
/usr/share/postgresql/8.1/man/man7/declare.7.gz
/usr/share/postgresql/8.1/man/man7/drop_operator_class.7.gz
/usr/share/postgresql/8.1/man/man7/drop_conversion.7.gz
/usr/share/postgresql/8.1/man/man7/drop_database.7.gz
/usr/share/postgresql/8.1/man/man7/drop_domain.7.gz
/usr/share/postgresql/8.1/man/man7/drop_function.7.gz
/usr/share/postgresql/8.1/man/man7/drop_group.7.gz
/usr/share/postgresql/8.1/man/man7/drop_index.7.gz
/usr/share/postgresql/8.1/man/man7/drop_language.7.gz
/usr/share/postgresql/8.1/man/man7/drop_schema.7.gz
/usr/share/postgresql/8.1/man/man7/drop_role.7.gz
/usr/share/postgresql/8.1/man/man7/drop_rule.7.gz
/usr/share/postgresql/8.1/man/man7/drop_tablespace.7.gz
/usr/share/postgresql/8.1/man/man7/drop_sequence.7.gz
/usr/share/postgresql/8.1/man/man7/drop_table.7.gz
/usr/share/postgresql/8.1/man/man7/release_savepoint.7.gz
/usr/share/postgresql/8.1/man/man7/drop_trigger.7.gz
/usr/share/postgresql/8.1/man/man7/drop_type.7.gz
/usr/share/postgresql/8.1/man/man7/drop_user.7.gz
/usr/share/postgresql/8.1/man/man7/end.7.gz
/usr/share/postgresql/8.1/man/man7/execute.7.gz
/usr/share/postgresql/8.1/man/man7/explain.7.gz
/usr/share/postgresql/8.1/man/man7/fetch.7.gz
/usr/share/postgresql/8.1/man/man7/grant.7.gz
/usr/share/postgresql/8.1/man/man7/insert.7.gz
/usr/share/postgresql/8.1/man/man7/listen.7.gz
/usr/share/postgresql/8.1/man/man7/load.7.gz
/usr/share/postgresql/8.1/man/man7/lock.7.gz
/usr/share/postgresql/8.1/man/man7/notify.7.gz
/usr/share/postgresql/8.1/man/man7/prepare.7.gz
/usr/share/postgresql/8.1/man/man7/reindex.7.gz
/usr/share/postgresql/8.1/man/man7/rollback.7.gz
/usr/share/postgresql/8.1/man/man7/reset.7.gz
/usr/share/postgresql/8.1/man/man7/revoke.7.gz
/usr/share/postgresql/8.1/man/man7/rollback_to_savepoint.7.gz
/usr/share/postgresql/8.1/man/man7/rollback_prepared.7.gz
/usr/share/postgresql/8.1/man/man7/select_into.7.gz
/usr/share/postgresql/8.1/man/man7/savepoint.7.gz
/usr/share/postgresql/8.1/man/man7/select.7.gz
/usr/share/postgresql/8.1/man/man7/set_constraints.7.gz
/usr/share/postgresql/8.1/man/man7/set.7.gz
/usr/share/postgresql/8.1/man/man7/set_transaction.7.gz
/usr/share/postgresql/8.1/man/man7/set_role.7.gz
/usr/share/postgresql/8.1/man/man7/spi_connect.7.gz
/usr/share/postgresql/8.1/man/man7/show.7.gz
/usr/share/postgresql/8.1/man/man7/spi_cursor_close.7.gz
/usr/share/postgresql/8.1/man/man7/spi_copytuple.7.gz
/usr/share/postgresql/8.1/man/man7/prepare_transaction.7.gz
/usr/share/postgresql/8.1/man/man7/spi_cursor_fetch.7.gz
/usr/share/postgresql/8.1/man/man7/spi_cursor_find.7.gz
/usr/share/postgresql/8.1/man/man7/spi_cursor_move.7.gz
/usr/share/postgresql/8.1/man/man7/spi_cursor_open.7.gz
/usr/share/postgresql/8.1/man/man7/spi_exec.7.gz
/usr/share/postgresql/8.1/man/man7/spi_execp.7.gz
/usr/share/postgresql/8.1/man/man7/spi_execute.7.gz
/usr/share/postgresql/8.1/man/man7/spi_execute_plan.7.gz
/usr/share/postgresql/8.1/man/man7/spi_finish.7.gz
/usr/share/postgresql/8.1/man/man7/spi_fname.7.gz
/usr/share/postgresql/8.1/man/man7/spi_fnumber.7.gz
/usr/share/postgresql/8.1/man/man7/spi_freetuple.7.gz
/usr/share/postgresql/8.1/man/man7/spi_freetuptable.7.gz
/usr/share/postgresql/8.1/man/man7/spi_getargcount.7.gz
/usr/share/postgresql/8.1/man/man7/spi_getargtypeid.7.gz
/usr/share/postgresql/8.1/man/man7/spi_getbinval.7.gz
/usr/share/postgresql/8.1/man/man7/spi_getnspname.7.gz
/usr/share/postgresql/8.1/man/man7/spi_getrelname.7.gz
/usr/share/postgresql/8.1/man/man7/spi_gettype.7.gz
/usr/share/postgresql/8.1/man/man7/spi_getvalue.7.gz
/usr/share/postgresql/8.1/man/man7/spi_is_cursor_plan.7.gz
/usr/share/postgresql/8.1/man/man7/spi_modifytuple.7.gz
/usr/share/postgresql/8.1/man/man7/spi_palloc.7.gz
/usr/share/postgresql/8.1/man/man7/spi_pfree.7.gz
/usr/share/postgresql/8.1/man/man7/spi_pop.7.gz
/usr/share/postgresql/8.1/man/man7/spi_prepare.7.gz
/usr/share/postgresql/8.1/man/man7/spi_push.7.gz
/usr/share/postgresql/8.1/man/man7/spi_repalloc.7.gz
/usr/share/postgresql/8.1/man/man7/spi_saveplan.7.gz
/usr/share/postgresql/8.1/man/man7/start_transaction.7.gz
/usr/share/postgresql/8.1/man/man7/truncate.7.gz
/usr/share/postgresql/8.1/man/man7/unlisten.7.gz
/usr/share/postgresql/8.1/man/man7/update.7.gz
/usr/share/postgresql/8.1/man/man7/vacuum.7.gz
/usr/share/postgresql/8.1/man/man7/abort.7.gz
/usr/share/postgresql/8.1/man/man7/alter_aggregate.7.gz
/usr/share/postgresql/8.1/man/man7/alter_operator.7.gz
/usr/share/postgresql/8.1/man/man7/alter_user.7.gz
/usr/share/postgresql/8.1/man/man7/commit_prepared.7.gz
/usr/share/postgresql/8.1/man/man7/create_language.7.gz
/usr/share/postgresql/8.1/man/man7/drop_aggregate.7.gz
/usr/share/postgresql/8.1/man/man7/drop_operator.7.gz
/usr/share/postgresql/8.1/man/man7/drop_view.7.gz
/usr/share/postgresql/8.1/man/man7/move.7.gz
/usr/share/postgresql/8.1/man/man7/set_session_authorization.7.gz
/usr/share/postgresql/8.1/man/man7/spi_freeplan.7.gz
/usr/share/postgresql/8.1/man/man7/spi_gettypeid.7.gz
/usr/share/postgresql/8.1/man/man7/spi_returntuple.7.gz
/usr/share/postgresql/8.1/conversion_create.sql
/usr/share/postgresql/8.1/psqlrc.sample
/usr/share/postgresql/8.1/contrib
/usr/share/postgresql/8.1/contrib/ip4r.sql
/usr/share/postgresql/8.1/information_schema.sql
/usr/share/postgresql/8.1/system_views.sql
/usr/share/postgresql/8.1/pg_hba.conf.sample
/usr/share/postgresql/8.1/pg_ident.conf.sample
/usr/share/postgresql/8.1/pg_service.conf.sample
/usr/share/postgresql/8.1/postgresql.conf.sample
/usr/share/postgresql/8.1/recovery.conf.sample
/usr/share/postgresql/8.1/postgres.bki
/usr/share/postgresql/8.1/postgres.description
/usr/share/postgresql/8.1/sql_features.txt
/usr/share/postgresql-common
/usr/share/postgresql-common/maintscripts-functions
/usr/share/postgresql-common/supported-versions
/usr/share/postgresql-common/init.d-functions
/usr/share/postgresql-common/PgCommon.pm
/usr/share/postgresql-common/pg_wrapper
/usr/share/postgresql-common/run-upgrade-scripts
/usr/share/postgresql-common/upgrade-scripts
/usr/share/postgresql-common/upgrade-scripts/SPECIFICATION
/usr/share/postgresql-common/t
/usr/share/postgresql-common/t/002_existing_clusters.t
/usr/share/postgresql-common/t/001_packages.t
/usr/share/postgresql-common/t/020_create_sql_remove.t
/usr/share/postgresql-common/t/005_PgCommon.t
/usr/share/postgresql-common/t/120_pg_upgradecluster_scripts.t
/usr/share/postgresql-common/t/010_defaultport_cluster.t
/usr/share/postgresql-common/t/030_errors.t
/usr/share/postgresql-common/t/040_upgrade.t
/usr/share/postgresql-common/t/041_upgrade_custompaths.t
/usr/share/postgresql-common/t/050_encodings.t
/usr/share/postgresql-common/t/060_obsolete_confparams.t
/usr/share/postgresql-common/t/070_non_postgres_clusters.t
/usr/share/postgresql-common/t/080_start.conf.t
/usr/share/postgresql-common/t/090_multicluster.t
/usr/share/postgresql-common/t/100_upgrade_scripts.t
/usr/share/postgresql-common/t/110_integrate_cluster.t
/usr/share/postgresql-common/t/template
/usr/share/postgresql-common/t/TestLib.pm
/usr/share/postgresql-common/pg_checksystem
/usr/share/postgresql-common/testsuite
/usr/lib/postgresql
/usr/lib/postgresql/8.2
/usr/lib/postgresql/8.2/bin
/usr/lib/postgresql/8.2/bin/pg_controldata
/usr/lib/postgresql/8.2/bin/clusterdb
/usr/lib/postgresql/8.2/bin/pg_dumpall
/usr/lib/postgresql/8.2/bin/pg_dump
/usr/lib/postgresql/8.2/bin/createdb
/usr/lib/postgresql/8.2/bin/createlang
/usr/lib/postgresql/8.2/bin/createuser
/usr/lib/postgresql/8.2/bin/dropdb
/usr/lib/postgresql/8.2/bin/droplang
/usr/lib/postgresql/8.2/bin/dropuser
/usr/lib/postgresql/8.2/bin/reindexdb
/usr/lib/postgresql/8.2/bin/pg_restore
/usr/lib/postgresql/8.2/bin/psql
/usr/lib/postgresql/8.2/bin/vacuumdb
/usr/lib/postgresql/8.2/bin/initdb
/usr/lib/postgresql/8.2/bin/ipcclean
/usr/lib/postgresql/8.2/bin/pg_resetxlog
/usr/lib/postgresql/8.2/bin/pg_ctl
/usr/lib/postgresql/8.2/bin/postgres
/usr/lib/postgresql/8.2/bin/postmaster
/usr/lib/postgresql/8.2/bin/oid2name
/usr/lib/postgresql/8.2/bin/pgbench
/usr/lib/postgresql/8.2/bin/vacuumlo
/usr/lib/postgresql/8.2/lib
/usr/lib/postgresql/8.2/lib/latin2_and_win1250.so
/usr/lib/postgresql/8.2/lib/ascii_and_mic.so
/usr/lib/postgresql/8.2/lib/cyrillic_and_mic.so
/usr/lib/postgresql/8.2/lib/euc_cn_and_mic.so
/usr/lib/postgresql/8.2/lib/euc_jp_and_sjis.so
/usr/lib/postgresql/8.2/lib/euc_kr_and_mic.so
/usr/lib/postgresql/8.2/lib/euc_tw_and_big5.so
/usr/lib/postgresql/8.2/lib/utf8_and_cyrillic.so
/usr/lib/postgresql/8.2/lib/latin_and_mic.so
/usr/lib/postgresql/8.2/lib/utf8_and_ascii.so
/usr/lib/postgresql/8.2/lib/utf8_and_big5.so
/usr/lib/postgresql/8.2/lib/utf8_and_iso8859_1.so
/usr/lib/postgresql/8.2/lib/utf8_and_euc_cn.so
/usr/lib/postgresql/8.2/lib/utf8_and_euc_jp.so
/usr/lib/postgresql/8.2/lib/utf8_and_euc_kr.so
/usr/lib/postgresql/8.2/lib/utf8_and_euc_tw.so
/usr/lib/postgresql/8.2/lib/utf8_and_gb18030.so
/usr/lib/postgresql/8.2/lib/utf8_and_gbk.so
/usr/lib/postgresql/8.2/lib/utf8_and_iso8859.so
/usr/lib/postgresql/8.2/lib/utf8_and_johab.so
/usr/lib/postgresql/8.2/lib/utf8_and_sjis.so
/usr/lib/postgresql/8.2/lib/utf8_and_uhc.so
/usr/lib/postgresql/8.2/lib/utf8_and_win.so
/usr/lib/postgresql/8.2/lib/plpgsql.so
/usr/lib/postgresql/8.2/lib/plpython.so
/usr/lib/postgresql/8.2/lib/_int.so
/usr/lib/postgresql/8.2/lib/autoinc.so
/usr/lib/postgresql/8.2/lib/btree_gist.so
/usr/lib/postgresql/8.2/lib/chkpass.so
/usr/lib/postgresql/8.2/lib/cube.so
/usr/lib/postgresql/8.2/lib/dblink.so
/usr/lib/postgresql/8.2/lib/earthdistance.so
/usr/lib/postgresql/8.2/lib/fuzzystrmatch.so
/usr/lib/postgresql/8.2/lib/insert_username.so
/usr/lib/postgresql/8.2/lib/int_aggregate.so
/usr/lib/postgresql/8.2/lib/lo.so
/usr/lib/postgresql/8.2/lib/ltree.so
/usr/lib/postgresql/8.2/lib/moddatetime.so
/usr/lib/postgresql/8.2/lib/pg_trgm.so
/usr/lib/postgresql/8.2/lib/pgcrypto.so
/usr/lib/postgresql/8.2/lib/pgstattuple.so
/usr/lib/postgresql/8.2/lib/refint.so
/usr/lib/postgresql/8.2/lib/seg.so
/usr/lib/postgresql/8.2/lib/tablefunc.so
/usr/lib/postgresql/8.2/lib/timetravel.so
/usr/lib/postgresql/8.2/lib/tsearch2.so
/usr/lib/postgresql/8.2/lib/pgxml.so
/usr/lib/postgresql/8.2/lib/pg_buffercache.so
/usr/lib/postgresql/8.2/lib/adminpack.so
/usr/lib/postgresql/8.2/lib/sslinfo.so
/usr/lib/postgresql/8.2/lib/isn.so
/usr/lib/postgresql/8.2/lib/hstore.so
/usr/lib/postgresql/8.2/lib/pgrowlocks.so
/usr/lib/postgresql/8.2/lib/pg_freespacemap.so
/usr/lib/postgresql/8.1
/usr/lib/postgresql/8.1/bin
/usr/lib/postgresql/8.1/bin/pg_controldata
/usr/lib/postgresql/8.1/bin/clusterdb
/usr/lib/postgresql/8.1/bin/pg_dumpall
/usr/lib/postgresql/8.1/bin/pg_dump
/usr/lib/postgresql/8.1/bin/createdb
/usr/lib/postgresql/8.1/bin/createlang
/usr/lib/postgresql/8.1/bin/createuser
/usr/lib/postgresql/8.1/bin/dropdb
/usr/lib/postgresql/8.1/bin/droplang
/usr/lib/postgresql/8.1/bin/dropuser
/usr/lib/postgresql/8.1/bin/reindexdb
/usr/lib/postgresql/8.1/bin/pg_restore
/usr/lib/postgresql/8.1/bin/psql
/usr/lib/postgresql/8.1/bin/vacuumdb
/usr/lib/postgresql/8.1/bin/vacuumlo
/usr/lib/postgresql/8.1/bin/initdb
/usr/lib/postgresql/8.1/bin/ipcclean
/usr/lib/postgresql/8.1/bin/pg_resetxlog
/usr/lib/postgresql/8.1/bin/pg_ctl
/usr/lib/postgresql/8.1/bin/postgres
/usr/lib/postgresql/8.1/bin/postmaster
/usr/lib/postgresql/8.1/lib
/usr/lib/postgresql/8.1/lib/latin2_and_win1250.so
/usr/lib/postgresql/8.1/lib/ascii_and_mic.so
/usr/lib/postgresql/8.1/lib/cyrillic_and_mic.so
/usr/lib/postgresql/8.1/lib/euc_cn_and_mic.so
/usr/lib/postgresql/8.1/lib/euc_jp_and_sjis.so
/usr/lib/postgresql/8.1/lib/euc_kr_and_mic.so
/usr/lib/postgresql/8.1/lib/euc_tw_and_big5.so
/usr/lib/postgresql/8.1/lib/utf8_and_cyrillic.so
/usr/lib/postgresql/8.1/lib/latin_and_mic.so
/usr/lib/postgresql/8.1/lib/utf8_and_ascii.so
/usr/lib/postgresql/8.1/lib/utf8_and_big5.so
/usr/lib/postgresql/8.1/lib/utf8_and_iso8859_1.so
/usr/lib/postgresql/8.1/lib/utf8_and_euc_cn.so
/usr/lib/postgresql/8.1/lib/utf8_and_euc_jp.so
/usr/lib/postgresql/8.1/lib/utf8_and_euc_kr.so
/usr/lib/postgresql/8.1/lib/utf8_and_euc_tw.so
/usr/lib/postgresql/8.1/lib/utf8_and_gb18030.so
/usr/lib/postgresql/8.1/lib/utf8_and_gbk.so
/usr/lib/postgresql/8.1/lib/utf8_and_iso8859.so
/usr/lib/postgresql/8.1/lib/utf8_and_johab.so
/usr/lib/postgresql/8.1/lib/utf8_and_sjis.so
/usr/lib/postgresql/8.1/lib/utf8_and_uhc.so
/usr/lib/postgresql/8.1/lib/utf8_and_win1250.so
/usr/lib/postgresql/8.1/lib/utf8_and_win1252.so
/usr/lib/postgresql/8.1/lib/utf8_and_win1256.so
/usr/lib/postgresql/8.1/lib/utf8_and_win1258.so
/usr/lib/postgresql/8.1/lib/utf8_and_win874.so
/usr/lib/postgresql/8.1/lib/plpgsql.so
/usr/lib/postgresql/8.1/lib/ip4r.so
```
```
zerobinary@zerobinary:~$ sudo dpkg -r --force-all postgresql-8.2
(Reading database ... 174774 files and directories currently installed.)
Removing postgresql-8.2 ...
 * Stopping PostgreSQL 8.2 database server                               [ OK ]
```
i find i didn't remove the whole thing that's y is failing now it should be ok
```
zerobinary@zerobinary:~$ sudo apt-get install convmv
Reading package lists... Done
Building dependency tree       
Reading state information... Done
convmv is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  glom: Depends: postgresql-8.2 but it is not going to be installed
  postgresql-contrib-8.2: Depends: postgresql-8.2 but it is not going to be installed
  postgresql-plpython-8.2: Depends: postgresql-8.2 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
zerobinary@zerobinary:~$ sudo dpkg -r --force-all glom
(Reading database ... 172858 files and directories currently installed.)
Removing glom ...
zerobinary@zerobinary:~$ sudo apt-get install convmv
Reading package lists... Done
Building dependency tree       
Reading state information... Done
convmv is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  postgresql-contrib-8.2: Depends: postgresql-8.2 but it is not going to be installed
  postgresql-plpython-8.2: Depends: postgresql-8.2 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
zerobinary@zerobinary:~$ sudo dpkg -r --force-all postgresql-contrib-8.2
(Reading database ... 172771 files and directories currently installed.)
Removing postgresql-contrib-8.2 ...
zerobinary@zerobinary:~$ sudo dpkg -r --force-all postgresql-plpython-8.2
(Reading database ... 172639 files and directories currently installed.)
Removing postgresql-plpython-8.2 ...
zerobinary@zerobinary:~$ sudo apt-get install convmv
Reading package lists... Done
Building dependency tree       
Reading state information... Done
convmv is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic postgresql-client-8.2
  linux-headers-2.6.20-15
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up postgresql-8.1 (8.1.8-1ubuntu3) ...
 * Starting PostgreSQL 8.1 database server                                       * The PostgreSQL server failed to start. Please check the log output:
2007-06-06 22:08:14 PDT LOG:  could not load root certificate file "root.crt": No SSL error reported
2007-06-06 22:08:14 PDT DETAIL:  Will not verify client certificates.
2007-06-06 22:08:14 PDT LOG:  could not translate host name "localhost", service "5433" to address: Name or service not known
2007-06-06 22:08:14 PDT WARNING:  could not create listen socket for "localhost"
2007-06-06 22:08:14 PDT FATAL:  could not create any TCP/IP sockets
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.1, action "start" failed.
dpkg: error processing postgresql-8.1 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 postgresql-8.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
zerobinary@zerobinary:~$ 

```
[new and looks like fixed]zerobinary@zerobinary:~$ sudo dpkg -r --force-all postgresql-8.1
(Reading database ... 172632 files and directories currently installed.)
Removing postgresql-8.1 ...
 * Stopping PostgreSQL 8.1 database server                               [ OK ] 
zerobinary@zerobinary:~$ sudo apt-get install compiz
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
compiz set to manual installed.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic postgresql-client-8.2
  linux-headers-2.6.20-15 postgresql-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
zerobinary@zerobinary:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic postgresql-client-8.2
  linux-headers-2.6.20-15 postgresql-common
The following packages will be REMOVED:
  linux-headers-2.6.20-15 linux-headers-2.6.20-15-generic
  postgresql-client-8.2 postgresql-common
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 70.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 171914 files and directories currently installed.)
Removing linux-headers-2.6.20-15-generic ...
Removing linux-headers-2.6.20-15 ...
Removing postgresql-client-8.2 ...
Removing postgresql-common ...
zerobinary@zerobinary:~$ 
[/new and looks like fixed]

---

### Post by flawedprefect on 2007-10-01
I get a strange warning when I try to "completely remove" postgresql 8.2:

> E: postgresql-8.2: Package is in a very bad inconsistent state - you should


does anyone know how that sentence ends?

---

### Post by ichi_730 on 2007-10-18
Hi. Im a college student here in Athens Academy Open Source College and I have a problem about postgresql.. 
1. My prof assign this task to our group (for finals) none of us dont know how to perform this task.. what was the procedure on how to install this one?? 
2. how to encode a data here.. thanks we are all newbies here I hope someone might help us.. thanks..

---


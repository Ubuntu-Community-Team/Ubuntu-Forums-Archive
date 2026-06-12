---
title: "man-db doesn't work"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by unregistr3d on 2007-04-24
Hallo,
i tried to read some manuals on Feisty with "man PACKAGE" but it doesn't work "command not found"......
so, how can i enable the man database. man-db is installed.

plz help
Mfg, unregistr3d

---

### Post by tomcheng76 on 2007-04-24
```
/usr/bin/man Package
```
sucess:confused:

---

### Post by unregistr3d on 2007-04-24
```
unregistr3d@ubuntu-laptop1 /usr/bin % /usr/bin/man truecrypt
zsh: correct '/usr/bin/man' to '/usr/bin/xman' [nyae]? n
zsh: no such file or directory: /usr/bin/man
127 unregistr3d@ubuntu-laptop1 /usr/bin % which man             
man not found
1 unregistr3d@ubuntu-laptop1 /usr/bin % sudo apt-get upgrade
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Reading state information... Fertig
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
1 nicht vollständig installiert oder entfernt.
Es müssen 0B Archive geholt werden.
Nach dem Auspacken werden 0B Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren [J/n]? j
Richte man-db ein (2.4.3-5ubuntu1) ...
dpkg: Fehler beim Bearbeiten von man-db (--configure):
 Unterprozess post-installation script gab den Fehlerwert 1 zurück
Fehler traten auf beim Bearbeiten von:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
<= i have Z-Shell as default

OK, i think there is an other Error
thx


EDIT:
I tried to compile the source, and...
```
checking for working memcmp... yes
checking return type of signal handlers... void
checking for working strcoll... yes
checking for unistd.h... (cached) yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking for vprintf... yes
checking for _doprnt... no
checking for ANSI C sprintf... yes
checking for working pclose... yes
checking for strsignal... yes
checking db4/db_185.h usability... no
checking db4/db_185.h presence... no
checking for db4/db_185.h... no
checking db_185.h usability... no
checking db_185.h presence... no
checking for db_185.h... no
checking db3/db_185.h usability... no
checking db3/db_185.h presence... no
checking for db3/db_185.h... no
checking for db_185.h... (cached) no
checking for db_185.h... (cached) no
checking db2/db_185.h usability... no
checking db2/db_185.h presence... no
checking for db2/db_185.h... no
checking db2_185.h usability... no
checking db2_185.h presence... no
checking for db2_185.h... no
checking db/db.h usability... no
checking db/db.h presence... no
checking for db/db.h... no
checking db.h usability... no
checking db.h presence... no
checking for db.h... no
checking db1/db.h usability... no
checking db1/db.h presence... no
checking for db1/db.h... no
checking gdbm.h usability... no
checking gdbm.h presence... no
checking for gdbm.h... no
checking ndbm.h usability... no
checking ndbm.h presence... no
checking for ndbm.h... no
configure: error: Fatal: no supported database library/header found
```
i think this isn't an beginner talk anymore...
wfg

---


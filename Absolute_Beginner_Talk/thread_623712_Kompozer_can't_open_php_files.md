---
title: "Kompozer can't open php files"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by cemelmaci on 2007-11-26
hi,

Kompozer can't open php files.
I always got a "open with" dialog, if I try to open php files.

[IMG]http://img144.imageshack.us/img144/110/bildschirmfotoes7.png[/IMG]
any ideas?

---

### Post by jfinkels on 2007-11-26
Are you trying to access PHP pages on a server that you set up yourself? If so, you may not have libapache2_mod_php[4|5] installed... I have found that if the web server fails to execute the scripts, your web browser will prompt you to open the file.

---

### Post by dasunst3r on 2007-11-26
Kompozer is the buggiest piece of **** I've ever used as an HTML editor.  I would suggest giving Amaya a shot -- it's in the repositories. 

More information about Amaya: [http://www.w3.org/Amaya/](http://www.w3.org/Amaya/)

---

### Post by cemelmaci on 2007-11-26
no i trying local files to open.

> sc@sc-laptop:~$ sudo apt-get install libapache2-mod-php5
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Reading state information... Fertig
libapache2-mod-php5 ist schon die neueste Version.
libapache2-mod-php5 set to manual installed.
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.


	
Quanta php open the files but without the table view function.
[IMG]http://img152.imageshack.us/img152/3465/bildschirmfotoen6.png[/IMG]
I need Kompozer for table display function in Php files.
Such a function is available in NVU so I thought kompozer would also have this function.

---


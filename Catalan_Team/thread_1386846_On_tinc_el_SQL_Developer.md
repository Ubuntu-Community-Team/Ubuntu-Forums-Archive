---
title: "On tinc el SQL Developer??"
date: 2010-01-21
forum: Catalan Team
---

### Post by pserra on 2010-01-21
Hola,
ahir vaig instal·lar el Oracle 10g des de Synaptic (molt pràctic) i ara per treballar-hi  he instal·lat el Sql Developer (baixant-lo des de la pagina oficial e instal·lar-ho amb el instal·lador de pàquets).El cas es que des de el terminal l'executo:
pere@pere-portatil:~$ sqldeveloper

Oracle SQL Developer
 Copyright (c) 1997, 2009, Oracle and/or its affiliates.All rights reserved. 

Type the full pathname of a J2SE installation (or Ctrl-C to quit), the path will be stored in ~/.sqldeveloper/jdk

i que no em trobi el java ja es normal... he de modificar el arxiu sqldeveloper.conf i afegir-hi el java home.... però aquesta vegada desconec on esta instal·lat el sqldeveloper...si vaig a cerca fitxers (escric sqldeveloper) i selecciono el sistema de fitxers... em troba residus de una instal·lació-desinstal·lació que vaig fer fa mesos i   que es va instal·lar al meu home... ara no hi és...
**Hi ha alguna sentència per conèixer la ubicació dels programes instal·lats?? **fa estona que li dono voltes al tema i no me'n surto...
el instal·lador de paquets a quin directori instal·la?
Merci

---

### Post by papapep on 2010-01-21
> Hi ha alguna sentència per conèixer la ubicació dels programes instal·lats?? fa estona que li dono voltes al tema i no me'n surto

No sé per on "has fet voltes", però la ordre [find]("http://www.google.es/search?q=linux+find+command&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:ca:unofficial&client=firefox-a") és la teva primera opció, complicada, però potent.
També pots fer servir la [locate]("http://packages.ubuntu.com/karmic/locate"), més simple, però efectiva.

---

### Post by pserra on 2010-01-21
Merci papapep,
se m'ha creat a un directori per mi desconegut:** home/pere/.**
i a més, totes les carpetes porten abans una "o.".exemple: o.sqldeveloper

em sembla que alguna cosa ha fallat...a l'instalació
que aconselles... reinstal·lar-ho??
Merci per tot,
per cert, el find no l'ha trobat però el locate si, perfecte.

deixo sortida terminal:


pere@pere-portatil:~$ find sqldeveloper
find: «sqldeveloper»: No such file or directory
pere@pere-portatil:~$ sudo find sqldeveloper
[sudo] password for pere: 
find: «sqldeveloper»: No such file or directory
pere@pere-portatil:~$ locate sqldeveloper
/home/pere/.sqldeveloper
/home/pere/sqldeveloper-2.1.0.62.61-1.noarch
/home/pere/.nautilus/metafiles/file:%2F%2F%2Fhome%2Fpere%2Fsqldeveloper-2.1.0.62.61-1.noarch%2Fopt%2Fsqldeveloper%2Fsqldeveloper%2Fbin.xml
/home/pere/.nautilus/metafiles/file:%2F%2F%2Fhome%2Fpere%2Fsqldeveloper-2.1.0.62.61-1.noarch%2Fopt%2Fsqldeveloper.xml
/home/pere/.sqldeveloper/MigrationErrorLog.xml
/home/pere/.sqldeveloper/system2.1.0.62.61
/home/pere/.sqldeveloper/tmp
/home/pere/.sqldeveloper/system2.1.0.62.61/.issplash
/home/pere/.sqldeveloper/system2.1.0.62.61/o.datamodeler.2.0.0.574
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.audit.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.ceditor.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.db.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.db.explorer.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.diffmerge.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.externaltools.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.files.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.gallery.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.help.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.importexport.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.indexing.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.log.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.navigator.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.peek.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.persistence.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.quickdiff.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.replace.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.runner.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.vfs.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.vhv.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.webbrowser.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.webupdate.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ideimpl.indexing-migrator.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.javacore.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.jdeveloper.db.connection.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.jdeveloper.db.debug.probe.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.jdeveloper.history.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.jdeveloper.runner.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.jdeveloper.subversion.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.jdeveloper.vcs.11.1.1.2.36.54.96
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.11.1.1.62.61
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.datamodeler_reports.11.1.1.62.61
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.extras.1.1.1.62.61
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.filenavigator.11.1.1.62.61
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.migration.11.1.1.62.61
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.migration.db2.11.1.1.62.61
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.migration.msaccess.11.1.1.62.61
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.migration.mysql.11.1.1.62.61
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.migration.sqlserver.11.1.1.62.61
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.migration.sybase.11.1.1.62.61
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.migration.teradata.11.1.1.62.61
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.migration.translation.core.11.1.1.62.61
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.migration.translation.core_antlr3.11.1.1.62.61
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.migration.translation.db2.11.1.1.62.61
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.migration.translation.gui.11.1.1.62.61
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.oviewer.11.1.1.62.61
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.report.11.1.1.62.61
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.searchbar.11.1.1.62.61
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.snippet.11.1.1.62.61
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.sqlmonitor.11.1.1.62.61
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.thirdparty.browsers.11.1.1.62.61
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.timesten.2.0.0.62.61
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.tuning.11.1.1.62.61
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.unit_test.11.1.1.62.61
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.worksheet.11.1.1.62.61
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.xmlschema.11.1.1.62.61
/home/pere/.sqldeveloper/system2.1.0.62.61/oracle.javatools.cache
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.11.1.1.2.36.54.96/Debugging.layout
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.11.1.1.2.36.54.96/Editing.layout
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.11.1.1.2.36.54.96/dtcache.xml
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.11.1.1.2.36.54.96/projects
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.11.1.1.2.36.54.96/settings.xml
/home/pere/.sqldeveloper/system2.1.0.62.61/o.ide.11.1.1.2.36.54.96/windowinglayout.xml
/home/pere/.sqldeveloper/system2.1.0.62.61/o.jdeveloper.subversion.11.1.1.2.36.54.96/preferences.xml
/home/pere/.sqldeveloper/system2.1.0.62.61/o.jdeveloper.subversion.11.1.1.2.36.54.96/vcs.log
/home/pere/.sqldeveloper/system2.1.0.62.61/o.jdeveloper.vcs.11.1.1.2.36.54.96/preferences.xml
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.11.1.1.62.61/DefaultWorkspace
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.11.1.1.62.61/System.sys
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.11.1.1.62.61/breakpoints.xml
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.11.1.1.62.61/ide.properties
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.11.1.1.62.61/preferences.xml
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.11.1.1.62.61/product-preferences.xml
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.11.1.1.62.61/DefaultWorkspace/DefaultWorkspace.jws
/home/pere/.sqldeveloper/system2.1.0.62.61/o.sqldeveloper.11.1.1.62.61/DefaultWorkspace/Project1.jpr
/home/pere/.sqldeveloper/system2.1.0.62.61/oracle.javatools.cache/00000000
/home/pere/.sqldeveloper/system2.1.0.62.61/oracle.javatools.cache/00000000/00000000.jdb
/home/pere/.sqldeveloper/system2.1.0.62.61/oracle.javatools.cache/00000000/je.lck
/usr/bin/make-sqldeveloper-package
/usr/share/doc/sqldeveloper-package
/usr/share/doc/sqldeveloper-package/README
/usr/share/doc/sqldeveloper-package/changelog.gz
/usr/share/doc/sqldeveloper-package/copyright
/usr/share/man/man1/make-sqldeveloper-package.1.gz
/var/lib/dpkg/info/sqldeveloper-package.list
/var/lib/dpkg/info/sqldeveloper-package.md5sums
pere@pere-portatil:~$ ^C
pere@pere-portatil:~$

---

### Post by papapep on 2010-01-21
> em sembla que alguna cosa ha fallat...a l'instalació

No veig res que indueixi a pensar que és així. Dins /home/usuari és del més habitual tenir directoris d'usuari ocults (comencen per .) per a les aplicacions.

> per cert, el find no l'ha trobat però el locate si, perfecte.

És que "find nomdelfitxer" no és la ordre correcta. Així només busca al directori al qual ets en aquell moment :)
Si fas un "man find" veuràs tota la munió d'opcions, modificadors i paràmetres diversos, no parlem de les [expressions regulars]("http://ca.wikipedia.org/wiki/Expressi%C3%B3_regular"), que pot tenir.

Si fas un "find /home/pere -name sqldeveloper" veuràs com sí que troba coses :)

Per la resta, desconec aquest programa, amb el qual no et seré de gaire ajut.

Ah, per cert, per altres cops, quan hagis d'enganxar un text llarg, fes-ho amb un adjunt o posant la url que et surti en enganxar-lo a [http://ubuntu.pastebin.com/](http://ubuntu.pastebin.com/). Sinó queden uns posts i uns fils immenjables ;)

---

### Post by pserra on 2010-01-21
Merci pels consells papapep,
problema solventat i entés.

---


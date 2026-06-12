---
title: "maelys: internet cafe software"
date: 2010-05-24
forum: Cameroon Team
---

### Post by lug.limbe on 2010-05-24
il serait bien d'avoir un soft "open source" pour cafe internet. nous avons teste maelys sur ubuntu 10.04 et voici le resultat

l'installation est sans probleme 

nous avons installe les fichiers .deb avec gdebi, pour n'avoir pas de probeme de dependances.

mais nous ne pouvons pas lancer le serveur maelys

[I]root@ubu1004d:/home/michel/phpmi/Maelys# /usr/local/maelys/server/bin/master start
waiting for Maelys Server to start... ..............failed
master: Maelys Server does not start
root@ubu1004d:/home/michel/phpmi/Maelys# 
[/I]
le server ne peut pas etre lance (petite remarque il n'existe pas de ficher /etc/init.d/maelys*server )

par la commande
/usr/local/maelys/server/bin/master start

il y a une erreur, voila le log

[I]michel@ubu1004d:~/phpmi/Maelys$ sudo tail -f /usr/local/maelys/server/var/server.log
2010/05/24 - 09:32:25 -- Master -- Starting... 41086
2010/05/24 - 09:32:25 -- Master -- Starting service process Monitor...
2010/05/24 - 09:32:25 -- Master -- service process Monitor started, listening on port <34703>
2010/05/24 - 09:32:25 -- Master -- Starting service process Storage...
2010/05/24 - 09:32:25 -- Monitor -- En attente sur la socket
09:32:25 -- Monitor -- JSON arg {custom:{},netio:{master-port:41086},paths:{config-file:"/usr/local/maelys/server/etc/server.conf",plugin-dir:"/usr/local/maelys/server/plugins/monitor"}}

/usr/local/maelys/server/libexec//maelys-storage: error while loading shared libraries: libmysqlclient.so.15: cannot open shared object file: No such file or directory
2010/05/24 - 09:32:31 -- Master -- Exiting: Failed to start service process Storage


[/I]effectivement ce fichier n'existe pas, pendant l'instalation, j'ai vu qu'il faut installer libmysqlclient, j'ai charge le fichier suivant

[I]michel@ubu1004d:~/phpmi/Maelys$ apt-get -s install libmysqlclient16
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**libmysqlclient16 is already the newest version.**
libmysqlclient16 set to manually installed.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic-pae
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 24 not upgraded.
michel@ubu1004d:~/phpmi/Maelys$ 

[/I]question de version?
:confused:
nous voulons vraiment un soft pour internet cafe, un cyber de buea serait interesse a un installe un system x2go mais il lui faut un soft pour gerer le cyber. on pourrait ravaiiler ensemble


limbe

---

### Post by dhad on 2010-05-24
Essaie ceci en root:
apt-get install build-essential libmysqlclient-dev
j´ai installé maelys, normalement ca devrai marcher,  bonne chance.

---


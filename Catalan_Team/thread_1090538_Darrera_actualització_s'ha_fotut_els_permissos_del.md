---
title: "Darrera actualització s'ha fotut els permissos del /lib"
date: 2009-03-08
forum: Catalan Team
---

### Post by elbuit on 2009-03-08
Doncs que ahir abans d'anar-me'n vaig actualitzar els darrers pegats per a Hardy, en tenia 19 pendents, supose per que ja feia temps que no actualitzava.
Sols actualitze hardy-security i hardy-updates, res de proposed o backports en aquesta màquina.
Doncs bé, ahir vaig apagar l'ordinador i fa una estona el pose en marxa i tataxan...
No m'inicia el GDM.
Intente accedir des d'un shell i em diu que "/bin/bash: Permission denied".
Me caguen en la sota de bastos, no podia ni tan sols entrar en mode text.
Així que al reiniciar i entrar en mode de recuperació com a root he suposat que seria cosa d'algun permís que tindria root i no els demes usuaris.
una vegada descartats els directoris / /bin i l'arxiu /bin/bash que estaven tots amb els permisos adequats m'he adonat que hi havia un directori /lib que no tenia els permisos bé, ja que sols tenia permís per a llistar-lo el root
#ls -ld /lib
drwxr-xr-- 17 root root 12288 2009-01-29 21:36 /lib/
amb un simple chmod 755 /lib s'ha solventat, però ja m'ha costat trobar-ho...
SI vos passa ja sabeu.

---


---
title: "El Centre de Programari no s'instal·la"
date: 2009-11-14
forum: Catalan Team
---

### Post by oryctes on 2009-11-14
Acabo d'actualitzar el sistema a Karmic. Tot sembla funcionar correctament, excepte el nou "Centre de programari", que no s'obre.

He provat de desintalar-lo amb Synaptic i quan l'he tornat a instal·lar m'apareix el següent error:

[FONT="Courier New"]ERROR:root:error processing: /usr/share/app-install/desktop/gnomad2.desktop unknown locale: ca_AD
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/update.py", line 102, in update
    name = parser.get.desktop("Name")
  File "/usr/share/softeare-center/softwarecenter/db/update.py", line 61, in get_desktop
    locale = fetdefaultlocale(('LANGUAGE','LANG','LC_TYPE','LC_ALL'))[0]
  File "/usr/lib/python6.2/locale.py", line 478, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python6.2/locale.py", line 410 in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
ValueError: unknown locale: ca_AD
ERROR:root:error processing: /usr/share/app-install/desktop/gnome-specimen.desktop unknown locale: ca_AD
....[/FONT]

(i va apareixent el mateix error unes quantes vegades)

Alguna pista de a què pot ser degut???

Gràcies per endevant

---

### Post by papapep on 2009-11-15
> ERROR:root:error processing: /usr/share/app-install/desktop/gnomad2.desktop unknown locale: ca_AD

Fixa't que et repeteix uns quants cops això de l'"unknown locale: ca_AD".

Prova a anar a Preferències > Administració > Suport d'idioma, i canvia l'idioma a ca_ES (Català; Valencià (Espanya)). Crec recordar que ja és un històric que el ca_AD porta problemes. 
Un cop ho hagis fet, actualitza tots els paquets, per verificar que tens tots els paquets d'idioma i altres instal·lats. A un terminal:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

i torna a provar a executar el Centre de programari.

Benvingut al fòrum, Oryctes.

---

### Post by MorlanXaos on 2009-12-01
Doncs tenia el mateix problema, he seguit tots els passos, i ara si que s'obre, però totes les diferents departaments del programari estan buits. He canviat les fonts del programari de la ftp del caliu a el servidor d'Ubuntu Espanya, i despres de actualitzar el cache, continua estan buit. Francament no se gairebé que fer

(també he provat la opció de deixar escollir el millor servidor, però també sense resultat)

---

### Post by papapep on 2009-12-01
I al Synaptic et passa el mateix? o només al Centre de Programari??

---

### Post by MorlanXaos on 2009-12-01
El synaptic funciona correctament, es sols el centre de programari

---

### Post by MorlanXaos on 2009-12-24
Avui després d'actualitzar el sistema, voila!! el programari ja torna a estar al centre de programari. Deuria ser algun bug que afecta la meva instal.lacio. :confused:

---


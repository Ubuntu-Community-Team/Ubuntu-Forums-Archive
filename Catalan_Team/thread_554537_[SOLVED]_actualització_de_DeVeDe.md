---
title: "[SOLVED] actualització de DeVeDe"
date: 2007-09-19
forum: Catalan Team
---

### Post by Brunilda on 2007-09-19
El programa DeVeDe ha deixat de funcionar. Tot anava bé fins que vaig acceptar actualitzar a la versió 3.1b. Un cop actualitzat cridava el programa i no s'obria, ho vaig fer des del terminal i es pot llegir el següent*

Psyco not installed, the program will just run slower
DeVeDe 3.2
Traceback (most recent call last):
  File "/usr/bin/devede", line 130, in <module>
    gettext.install("devede",localedir=share_locale) # None is sys default locale
  File "/usr/lib/python2.5/gettext.py", line 508, in install
    t = translation(domain, localedir, fallback=True, codeset=codeset)
  File "/usr/lib/python2.5/gettext.py", line 493, in translation
    t = _translations.setdefault(key, class_(open(mofile, 'rb')))
  File "/usr/lib/python2.5/gettext.py", line 180, in __init__
    self._parse(fp)
  File "/usr/lib/python2.5/gettext.py", line 314, in _parse
    plural = v[1].split('plural=')[1]
IndexError: list index out of range

La veritat és que no el sé interpretar i us demano novament ajuda.

*Aquest missatge és de la versió 3.2 però és el mateix que apareixia amb la versió 3.1b

---

### Post by CarlesOriol on 2007-09-19
Aquesta actualització no està en repositoris. Explica quina versió de l'ubuntu tens i com l'has fet.

---

### Post by Brunilda on 2007-09-19
Jo treballo amb la Feisty i la versió 3.1b del DeVeDe es va descarregar des del gestor d'actualitzacions i la 3.2 la vaig descarregar amb el synaptic.

---

### Post by papapep on 2007-09-19
Però feisty no té la versió 3.2 al repositori, sinó la 2.9:

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=devede&searchon=names&subword=1&version=feisty&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=devede&searchon=names&subword=1&version=feisty&release=all)

Ja que sembla ser que cap de la versió 3 no et funciona, provaria a tornar a posar la que et funcionava (que devia ser la 2.9, no?)

---

### Post by Brunilda on 2007-09-19
Perdoneu, però alguna cosa se m'escapa.  Així és com instal·lo la versió 3.2:
jordi@brunilda:~$ sudo aptitude install devede
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències       
Reading state information... Fet           
S'està llegint la informació d'estat estesa      
S'estan inicialitzant els estats dels paquets... Fet
S'està generant la base de dades de marcadors... Fet
Els paquets següents s'han apartat:
  nspluginwrapper 
Els paquets nous següents s'instal·laran:
  devede 
0 paquets actualitzats, 1 instal·lats, 0 a suprimir i 1 a no actualitzar.
Es necessita obtenir 0B/1148kB d'arxius. Després del desempaquetat s'utilitzaran 2552kB.
S'està escrivint la informació d'estat estesa... Fet
S'està seleccionant el paquet devede prèviament no seleccionat.
(S'està llegint la base de dades ... hi ha 136376 fitxers i directoris instal·lats actualment.)
S'està desempaquetant devede (de .../devede_3.2-0ubuntu1~upure64_all.deb) ...
S'està configurant devede (3.2-0ubuntu1~upure64) ...

Com ho puc fer per instal·lar una altra versió?

---

### Post by pespin on 2007-09-19
Deus tindre algun repositori no oficial o alguna cosa per l'estil. Pots enganxar aquí el contingut del arxiu '/etc/apt/sources.list' ?

---

### Post by Brunilda on 2007-09-19
jordi@brunilda:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://janvitus.interfree.it/ubuntu/](http://janvitus.interfree.it/ubuntu/) feisty-upure64 main-amd64
deb-src [http://janvitus.interfree.it/ubuntu/](http://janvitus.interfree.it/ubuntu/) feisty-upure64 main-amd64
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

#AUTOMATIX REPOS START
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse #Added by software-properties
#AUTOMATIX REPOS END

---

### Post by pespin on 2007-09-19
Efectivament tens tot el set de repositoris del automatix2 jeje. Segurament serà aquest el problema. Els anteriors a l'automatix exactament no se que són i pot ser que siguin el causant del problema.

1- Desinstal·la el devede (sudo aptitude purge devede)
2- comenta els repositoris del automatix
3- Actualitza la llista de repositoris (sudo aptitude update)
4- Instal·la el devede (sudo aptitude install devede)

---

### Post by Brunilda on 2007-09-19
Gràcies Pespin, he solucionat els dos problemes que tenia d'una tacada.

---

### Post by CarlesOriol on 2007-09-20
No... no tenies dos problemes. En tenies sols un i es diu automatix.

---

### Post by Brunilda on 2007-09-20
Hola Carles, ja t'he llegit alguna altra vegada i he comprès que ets el creador del club de fans de l'Automatix. Per fer-me el carnet ja l'he desinstal·lat completament, perquè la veritat és que en el temps que m'ha acompanyat tampoc no m'ha aportat res (bé algun problemilla).

Novament, gràcies a tots.

---


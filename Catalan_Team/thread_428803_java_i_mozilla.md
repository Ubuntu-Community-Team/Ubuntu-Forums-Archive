---
title: "java i mozilla"
date: 2007-04-30
forum: Catalan Team
---

### Post by perevidal on 2007-04-30
hola a tots i totes

no soc capaç de instalar el java al 7.04 (amd 64 bits)

algú sp fer-ho ..i el mes important m'ho pot explicar???


gràcies

---

### Post by papapep on 2007-05-01
Al menú Aplicacions > Afegeix/Elimina, un cop dins, a la dreta a dalt, hauries de canviar la selecció a"Totes les aplicacions disponibles". Un cop fet això, si cerques java ja t'haurien de sortir els paquets necessaris per a seleccionar i instal·lar.

Salutacions.

---

### Post by utep on 2007-06-18
He intentat fer el que tu deies papapep i en ppi tot be però fins que la instalació ha petat i m'ha sortit un error dient que no s'havia pogut instalar...
Ara quen vaic a Afegeix/Elimina programes em surt l'error:

> [B]No s'ha pogut fer la verificació de les
aplicacions instal·lades i disponibles[/B]
This is a major failure of your software management system.
Please check for broken packages with synneptic, check the file
permissions and correctness of the file '/etc/apt/sources.list'
anr reaload the software information with: 'sudo apt -get update'
and 'sudo apt -get install -f'

Aiximateix, alhora d'instalar actualitzacions tb m'apareix l'error:

> **L'index de programari està trencat**
No és posible instal·lar o desinstal·lar programari. Per arreglar -
ho, utilitzeu el gestor de paquets "Synaptic" o executeu "sudo apt -get install -f" en un terminal

Pel que fa l'arxiu sources.list, l'he editat i donat que son novato en el tema no veic res extrany. Aqui el teniu per si algú hi veu quelcom extrany:

> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

Pel que fa al les linies de comando 'sudo apt -get update' i 'sudo apt -get install -f', m'apareix en ambdós comandos:
> sudo: apt: command not found

Té solució?
Merci,
utep

---

### Post by papapep on 2007-06-18
...o jo estic molt dormit a aquesta hora, o no ho entenc.

Utep, què té a veure el teu comentari amb el fil del*** java i mozilla***??? T'has equivocat de fil? O realment navego més que el Titanic??

---

### Post by utep on 2007-06-19
home jo diria que si que te relació :D:D:D:D:D:D:D:D

Defet el problema original es que volia obrir alguna pagina amb el mozilla i em demanava els plugins de java; llavors he buscat per aqui al foro com s'instalaven i he seguit les teves instruccins  però malauradament, a diferencia de perevidal jo no he tingut un final feliç i al intentar instalar el java  m'ha sortit un error i se m'ha tancat l'aplicació i ara quan intento accedir a afegir/eliminar programes em surt això...

---

### Post by papapep on 2007-06-19
Doncs el teu problema el tens amb l'instal·lador, no amb el java i mozilla. Aleshores, això pertoca a un altre fil ;)

Apart, la solució te la dóna el mateix error:

> This is a major failure of your software management system.
Please check for broken packages with synneptic, check the file
permissions and correctness of the file '/etc/apt/sources.list'
anr reaload the software information with: 'sudo apt -get update'
and 'sudo apt -get install -f'

Traduït: Això és un greu error del vostre sistema de gestió de programari. Si us plau comproveu els fitxers trencats amb synneptic (Synaptic), comproveu els permisos de fitxers i que el fitxer "/etc/apt/sources.list" estigui bé, i torneu a carregar la informació amb: "**sudo apt-get update**" i "**sudo apt-get install -f**"

Les dues comandes en negreta, són les que hauries d'executar en un terminal a veure si t'arreglen el problema.

---

### Post by utep on 2007-06-19
En l'explicació de l'error que he fet, he probat la solució proposada amb el mateix error però no ha resultat... pots veure una mica més amunt el resultat de l'arxiu sources i de les dues linies de comando que comentes...
:(

---

### Post by papapep on 2007-06-19
Si molt no m'equivoco, deixes un espai entre el guió i get, el qual fa que l'intèrpret d'ordres no sàpiga què li demanes. La comanda exacte és:

```
apt-get update
``` (sense espai entre apt guió i get).

Tot i això, si vols assegurar la jugada, fes:

```
aptitude update
```

Després pots executar el:

```
apt-get install -f
```

(un altre cop sense espai entre apt guió i get)

---

### Post by Pijus on 2007-06-19
Holes,
jo també sóc novell amb el linux i també tenia problemes amb el navegador i el java...

Després de veure les instruccions l'he instal.lat sense cap mena de problema, ara em funciona el navegador correctament.

Gracies de nou!

Pijus

---

### Post by AlexMuntada on 2007-06-19
> **perevidal said:**
> no soc capaç de instalar el java al 7.04 (amd 64 bits)

Si no us en sortiu amb les indicacions d'en papapep, hauríeu de donar-nos més detalls sobre el problema: el que heu executat, el missatge d'error que us ha sortit, etc.

---

### Post by utep on 2007-06-20
> **papapep said:**
> Si molt no m'equivoco, deixes un espai entre el guió i get, el qual fa que l'intèrpret d'ordres no sàpiga què li demanes. La comanda exacte és:

```
apt-get update
``` (sense espai entre apt guió i get).

Tot i això, si vols assegurar la jugada, fes:

```
aptitude update
```

Després pots executar el:

```
apt-get install -f
```

(un altre cop sense espai entre apt guió i get)


Tot i els problemes que has vist que tinc papapep en l'altre post... he pogut iniciar la versió 15 de ubuntu (no se si podre reiniciar sense problemes pero de moment aguanta...) i he probat el que em comentaves...
Efectivament ho posava malament com em comentes...

TEMA SOLUCIONAT!!
(un menys...:D:D:D:D)

Gracies,
utep

---


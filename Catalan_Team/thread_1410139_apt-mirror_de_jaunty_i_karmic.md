---
title: "apt-mirror de jaunty i karmic"
date: 2010-02-18
forum: Catalan Team
---

### Post by mguerr35 on 2010-02-18
Hola,

algú de vosaltres ha fet servir apt-mirror per a 2 versions d'Ubuntu?

A l'institut tenim un repositori local de jaunty funcionant, llavors he modificat l'arxiu mirror.list per a que també s'afegissin els repositoris de karmic però no va.

Navegant per les carpetes he vist que a apt-mirror/mirror/archive.ubuntu.com hi ha dos subdirectoris: 
- dist: Amb jaunty, jaunty-security, jaunty-updates
- pool: Amb main, universe, multiverse, restricted

Llavors dedueixo que a pool (on és tot el programari) no hi ha per distingir si és de jaunty o karmic i per això continua només funcionant per a jaunty. 
Sabeu la forma correcta de poder afegir karmic a la mateixa màquina?

---

### Post by SiscoGarcia on 2010-02-19
Hola mguerr35, nosaltres tenim un mirall funcionant amb 2 versions sense cap problema. El que hem fet és editar el fitxer /etc/apt/mirror.list que teníem funcionant amb la versió vella, l'hem copiat i on deia jaunty ho hem canviat per karmic. Després l'hem afegit al final del mateix fitxer i ja ens ha funcionat. Llavors executant
```
sudo apt-mirror
```
ja comença a descarregar els paquets.

Sort ;)

---

### Post by mguerr35 on 2010-02-19
Hola,

vaig fer el mateix que Sisco (copiar les línies de la 9.04, enganxar-les al final i canviar jaunty per karmic).

De totes formes crec que acabo de trobar l'error. Tenim el següent cron que executa l'apt-mirror cada dia a les 4 del matí:

```
#
# Regular cron jobs for the apt-mirror package
#
#0 4    * * *    apt-mirror    /usr/bin/apt-mirror > /var/spool/apt-mirror/var/cron.log
```Però el **#** de la darrera línia?? Aquest repositori no s'ha actualitzat des del primer dia que va instal·lar-se #-o

Descomentaré la línia per a que vagi fent durant el cap de setmana i dilluns us explico com ha anat!!

Gràcies Sisco!

Mario

---

### Post by mguerr35 on 2010-02-26
Hola,

una setmana més tard ja s'ha descarregat el repositori. Però no funciona gaire bé, he desinstal·lat openoffice.org-base per fer la prova i ara no permet tornar-lo a instal·lar, apareix aquest error:
```
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
No s'han pogut instal·lar alguns paquets. Això pot ser degut a que vàreu
requerir una situació imposible o a que esteu emprant la distribució
unstable i alguns paquets requerits encara no han estat creats o bé
encara no els hi han afegit.
La informació següent pot ajudar-vos a resoldre la situació:

Els següents paquets tenen dependències sense satisfer:
  openoffice.org-base: Depén: openoffice.org-core (= 1:3.0.1-9ubuntu3) però no serà instal·lat
                       Depén: openoffice.org-base-core (= 1:3.0.1-9ubuntu3) però no serà instal·lat
E: Paquets trencats
```D'altra banda he instal·lat tree sense cap problema. 
Mirant l'arbre de directoris (i recordant el primer post), hi ha un estructura que dubto si és correcta i si pot plantejar conflictes entre paquets de jaunty i karmic, ja que _són tots dins del directori pool_.

Us adjunto l'arbre:

```
/repositori/apt-mirror/
|-- mirror
|   |-- archive.ubuntu.com
|   |   `-- ubuntu
|   |       |-- dists
|   |       |   |-- jaunty
|   |       |   |   |-- main
|   |       |   |   |-- multiverse
|   |       |   |   |-- restricted
|   |       |   |   `-- universe
|   |       |   |-- jaunty-security
|   |       |   |   |-- main
|   |       |   |   |-- multiverse
|   |       |   |   |-- restricted
|   |       |   |   `-- universe
|   |       |   |-- jaunty-updates
|   |       |   |   |-- main
|   |       |   |   |-- multiverse
|   |       |   |   |-- restricted
|   |       |   |   `-- universe
|   |       |   |-- karmic
|   |       |   |   |-- main
|   |       |   |   |-- multiverse
|   |       |   |   |-- restricted
|   |       |   |   `-- universe
|   |       |   |-- karmic-security
|   |       |   |   |-- main
|   |       |   |   |-- multiverse
|   |       |   |   |-- restricted
|   |       |   |   `-- universee
|   |       |   `-- karmic-updates
|   |       |       |-- main
|   |       |       |-- multiverse
|   |       |       |-- restricted
|   |       |       `-- universe
|   |       `-- pool
|   |           |-- main
|   |           |   |-- a
|   |           |   |(...b,c,d,e,f..x,y,)
|   |           |   `-- z
|   |           |-- multiverse
|   |           |   |-- a
|   |           |   |(...b,c,d,e,f..x,y,)
|   |           |   `-- z
|   |           |-- restricted
|   |           |   |(a...z)
|   |           `-- universe
|   |               |(a,b,c...)
|   |               |-- y
|   |               `-- z
(...)
`-- var
```Sisco, podries comprovar si la vostra estructura de directoris també és així? Gràcies!
A mi em fa extrany que, per exemple, si vull instal·lar brasero_2.26.1-0ubuntu1_i386.deb, només hi ha un paquet .deb, llavors o és el mateix per a karmic i jaunty o a la carpeta /pool/main/b/brasero una versió sobreescriu a l'altra...

Gràcies,

Mario

---

### Post by SiscoGarcia on 2010-02-26
> **mguerr35 said:**
> Sisco, podries comprovar si la vostra estructura de directoris també és així?

D'acord Mario, dilluns miro d'esbrinar com ho tenim i us ho explico.

---

### Post by mguerr35 on 2010-03-02
Ja funciona!!!

Després de descarregar 64Gb a velocitat d'institut de secundària, vaig actualitzar altres màquines i va funcionar a la primera (tant amb jaunty com a karmic). 

A la prova que havia fet amb l'openoffice.org-base vaig desinstal·lar tot l'open office i tornar-lo a instal·lar i també va funcionar correctament, probablement tenia algun conflicte a llibreries i/o dependencies.

De totes formes, que estiguin tots els paquets d'ambdues versions dins de /pool no ho acabo de veure clar (i funciona!), continuaré buscant per veure com ho gestiona...


Mario

---


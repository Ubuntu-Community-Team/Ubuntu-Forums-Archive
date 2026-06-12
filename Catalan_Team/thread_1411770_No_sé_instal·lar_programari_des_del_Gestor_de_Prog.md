---
title: "No sé instal·lar programari des del Gestor de Programari"
date: 2010-02-20
forum: Catalan Team
---

### Post by mrc2407 on 2010-02-20
Bé, doncs això... Sóc nou en això d'Ubuntu i Linux en general, només m'he estat un matí provant el Linkat i bé, no m'havia donat gaires problemes.

He instal·lat Ubuntu 9.10, he creat un usuari des de l'instal·lador ("principal") i m'he connectat amb aquest usuari. Llavors he creat un segon usuari, "prova", des de Sistema -> Administració -> Usuaris i Grups amb permisos "Desktop user" + permís de fer servir xarxes inalàmbriques i ethernet.

Per comprovar que "prova" no podia instal·lar res, he anat a Aplicacions -> Centre de programari i he intantat instal·lar alguna cosa. No he pogut, però no m'ha demanat cap contrasenya. Ho he provat amb "principal" i tampoc he pogut. En ambdós casos, quan entro a veure una fitxa d'un programa qualsevol, em diu que "No està disponible en les dades actuals". Per posar un exemple de programa, Obteniu programari lliure -> Ciència -> Stellarium.

Si amb l'usuari "principal" entro al Gestor de Paquets de Synaptic puc instal·lar/desinstal·lar paquets. Si hi entro des del "prova" amb la contrasenya de "principal", no em deixa (diu contrasenya incorrecta). És extrany, oi? En canvi, si amb "prova" entro amb la seva contrasenya em diu que no tinc permisos. Això ho faig notar perquè amb Linkat ppuc instal·lar coses d'es d'un usuari si tinc la contrasenya del root, i sembla que amb Ubuntu no.

Doncs això, que no puc instal·lar res per aquí, i no em demana la contrasenya tampoc.

Relacionat amb això, aquest usuari "principal" que he creat amb l'instal·lador és el mateix que el "root"? Perquè al gestor d'usuaris i grups m'apareixen els tres ("principal", "root" i "prova")

Com veieu sóc molt novato amb això... Aviam si em podeu ajudar!

Gràcies!

---

### Post by papapep on 2010-02-20
Si com a usuari "principal" fas a un terminal:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

actualitza correctament la base de paquets i el sistema?

---

### Post by ifanlo on 2010-02-21
Hola!

> **mrc2407 said:**
> Relacionat amb això, aquest usuari "principal" que he creat amb l'instal·lador és el mateix que el "root"? Perquè al gestor d'usuaris i grups m'apareixen els tres ("principal", "root" i "prova")


No; son tres usuaris diferents.  El motiu pel qual l'usuari [FONT="Courier New"]principal[/FONT] pot insta-lar programes és perquè el sistema afegeix automàticament l'usuari al grup [FONT="Courier New"]admin[/FONT].

I el grup [FONT="Courier New"]admin[/FONT] té privilegis per executar comandes amb privilegis de [FONT="Courier New"]root[/FONT], mitjançant [FONT="Courier New"]sudo[/FONT] o [FONT="Courier New"]gksudo[/FONT], com podràs veure a l'arxiu de configuració [FONT="Courier New"]/etc/sudoers[/FONT].

En consequència, una solució senzilla perquè [FONT="Courier New"]prova[/FONT] pugui instal·lar programes, passaria per afegir aquest usuari al grup [FONT="Courier New"]admin[/FONT].

---

### Post by mrc2407 on 2010-02-21
> **papapep said:**
> Si com a usuari "principal" fas a un terminal:

```
sudo aptitude update && sudo aptitude safe-upgrade
```actualitza correctament la base de paquets i el sistema?

Sí, amb l'usuari "principal" puc actualitzar bé els paquets... Bé, em dóna problemes de connexió en alguns, però l'ordre s'executa bé.

> **ifanlo said:**
> Hola!

No; son tres usuaris diferents.  El motiu pel qual l'usuari [FONT=Courier New]principal[/FONT] pot insta-lar programes és perquè el  sistema afegeix automàticament l'usuari al grup [FONT=Courier  New]admin[/FONT].

I el grup [FONT=Courier New]admin[/FONT] té privilegis per  executar comandes amb privilegis de [FONT=Courier New]root[/FONT],  mitjançant [FONT=Courier New]sudo[/FONT] o [FONT=Courier  New]gksudo[/FONT], com podràs veure a l'arxiu de configuració [FONT=Courier New]/etc/sudoers[/FONT].

En consequència, una solució senzilla perquè [FONT=Courier New]prova[/FONT]  pugui instal·lar programes, passaria per afegir aquest usuari al grup [FONT=Courier New]admin[/FONT].

Però el problema és que "principal" no pot instal·lar programes! Des del Centre de programari puc eliminar programes ja instal·lats, però no els puc instal·lar. Tampoc puc llegir el fitxer que em dius amb el Gedit, perquè em diu que no tinc permisos necessaris.

Puc donar més permisos a "rincipal", però llavors no entenc la funció de l'usuari root... No seria tot molt més fàcil si, d'alguna manera, es pogués iniciar sessió com a root?

Gràcies!

---

### Post by SiscoGarcia on 2010-02-21
> **mrc2407 said:**
> No seria tot molt més fàcil si, d'alguna manera, es pogués iniciar sessió com a root?

Seria diferent. Probablement seria més fàcil, no ho sé; però segur que seria més perillós perquè fàcilment podries instal·lar/desinstal·lar paquets no desijats.

---

### Post by papapep on 2010-02-21
> Puc donar més permisos a "rincipal", però llavors no entenc la funció de l'usuari root... 

Això és per que no tens present que els [sistemes *nix]("http://ca.wikipedia.org/wiki/Unix"), dels quals deriva, ni que sigui filosòficament [Gnu/Linux]("http://ca.wikipedia.org/wiki/GNU/Linux"), eren sistemes amb molts usuaris amb pocs privilegis treballant des de terminals tontos i que hi havia la figura de l'administrador que era el que controlaba tots els recursos del/s servidors, amb el seu compte de "root". :)


> No seria tot molt més fàcil si, d'alguna manera, es pogués iniciar sessió com a root?

Bé, fàcil segur, i suïcida també :D. Seria pervertir completament la base de la seguretat dels sistemes *nix. Si vols fer tasques d'administració, només et cal executar les ordres amb "sudo" a un terminal, o executar-les amb "gksudo" a l'entorn gràfic. Així limites les conseqüències d'una possible intrusió al sistema, codi maliciós o, fins i tot, d'una errada pròpia teva al mínim possible.

Amb el teu usuari "principal", si no has tocat res dels permisos que té assignats de manera predeterminada en crear-lo al instal·lar el sistema, has de poder fer tot el que et calgui sense problemes. Només et cal saber com i on ;)

Respecte l'altre usuari "prova", doncs depèn dels permisos que li hagis atorgat. Si vas a Sistema > Administració > Usuaris i grups, fas un clic damunt l'usuari "prova", fas clic damunt "Propietats" i després a la pestanya "Privilegis d'usuari", veuràs què pot fer i què no.

En tot cas, amb un sol usuari (en el teu cas "principal") a banda de "root" per a administrar el sistema, a no ser que sigueu diverses persones al mateix ordinador, en tens de sobres.

T'aconsellaria una llegida sobre les bases de la seguretat i funcionament dels sistemes Gnu/Linux. Un bon principi, pot ser aquest: [https://wiki.ubuntu.com/CatalanTeam/Recursos/Int%C3%A8rpretComandes](https://wiki.ubuntu.com/CatalanTeam/Recursos/Int%C3%A8rpretComandes)

---

### Post by mrc2407 on 2010-02-21
Moltes gràcies a tots per les respostes i suggeriments, però continuo tenint el problema base: l'usuari "principal", creat des de l'instal·lador, no pot instal·lar programes amb el Centre de Programari perquè em diu que "No està disponible en les dades actuals". No he canviat els permisos d'aquest usuari en cap moment, i pertany al grup d'usuaris "admin".

---

### Post by papapep on 2010-02-21
Doncs prova a reconfigurar-lo:

```
sudo dpkg-reconfigure software-center
```

Si es segueix resistint, crea un usuari nou, li atorgues els permisos que vulguis allà on t'he dit abans i ja hauria d'estar.
Si segueixes tenint problemes amb el nou usuari, és que alguna cosa "s'ha fet malbé" a nivell de permisos en la instal·lació del SO o posterior manipulació.

---

### Post by mrc2407 on 2010-02-21
He creat un altre usuari amb permisos d'administrador i tampoc puc. Estic reinstal·lant l'Ubuntu, aviam si ara... De fet, ara que m'hi fixo em surt una pantalla tipo consola que diu:

Mount of filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.

L'ubuntu aquest el vaig baixar d'aquí: [http://www.ubuntu.cat/node/341](http://www.ubuntu.cat/node/341) Pot ser que el problema sigui d'aquesta ISO i que amb l'Ubuntu de la web oficial funcioni bé?

Gràcies un altre cop.

---

### Post by mrc2407 on 2010-02-21
Bé, sembla ser que al final ho he aconseguit: a Sistea -> Administració -> Fonts de programari, he canviat el srvidor des d'on baixar programari a 

[http://ftp.caliu.cat/pub/distribucions/ubuntu/archive](http://ftp.caliu.cat/pub/distribucions/ubuntu/archive)

A més, a la pestanya Altre programari he activat la opció "http://archive.canonical.comm/ubtuntu karmic partner" i ara ja puc instal·lar correctament :) 

Gràcies a tots per la vostra ajuda i paciència :)

---


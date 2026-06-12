---
title: "Connexió defectuosa internet arrencant  d'inici"
date: 2012-01-02
forum: Catalan Team
---

### Post by prostata on 2012-01-02
Vaig fer una instal·lació neta de la 10.10, però encara que tot va bé el problema és que cada vegada que arrenco la màquina no es produeix la connexió automàtica a internet i haig de donar-li a la icona de connexió d'internet, o en cas contrari no es connecta automàticament. En la icona de connexió de xarxa apareix el subtitulo la connexió de xarxa cablejada "auto eth0" està activa, però no connectada, de manera que haig de clicar perquè es produeixi la connexió. No és greu, però si enutjós a més mai havia succeït alguna cosa així en totes les instal·lacions que porto fetes. He mirat a connexió de xarxa > Ipv4 > dispositiu de xarxa > i on diu "intercicie de bucle local (lo), el canvio per interficie ethernet(eth0)> edito la connexió i vaig a configurar i clico sobre les opcions > cablejada > aseguran-me que tant connectar automàticament com disponible per a tots els usuaris estiguin activades, però no obstant cada cop que arrenco la màquina haig de fer novament tot el proces...¿alguna suggerència..??

---

### Post by wgarcia on 2012-01-03
Què tens al fitxer /etc/network/interfaces?

Des d'una terminal fes:

```
cat /etc/network/interfaces
```

i enganxa aquí els resultats.

---

### Post by prostata on 2012-01-03
> **wgarcia said:**
> Què tens al fitxer /etc/network/interfaces?

Des d'una terminal fes:

```
cat /etc/network/interfaces
```

i enganxa aquí els resultats.

Doncs el que tinc és:

```
auto lo
iface lo inet loopback

```

---

### Post by wgarcia on 2012-01-04
Es pot provar el següent: obre una terminal, i edita aquest fitxer /etc/network/interfaces amb

```
gksudo gedit /etc/network/interfaces
```

agrega una línia que posi

```
auto eth0
```

Si no funciona torna a fer el mateix i esborra aquesta línia.

---

### Post by prostata on 2012-01-04
Ho he fet, però el resultat continua sent el mateix....¿altre idea...???

---

### Post by kimet on 2012-01-04
Em sembla que network manager sobreescriu aquest arxiu, així, si el tens NM actiu no serveix de res configurar la xarxa manualment.

Post provar a treure network manager dels programes al inici i afegir a /etc/network/intefaces:
```
allow-hotplug eth0
iface eth0 inet dhcp
```

O pots provar a instal.lar wicd a veure si et va millor.

Salut.

---

### Post by prostata on 2012-01-04
gràcies kimet, he instal·lat el wicd, he tret network manager de programes d'inici, he re-iniciat la màquina, i a la primera el wicd m'ha connectat a internet. no coneixia aquest soft, a veure com es comporta aquests propers dies.....com a conseqüencia del teu consell he llegit per google i sembla ser el soft ideal.

Hi ha prou de fer el que he fet o he de treure tot el relacionat amb network manager????, vull dir anar a synaptic i fer la des-instal-lació.

---

### Post by kimet on 2012-01-04
Em sembla que al instal.lar wicd es desinstal.la automatomaticament NM i a la inversa, pero si no fos així en no arrancarse al inici n'hi ha prou. 

Salut.

---

### Post by prostata on 2012-01-05
Bé, un breu resum: vaig des-instalar network manager, fins aquest moment només vaig amb wicd, però...però, encara triga una mica de fer la connexió, de fet haig de refrescar-la dins el gui de wicd perque es connecti a la xarxa, o sigui més o menys que igual amb el network-manager. També ho vaig fer treien-lo  del inici però amb el mateixos resultats. De fet m'agradaria saber el perquè d'aquesta situació, més que res perquè voldria saber la causa pel que amb altres instal·lacions netes que he fet al llarg dels anys aquest problema mai havia sorgit... també vaig fer les proves que em recomanaves editant l'arxiu que em deies i afegint-hi les dues línies de més, però el resultat sempre ha estat igual, continuaré investigant...per cert i per si serveix de res, treballo am router cisco de ONO 30 mb.

Salut

---

### Post by wgarcia on 2012-01-05
Dues coses més tontes que es poden provar són:

1) Crear un nou usuari i provar si des del nou usuari es connecta automàticament

2) Provar des d'un Live CD o USB a veure si es connecta automàticament

---

### Post by prostata on 2012-01-06
Des de el Live CD sí es va connectar, quan vaig fer instal·lació de forma automàtica, ¿?, però avui al mati ja es connecta amb wicd de forma automàtica, triga uns 15" però ho fa, pot ser algun paràmetre deins el gui de configuració perquè ho faci immediatament?=?? però de moment encara que siguin uns segundets ja ho fa....gracies a tots per la vostra col·laboració. Esperaré uns dies per confirmar el resultat i desprès marcaré el post coma Solved...

Salut

---


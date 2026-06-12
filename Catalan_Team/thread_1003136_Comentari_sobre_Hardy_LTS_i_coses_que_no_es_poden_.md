---
title: "Comentari sobre Hardy LTS i coses que no es poden actualitzar"
date: 2008-12-05
forum: Catalan Team
---

### Post by lpargemi on 2008-12-05
Hola

Ara mateix faig servir la distribució Hardy, i volia quedar-m'hi un temps pel fet que és LTS. No m'agrada canviar les coses només pel fet de canviar, i menys les coses que em funcionen; però trobo que en un mes i poc des que la versió següent s'ha alliberat ja hi ha coses que se m'han quedat desfasades. Les mostres:

Sembla que no podré instal.lar el Openoffice 3.0, > [http://ubuntuforums.org/showthread.php?t=987077]("http://ubuntuforums.org/showthread.php?t=987077"). A la feina, on no em puc desempallegar del W$, el tinc instal.lat sobre W2K; i es pot i va. Ja ho sé, és contradictori no voler canviar d'operatiu i si de openoffice, però és que no és ben bé el mateix. 

Farà una setmana i mitja el sistema es va actualitzar canviant al kernel 2.6-24-22. Ara ja no puc fer anar el virtualbox, perquè el paquet *virtualbox-ose module for linux-image-2.6.24-22-generic* encara no està disponible al Synaptic. Ja sé que apagant la màquina i arrencant amb el kernel 21 anirà... [Em dedico com a amateur a fer un parell de pàgines web, i em va bé provar-les amb altres navegadors, com MSIE o chrome]

Ja entenc que mantenir tot aquest conjunt enorme de programari al dia amb coherència és una feina descomunal, però m'esperava que una versió LTS no es quedaria obsoleta tan aviat.

I una reflexió: cal realment estar sempre al canvi permanent? Si cada sis mesos he d'estar actualitzant-ho tot, em queda molt menys temps disponible per fer servir l'ordinador; que és pel què el vull.

No sé si aquest és el lloc per fer aquests comentaris, però em penso que si.

Salut

Lluís

---

### Post by jaume69 on 2008-12-06
> Ja entenc que mantenir tot aquest conjunt enorme de programari al dia amb coherència és una feina descomunal, però m'esperava que una versió LTS no es quedaria obsoleta tan aviat.

I una reflexió: cal realment estar sempre al canvi permanent? Si cada sis mesos he d'estar actualitzant-ho tot, em queda molt menys temps disponible per fer servir l'ordinador; que és pel què el vull.

Jo també em pensava que amb la **8.04** m´hi estaría molt temps,però con que no tenia molts programes instal.lats o imprecindibles vaig decidir actualitzar a **8.10**(va anar +o- bé.),i al final instal.lar de nou desde 0,que crec és el millor.

Des de el meu punt de vista d´usuari bàsic vaig trobar més millores a la 8.10 a nivell d´entorn d´escriptori,Gnome,Nautilus,Compiz.

Pot ser si el que vols és treballar amb **[COLOR="Orange"]Ubuntu[/COLOR]** és millor la **LTS**.
O tenir força experiència en l´actualització de paquets i programes,i també depens dels programadors (versions-comptabilitat),per això..
):P

---

### Post by lpargemi on 2008-12-07
Hola Jaume

> **jaume69 said:**
> Jo també em pensava que amb la **8.04** m´hi estaría molt temps,però con que no tenia molts programes instal.lats o imprecindibles vaig decidir actualitzar a **8.10**(va anar +o- bé.),i al final instal.lar de nou desde 0,que crec és el millor.


Ja, però uns instal.lació des de zero vol dir setmanes de feina a restaurar tot allò que ja tenies més o menys estabilitzat. (Només hi puc dedicar una o dues hores al dia a això)

En fi, no em pensava que l'Ubuntu apliqués tan estrictament el pensament d'Heràclit d'Efes (aquell del tot flueix).

Lluís

---

### Post by PatrickVogeli on 2008-12-07
Ho tens mal entès això de LTS. LTS significa Long Term Support, i vol dir exactament que hi haurà actualitzacions de seguretat durant més temps que amb les versions normals. L'actualització d'openoffice de 2.4 a 3.0 no es una actualització de seguretat, com tampoc ho es passar de firefox 2.0 a 3.0 o del kernel .24 al 25; així doncs, mai les tindras.

El camí a seguir es o bé utilitzar el repositori hardy-backports o algun altre de no oficial, cosa que comporta els seus propis problemes. Compilar es pot amb segons que, pero hi ha vegades que resulta quasi bé impossible.

Sobre actualitzar cada 6 mesos, jo trobo que no es estrictament necessari, si ja tens tot el que necessites. El tema esta que sembla ser que hardy ara mateix no té tot el que vols, i per tant ja es una altra discussió.

salut

---

### Post by enricXIII on 2008-12-07
Totalment d'acord amb el patrick. Jo estic amb Hardy precisament per que és una LTS, i ja que ho tinc tot rutllant perfectament, necessito estabilitat per treballar, puc prescindir d'actualitzacions de programari "ultima versió"...perquè hauria d'actualitzar a Intrepid? en el meu cas es innecessari de moment, sobretot tinguent garantides les actualitzacions de seguretat importants.

---

### Post by SiscoGarcia on 2008-12-08
> **lpargemi said:**
> Sembla que no podré instal.lar el Openoffice 3.0, 

Sembla que s'està solucionant al menys aquest tema:

> **SiscoGarcia said:**
> Sembla que després d'un període de proves en què els repositoris del launchpad van deixar de funcionar, la cosa està solventada i ja és operatiu l'[enllaç al launchpad]("https://launchpad.net/~openoffice-pkgs/+archive"), no només per intrepid que és on hi ha hagut el problema, sinó que es pot fer servir el mateix enllaç per hardy. Llàstima que m'he actualitzat a intrepid ;)

He vist fa una estona al [launchpad]("https://launchpad.net/~openoffice-pkgs/+archive") que si que és possible fer aquesta actualització, encara ho he de provar per confirmar-ho.

---

### Post by lpargemi on 2008-12-08
> Ho tens mal entès això de LTS. LTS significa Long Term Support, i vol dir exactament que hi haurà actualitzacions de seguretat durant més temps que amb les versions normals. L'actualització d'openoffice de 2.4 a 3.0 no es una actualització de seguretat, com tampoc ho es passar de firefox 2.0 a 3.0 o del kernel .24 al 25; així doncs, mai les tindras.

Tens raó PatrickVogeli, segurament les meves expectatives sobre LTS no tenien massa fonament. També entenc que una cosa son les actualitzacions de seguretat i una altra els canvis de versió. (En SiscoGarcia comenta més amunt que pel openoffice 3.0 podria ser que estigués resolt). Amb tot això m'he quedat penjat, de moment, pel què fa al Virtualbox; i aquesta actualització si que era de seguretat.

Que consti que no em queixo, ja ho comentava al principi del post que ha de ser una feinada brutal tenir tot això al dia. Però segueixo pensant que potser no cal fer un canvi de versió cada sis mesos. I per descomptat que és una opinió d'un usuari, que només veig una part petita del bosc, i que en definitiva sé de sobres que tot això funciona per la bona voluntat de qui ho fa anar. I agraït.

Salut

Lluís

---

### Post by PatrickVogeli on 2008-12-08
no et serveix el paquete virtualbox-ose-source?? igual hauras de compilar el modul, no se.

---

### Post by lpargemi on 2008-12-08
> **PatrickVogeli said:**
> no et serveix el paquete virtualbox-ose-source?? igual hauras de compilar el modul, no se.

Potser si que serveixi, no ho he provat. Potser sigui el moment d'aprendre com es compila un paquet. No ho fet mai. Buscaré per aquí informació de com caldria fer-ho.

Lluís

---


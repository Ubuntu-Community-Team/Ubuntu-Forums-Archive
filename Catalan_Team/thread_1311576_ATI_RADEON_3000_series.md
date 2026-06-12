---
title: "ATI RADEON 3000 series"
date: 2009-11-02
forum: Catalan Team
---

### Post by guillemtanya7 on 2009-11-02
Hola companys,

us volia fer una pregunta. Acabo d'instal·lar la versió 9.10 de l'ubuntu. Fins ara tenia la 9.4 i cap problema. La instal·lació l'he fet de nou. El problema que tinc és que el driver de la targeta gràfica no se m'activa (l'hi dic activar i surt una barra de percentatge que es carrega molt rapid però no fa res ni diu res). Sí que se m'instal·la però no se m'activa. Llavors si provo d'instal·lar el que té la pàgina d'Ati, sense tenir instal·lat el que suggereix l'ubuntu (l'fglrx) tampoc funciona.

Crec que això és el problema principal, ja que llavors per fer l'scroll de les pàgines, ja siguin webs o per exemple de la llista de programes del Synaptic, em un efecte retardat un pèl molest.

Algú té alguna idea?

Moltes gràcies!  Salutacions!

---

### Post by guillemtanya7 on 2009-11-05
Hola a tothom!

Corretgeixo el que deia abans. El driver de la pàgina d'Ati sí que s'instal·la però no funciona bé, i continua produint el mateix efecte que abans.

El driver fglrx ja se m'instal·la i sí que em funciona bé, només que fa el tonto amb una cosa: al maximitzar les finestres té un retard, petit però suficient per notar-lo cada vegada.

Quan tenia la versió 9.04 també em passava, però actualitzant el paquet XOrg i instal·lant el driver de la pàgina d'Ati es va solucionar.

Alguna suggerència?

Gràcies!

Salutacions!

---

### Post by guillemtanya7 on 2009-11-07
Hola de nou companys!

Ja sé on falla el problema. Per si algú si troba, el fet és que hi ha una actualització de l'Xorg a través dels repositoris ppa que fa que el retard en maximitzar les pantalles no hi sigui. 
És a dir, el que cal fer és afegir els repositoris i actualitzar:

[https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill]("https://launchpad.net/%7Elaunchpad-weyland/+archive/xserver-nobackfill")

Llavors instal·lar el driver de la targeta gràfica ATI de la pàgina web i funciona a la perfecció.

Ara bé, existeix un altre problema que és si usem el kernel generic-pae. Llavors l'scroll funciona com si s'encallés.

Jo utilitzo el generic-pae per poder reconèixer les 4GB que té l'ordinador, sinó, amb el genèric sol només me'n reconeix 3.

Si algú coneix alguna manera de reconèixer les 4Gigues sense haver d'isntal·lar el generic-pae també l'hi agrairé.

MOltes mercès!

salutacions!

---


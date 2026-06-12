---
title: "[SOLVED] kDE, des del gestor de paquets"
date: 2008-12-23
forum: Catalan Team
---

### Post by markinux on 2008-12-23
Hola de nou a tohom;
Ja fa uns quants dies que experimento amb l'ubuntu i ara, m'agraderia instal·lar-me el KDE, i he llegit que tinc vàries opcions:
1- crear una màquina virtual.( amb el virtual box)
2- Puc instal·lar el KDE, fent un terminal?
3- Me'l puc descarregar des del gestor de paquets? Si és així, em podrieu especificar el nom que he de posar?
Aconselleu-me si us plau.
Gràcies i perdó per si ja s'ha parlat d'aquest tema.

SALUTACIONS

---

### Post by RafaelCarreras on 2008-12-23
Hola Markinux.

El KDE "només" és un escriptori, no un sistema operatiu, així que no cal cap màquina virtual per fer-lo anar.

El pots instal·lar des dels repositoris. El paquet kubuntu-desktop t'instal·larà tot el que cal. També et canviarà les pantalles d'arrencada i de tancament per les de Kubuntu, però si no t'agraden les pots tornar a canviar sense esborrar el KDE.
Si ho vols instal·lar-lo per consola: sudo apt-get install kubuntu-desktop.

Que vagi bé.

---

### Post by markinux on 2008-12-23
Ja l'he descarregat, ara em demana el gestor de pantalla.
Quin selecciono el gdm o el kdm?

---

### Post by RafaelCarreras on 2008-12-23
El kdm és el del KDE i el gdm el del Gnome. En realitat tant és, podràs accedir tant al KDE com al Gnome des de qualsevol dels dos. S'assemblen molt, pots elegir el que vulguis.

---

### Post by orestesmas on 2008-12-23
Ja t'han respost la majoria de les teves preguntes, però cal afegir-hi el següent:

No dius quina versió d'Ubuntu fas servir. Això és important, perquè per versions d'ubuntu iguals o anteriors a la 8.04 (Hardy) el KDE que se t'instal·larà per omissió és el KDE3, mentre que a partir de la 8.10 se t'instal·larà el KDE4.

El KDE3 és molt madur i complet (té força més aplicacions que cap altre escriptori, sense comptar, és clar, les aplicacions genèriques) però està quedant obsolet en favor del KDE4.

El projecte KDE va fer un salt de versió i de moltes altres coses el gener de 2008. Entre altres coses, s'han canviat molts aspectes de l'arquitectura subjacent, i s'han reescrit *totes* les aplicacions. Això fa que el futur sigui molt prometedor, però que a dia d'avui la versió del KDE4 que inclou la Intrepid (el KDE 4.1) sigui encara poc recomanable per un ús diari (tot i que jo i molts d'altres la usem i podem treballar perfectament). Bàsicament falta traspassar encara algunes aplicacions, i algunes peten de tant en tant.

El KDE 4.2 ja és tota una altra cosa, i és una versió que ja està al nivell de qualsevol altre escriptori, amb algunes coses millors i altres pitjors. El problema és que la Kubuntu no la incorporarà fins a la 9.04 (la del proper abril). Mentrestant si la vols usar has de recórrer a paquets "beta" extraoficials, o bé a usar la versió "alfa" de la Kubuntu 9.04. Ambdues opcions són vàlides, però jo no les recomanaria a ningú que comenci ara amb GNU/Linux.

Per tant què hi farem!, mentre no es publiqui la Jaunty, t'hauràs "d'aguantar" i seguir amb el GNOME.

<mode flame="on">
Dic "aguantar" perquè és clar que, una vegada s'ha tastat el nèctar i l'ambrosía, és molt dur tornar a la crua realitat...
</mode>

---

### Post by jaume69 on 2008-12-23
Jo no ho recomanaria instal.lar dos escriptoris tan pesats en una mateixa partició,si vols estabilitat.
Per provar no passa res..
Per experiència en temps recents anteriors.Pot ser ara ha canviat molt la cosa i tot rutlla a les mil meravelles,però no crec.
Tot i que ara els H.D.,en general,aguanten més,em sembla.
**Salut**.

---

### Post by orestesmas on 2008-12-23
Ja em perdonaràs, Jaume, però jo no li veig la base científica per enlloc al teu post... :-(

Què té a veure l'estabilitat amb el número de coses instal·lades? Pots tenir instal·lades totes les aplicacions que vulguis, fins i tot les més inestables del món, que si no les executes el teu sistema serà perfectament estable. I en el cas dels escriptoris, doncs només en fas servir un a la vegada de manera que, si un d'ells com a mínim funciona bé, no notaràs cap inestabilitat mentre el facis servir.

I, a més, si un programa és inestable ja el pots posar en una altra partició, que ho seguirà essent. Però aquí em sembla que ja sé per on vas: vols dir que tu instal·laries, per exemple, ubuntu en una partició i kubuntu en una altra, i usaries el grub per escollir-ne una o altra en arrencar. D'acord, és una opció (que no té cap relació amb l'estabilitat, sinó més aviat amb mantenir limitat el nombre de paquets instal·lats en una distribució), però això és instal·lar diverses distribucions, no diversos escriptoris.

Després no veig què té a veure la capacitat "d'aguante" dels discs durs amb l'estabilitat del sistema, excepte que si el disc dur peta, se'n va tot en orris. Mentrestant, ja pots anar-lo omplint, que el sistema és igual d'estable.

Amb l'única cosa que estic d'acord és amb la frase "per provar no passa res".

Vaja, que hem de procurar ser precisos en les explicacions, o confondrem tothom.

---

### Post by xoldy on 2008-12-23
Si és per provar, jo faria una màquina virtual amb kubuntu 8.10 per exemple, i allà faria de tot sense perill de carregar-te el sistema matriu.
De tota manera entenc que és un pal gestionar massa sistemes encara que siguin virtuals!

Una opinió més.
Espero haver-te ajudat
Jordi

---

### Post by CarlesOriol on 2008-12-23
Crec com l'Orestes que no es correcte això que dieu.

El fet d'insta&#320;lar el kde a la mateixa partició no provocarà cap tipus de problema al gnome ni al contrari.

Ara bé... després de provar la beta del kde 4.2 he de dir que el nectar mesclat amb ambrosia em crea un reugst excesivament dolç i empalagós a la boca.

---

### Post by markinux on 2008-12-23
Gràcies a tothom per les vostres opinions.

---

### Post by jaume69 on 2008-12-23
Jo he escrit la **meva experiència** que he tingut al provar d´instal.lar dos escriptoris,Gnome i KDE,i en el meu cas,quan normalment instal.les el segon escriptori,al principi tot va de meravelles però si instal.les molts programes,arriba un moment que et trobes amb "alguns" conflictes de Paquets o programes que no funcionen bé degut a l´esmentat anteriorment.No és res nou,amb Windows passa el mateix..

Pot ser si tens un ordinador "Ferrari" això no et passa tant,tot  i que ho dubto,encara que no hagi tingut mai l´ocasió-experiència de haver-ho pogut provar.

El que dius que pots anar omplint fins que el Disc Dur peta,jo penso que ara aguanten més els Disc Durs nous que els de fa 2 o 3 anys i tenen la mateixa efectivitat,diria.

Lo de tenir-los en diferents Particions crec que és el millor,en qüestió de rendiment,seguretat,fiabilitat,parlem d´anar a buscar el millor per a la màquina-pc.

Lo de tenir la Home en un altre Partició no ho he provat mai i no sé si realment millora molt el rendiment.¿:-.?

Orestes,tens raó que no m´he explicat prou bé del tot.
Es fa el que es pot..
**Salut.**

_____________________

*****BONES FESTES*****
_____________________

---


---
title: "Gnome Classic no es veu bé"
date: 2012-05-01
forum: Catalan Team
---

### Post by Joan A. on 2012-05-01
Bon dia!

Avui he instal·lat Ubuntu 12.04 amb gnome-panel per recordar temps millors. Malauradament, no es veu bé. La llista de finestres es veu en blanc i la barra d'Aplicacions i Llocs en negre. Aquí en teniu un exemple d'un altre usuari: [http://dl.dropbox.com/u/36251983/zontesAmbiance-screenshot-original.jpg](http://dl.dropbox.com/u/36251983/zontesAmbiance-screenshot-original.jpg)

Afortunadament, existeix una solució que consisteix en editar el tema Ambiance, però no sé com s'aplica. Aquí està el 'bug' i la solució: [https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/981289](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/981289)

Si qualqú m'ajudés a saber com es pot aplicar el canvi li estaria eternament agraït.

Gràcies!

---

### Post by Joan A. on 2012-05-03
Solucionat el problema! Pel que he vist la pàgina de 'launchpad' és un 'bug' bastant comú. Si qualqú vol solucionar el problema, hi ha dues opcions: editar l'arxiu gnome-panel.css del tema Ambiance o esperar a una actualització. Per aplicar la primera opció heu de fer el següent:

1. Obrir l'arxiu gnome-panel.css:

> sudo gedit /usr/share/themes/Ambiance/gtk-3.0/apps/gnome-panel.css2. Després copiam tot el codi del següent document i l'aferram al document obert: [gnome-panel.css]("https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/981289/+attachment/3091134/+files/gnome-panel.css")

3. Guardam i reiniciam la màquina.

Ara ja podreu gaudir de l'entorn Gnome clàssic sense color extranys. Això sí, encara queden alguns punts per polir. Però des del meu punt de vista el més correcte seria esperar per l'actualització, encara que és un misteri quan arribarà.

---

### Post by AlbertJB on 2012-05-03
I tant que queden moltes coses per polir a Gnome Classic. Per exemple, si tens els botons de minimitzar, maximitzar i tancar a la dreta de les finestres, i tens posem per cas una finestra maximitzada, el més lògic seria dirigir el cursor a l'extrem de dalt a la dreta de la pantalla i prémer amb el botó del ratolí, però almenys en el meu cas el cursor no arriba a la icona de tancar, sinó que has d'apuntar una mica més a baix a l'esquerra per arribar a tancar la finestra. Això fa molt poc usable el sistema. 

Ho he provat amb diversos Window Themes i GTK+ Themes. Aprofito per recomanar el ClearWaita-master (per als que utilitzàvem Clearlooks a Ubuntu 10.10) i si se'm permet per fer proposar un canal de discussió a Freenode IRC per discutir problemes relacionats amb Gnome Classic, p.ex. ##gnome-classic-ca o alguna cosa així... 

Salutacions cordials

---

### Post by Joan A. on 2012-05-03
Sincerament, no entenc gaire bé el teu problema, però pots canviar la posició dels botons. A mi, per defecte em venen a l'esquerra, cosa que no em molesta per res. Aquí tens un manual de com fer-ho: [http://robersoft.blogcindario.com/2011/01/00007-poner-los-botones-de-las-ventanas-de-ubuntu-a-la-derecha.html](http://robersoft.blogcindario.com/2011/01/00007-poner-los-botones-de-las-ventanas-de-ubuntu-a-la-derecha.html)

Vagi bé!

---

### Post by AlbertJB on 2012-05-03
Moltes gràcies Joan per la resposta. 

El cas és que ja tinc els botons a la dreta, tot fent el procediment que m'enllaces (amb l'editor de configuració i posant menu:maximize, minimize, close). Però precisament perquè el close queda a la dreta de tot, em pensava que dirigint el cursor a l'extrem "nord-est" de la pantalla tancaria fàcilment les finestres, però resulta que per qüestió d'uns pocs píxels els botons de tancar de les finestres no encaixen exactament a dalt a la dreta, sinó un pèl més a baix. A l'Ubuntu 10.10 encaixava perfectament.

Però entenc que és un cas particular perquè la majoria d'ubuntaires tinc entès que prefereixen els botons a l'esquerra.

També dir que estic una mica decebut amb el Nautilus del Gnome-Classic, hi trobo a faltar dues coses molt importants per mi:

1. La funció Resize Images a Edit
2. La barra d'eines principal l'han canviada, hi havia una icona amb una fletxa amunt per pujar de directori.

A part d'això, no sé quin suport tindrà en el futur Gnome-Classic, ja que veig que, i ho entenc, estan posant tot l'esforç a millorar el Gnome-Shell i no pas el Gnome-Classic.

I perdona per "robar-te" l'entrada, és la primera vegada que participo en aquests fòrums, t'he trobat cercant gnome-classic a Google i me n'he aprofitat ;---)

Salutacions i gràcies

---

### Post by Joan A. on 2012-05-03
No sé si parlam del mateix Gnome classic. Crec que tu dius el gnome classic que ve quan instales Gnome 3. Jo estic parlant del gnome-panel que instales dels dels mateixos repositoris d'Ubuntu i mantengut per Ubuntu.

---

### Post by wgarcia on 2012-05-03
Em sembla Joan que quan instal·les el paquet "gnome-panel" s'instal·la el "gnome-shell", això de "Gnome" que et surt a la pantalla inicial és el gnome-shell.

---

### Post by AlbertJB on 2012-05-03
Exacte, s'instal·la tot plegat Joan. De fet, actualment crec que el paquet gnome-panel == gnome-classic == gnome-fallback. 

I pel que he sabut, es tracta d'un bug amb Gnome-classic (amb efectes, amb Compiz). Entrant amb Gnome-classic sense efectes (amb Metacity) el problema es resol al 90%.

Realment Gnome-classic necessita madurar, li estic trobant molts bugs :(

---

### Post by Joan A. on 2012-05-04
> **wgarcia said:**
> Em sembla Joan que quan instal·les el paquet "gnome-panel" s'instal·la el "gnome-shell", això de "Gnome" que et surt a la pantalla inicial és el gnome-shell.

Quan instal·les gnome-panel no s'instal·la Gnome Shell. Però quan instal·les Gnome 3 sí s'instal·la la sessió fallback amb efectes i sense efectes. El gnome-panel és un paquet de Ubuntu i el Gnome 3 és un paquet de Gnome. Crec, hehe.

---

### Post by Joan A. on 2012-05-04
> **Gosset Inofensiu said:**
> Exacte, s'instal·la tot plegat Joan. De fet, actualment crec que el paquet gnome-panel == gnome-classic == gnome-fallback. 

I pel que he sabut, es tracta d'un bug amb Gnome-classic (amb efectes, amb Compiz). Entrant amb Gnome-classic sense efectes (amb Metacity) el problema es resol al 90%.

Realment Gnome-classic necessita madurar, li estic trobant molts bugs :(

Jo, a part de qualque tonteria no he trobat gaires 'bugs'. Però sí tens raó en que el necessiten perfeccionar.

---

### Post by AlbertJB on 2012-07-07
Per curiositat, com us va amb el gnome classic a Ubuntu 12.04? Jo segueixo sense poder executar l'onboard (perquè tinc el locale català) i de vegades em fa coses estranyes... Però s'aguanta prou bé. A tu també Joan A.?

---

### Post by AlbertJB on 2012-07-08
Per cert, em vaig posar en contacte amb el noi que va portar el gnome panel 2.x a 3.x, per agrair-li l'esforç, preguntant-li si el el paquet seria suportat en el futur, i la seva resposta no em va agradar gaire:

I ported gnome-panel to GTK+ 3 in order to provide a fallback mode for
GNOME 3. As you've mentioned, the primary intention is really to simply
offer a working desktop when there's no hardware support for
gnome-shell.

A secondary intention is to help people slowly migrate to GNOME 3: let
them adopt everything else except the core desktop [...]

Now, in terms of maintenance: gnome-panel is not actively developed by
me. I do maintain it in the sense that I'll try to fix major bugs that
are affecting people, and I'll merge contributions that make sense. I
intend to do so as long as GNOME needs the fallback mode. Currently,
nobody else has stepped up to become a maintainer, but I'd be happy to
have someone join and do more active development -- it's just that I
don't have time for this myself.

---

### Post by Joan A. on 2012-07-16
> **AlbertJB said:**
> Per curiositat, com us va amb el gnome classic a Ubuntu 12.04? Jo segueixo sense poder executar l'onboard (perquè tinc el locale català) i de vegades em fa coses estranyes... Però s'aguanta prou bé. A tu també Joan A.?

Hola AlbertJB,

A jo la veritat que em va bastant bé el gnome-panel. He hagut de solventar alguns *bugs* com el del tema que vaig comentar aquí. També el *bug* de la pantalla completa perquè era impossible visualitzar un vídeo sense apareíxer les dues barres i també he tocat qualque efecte que no anava bé. La majoria dels *bugs* estan relacionats amb compiz i pel que he vist a launchpad estan fent feina per solvertar-los. El problema és que ja els llancen per la versió 12.10, així que tots els avenços els veurem ja a l'Octubre.

Sincerament, aquest entorn em va perfecte perquè puc utilitzar la meva màquina de 6 anys amb Ubuntu. Lubuntu i Xubuntu són ràpides però no m'acaben de convèncer a nivell estètic i de software inclòs, així que intent allargar la meva estància a Ubuntu, je, je. Si necessites ajuda, et contestaré amablement.

Salut! ;)

---

### Post by AlbertJB on 2012-07-16
Hola Joan A. Celebro que et vagi bé, jo també intentaré allargar la meva estada a Ubuntu fins que retirin el gnome-panel xD 

El que no m'agrada és veure que arreglin bugs del paquet gnome-panel per a la versió 12.10 d'Ubuntu, no pensen en els que ens volguem quedar en la 12.04 que és LTS. 

A mi tampoc no em convencen Xubuntu, Lubuntu..

En fi, gràcies per contestar, fins una altra!

---

### Post by wgarcia on 2012-07-16
AlbertJB, com comentàvem en un altre fil, els errors sempre s'arreglen per a la versió en desenvolupament, i si està ben justificat s'inclouen per a les versions estables. 

El problema és que s'ha de ser molt curós, no saps mai si arreglant una cosa trenques quatre més, i per tant s'ha de justificar bé l'aplicació dels canvis a una versió estable. A més tractant-se d'alguna cosa que afecti gnome, poden haver-hi moltes altres coses que depenguin d'aquest paquet, i és més probable que s'introdueixin problemes en altres coses si es un canvi no massa verificat.

---

### Post by Joan A. on 2012-07-16
> **wgarcia said:**
> AlbertJB, com comentàvem en un altre fil, els errors sempre s'arreglen per a la versió en desenvolupament, i si està ben justificat s'inclouen per a les versions estables. 

El problema és que s'ha de ser molt curós, no saps mai si arreglant una cosa trenques quatre més, i per tant s'ha de justificar bé l'aplicació dels canvis a una versió estable. A més tractant-se d'alguna cosa que afecti gnome, poden haver-hi moltes altres coses que depenguin d'aquest paquet, i és més probable que s'introdueixin problemes en altres coses si es un canvi no massa verificat.

Hola wgarcia,

La veritat és que es torben molt per arreglar el *bug* del tema. Jo he instal·lat el paquet .deb que varen llençar per Quantal fa un parell de mesos i va perfectament. Des d'Abril aquest *bug* està publicat a launchpad. Supòs que no és prioritari ja que no és Unity.

---

### Post by wgarcia on 2012-07-16
Però gnome-panel és un paquet d'Ubuntu o és un paquet general de Gnome? Perquè en aquest cas arreglar aquest error depèn d'una comunitat molt més àmplia que no la d'estrictament Ubuntu.

---

### Post by Joan A. on 2012-07-17
És un paquet d'Ubuntu.

---

### Post by wgarcia on 2012-07-17
He mirat i és un paquet del projecte Gnome:

[https://bugzilla.gnome.org/buglist.cgi?quicksearch=gnome-panel](https://bugzilla.gnome.org/buglist.cgi?quicksearch=gnome-panel)

Hauries de mirar si l'error està reportat aquí ("upstream") i enllaçar l'error d'Ubuntu amb aquest error de Gnome. 

Si em dones la referència de l'error d'Ubunt ho puc fer per tu.

---

### Post by Joan A. on 2012-07-17
> **wgarcia said:**
> He mirat i és un paquet del projecte Gnome:

[https://bugzilla.gnome.org/buglist.cgi?quicksearch=gnome-panel](https://bugzilla.gnome.org/buglist.cgi?quicksearch=gnome-panel)

Hauries de mirar si l'error està reportat aquí ("upstream") i enllaçar l'error d'Ubuntu amb aquest error de Gnome. 

Si em dones la referència de l'error d'Ubunt ho puc fer per tu.

Perfecte! Avui horabaixa ho miraré tot. Pareix que sí és un projecte de Gnome, ja que si instal·les Gnome Shell el mateix gnome clàssic també s'instal·la.

Moltes gràcies!

---


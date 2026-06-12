---
title: "Reparar el disc i instal·lació K3B i Java [ERA:reparar el disc]"
date: 2007-08-23
forum: Catalan Team
---

### Post by muleta on 2007-08-23
Com que ja no vull instal·lar nerolinux, obro una nova  línia, no sé si ho faig bé o si podia canviar el *Title* desde allà.

Per cert, hi ha algun sistema de crèdits o fórmula per agraïr els ajuds o per compensar als bons usuaris?.

Lluïsa, en un post em recomanaves treballar amb les aplicacions de la distribució. Però és que no trobo gairebé res.

He descobert una pàgina amb programari deb i confio trobar-hi eines útils però encara no me la he mirat.

A través d'afegir/eliminar programes, no aconsegueixo res. Per exemple: un programa per netejar el disc, buidar-lo de tots els trossets de programes que he intentat instal·lar, assegurar-me de que tot torna a funcionar bé, com abans de destrossar-ho.

Ahir n'havia trobat un a softonic i, quan l'estava insta·lant, em va indicar que ja era en la relació. Ara no el trobo, per molt que el busqui, no en recordo el nom, ni n'hi trobo cap de semblant.

Me'n recomaneu algun?.

---

### Post by papapep on 2007-08-23
Muleta, com ja t'ha dit la Lluïsa, si fas això d'instal·lar programari de fora d'Ubuntu per sistema tindràs MOLTS problemes.
No és la manera adeqüada de treballar.
Ubuntu té mil·lers de programes per a instal·lar, que no els sàpigues trobar no vol dir que no hi siguin :-) només vol dir que ENCARA no els saps trobar. Símplement.

Respecte lo de la neteja i tal que comentes, no et preocupis gaire. Com ja t'he dit altres cops, Linux no és Windows (Deo gratia) i també en això és diferent.

> A través d'afegir/eliminar programes, no aconsegueixo res. Per exemple: un programa per netejar el disc, buidar-lo de tots els trossets de programes que he intentat instal·lar, assegurar-me de que tot torna a funcionar bé, com abans de destrossar-ho.

El que has de fer és esborrar els fitxers o carpetes que has creat per als experiments que dius que has fet. No crec que sigui el tema tan bèstia com dius.

> He descobert una pàgina amb programari deb i confio trobar-hi eines útils però encara no me la he mirat.


Et torno a referir al primer comentari d'aquest post. 

I en vers d'invertir temps preguntant al fòrum com desfer els disbarats que puguis haver fet, inverteix-lo en preguntar abans de fer-los. Et garanteixo que és molt més profitós ;-)

> Me'n recomaneu algun?.

Jo personalment no te'n recomano cap, perquè no cal. Si fas servir el sistema d'Ubuntu d'instal·lació de paquets ell mateix s'encarrega de mantenir el sistema net i polit.
Quan instal·les un paquet ell controla què i on ho posa, i si ho esborres amb les comandes adeqüades o des d'el Synaptic ell s'encarrega de fer dissabte i deixar-te el sistema en ordre.

En conclusió, ja t'ho ha dit la Lluïsa, dones la impresió de voler córrer molt, i això no sol funcionar bé quan estàs començant. 
Et sona la frase "no vulguis córrer abans d'aprendre a caminar"? :-D

Vinga, ja saps que tens un bon "coixí" a la comunitat tant del fòrum, com de les llistes de correu, com del canal de xat. Al principi és dur el canvi de mentalitat, però és una inversió que et torna en escreix quan deixes de ser tan novell i ja controles un pèl el tema.

---

### Post by lluisanunez on 2007-08-23
hola,
t'ho torno a recomanar: fins que sàpigues millor el que et fas, cenyeix-te al programari dels repositoris Ubuntu.  Jo hi trobo tot el que necessito, bé, amb alguna excepció que ja he demanat que l'incloguin al Gutsy. Aquí hi ha una bona guia d'Ubuntu Feisty i els programes que conté la distro:
[https://help.ubuntu.com/7.04/](https://help.ubuntu.com/7.04/)
No sé si existeix una traducció al català.
I el wiki de documentació general també està molt bé:
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

La resta que anava a dir, ja ho ha dit en Papapep :-)
Pas a pas. Com que veig que t'agrada passar-te la nit davant l'ordinador, aprendràs molt ràpid.  Jo si fos tu m'asseguraria que domino la insta&#320;lació i desinta&#320;lació de paquets amb apt-get o la seva versió gràfica Synaptic. Després aprendria coses molt útils com arrencar sense el mode gràfic i restaurar còpies de seguretat dels arxius de configuració importants (gràfica, xarxa...) que se't puguin "trencar" fent proves. Per això t'anirà bé el tutorial de'n Papapep, encara que jo no crec que sigui qüestió d'imprimir-lo tot (a menys que vulguis decorar l'habitació, ei, te bonics colors, verd i negre), sinó com a consulta de referència i per aprendre cada dia un o uns quants comandaments interessants.

---

### Post by muleta on 2007-08-23
Seguiré els vostres consells, Luïsa i Papapep, gràcies.

Però, veieu què em passa?:

                                                                                
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuració del paquet «sun-java6-bin» &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474;     its subject matter.  It supersedes all prior or contemporaneous       &#8593;  
 &#9474;     oral or written communications, proposals, representations and        &#9618;  
 &#9474;     warranties and prevails over any conflicting or additional terms      &#9618;  
 &#9474;     of any quote, order, acknowledgment, or other communication           &#9618;  
 &#9474;     between the parties relating to its subject matter during the term    &#9618;  
 &#9474;     of this Agreement.  No modification of this Agreement will be         &#9618;  
 &#9474;     binding, unless in writing and signed by an authorized                &#9618;  
 &#9474;     representative of each party.                                         &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; For inquiries please contact: Sun Microsystems, Inc., 4150 Network        &#9618;  
 &#9474; Circle, Santa Clara, California 95054, U.S.A.                             &#9618;  
 &#9474;                                                                           &#9646;  
 &#9474; DLJ v1.1                                                  27APR2006ANS    &#8595;  
 &#9474;                                                                              
 &#9474;                                  <D'acord>                                   
 &#9474;                                                                        




Això és que se'm ha quedat fixat en el terminal. Deu ser alguna resta de fitxer d'aquells que us dic, oi?.

---

### Post by lluisanunez on 2007-08-23
Sembla que has de fer <D'ACORD>, em sembla que amb la tecla return... tens la insta&#320;lació de Java a mig fer, diria

---

### Post by papapep on 2007-08-23
Aquest tros de text que es veu, sembla una llicència d'utilització de programari (en aquest cas del Java de Sun) i, si no vaig errat, estarà esperant que cliquis damunt el "D'acord" o que premis Intro per acceptar-la i seguir el procés d'instal·lació i configuració del paquet.

Si hi ha alguna paraula de les que diem que no entens, no dubtis en preguntar-ho, és vital que parlem el mateix "idioma".

---

### Post by muleta on 2007-08-23
Nois, és que us havia començat a parlar d'aquesta pantalla en el fil anterior.

El meu problema és que no fa res. Com que no m'obeïa quan pulsava l'intro, he fet com si llegís tota la llicència i tampoc no es mou.

---

### Post by papapep on 2007-08-23
Prova a prèmer **un cop** el tabulador primer i després Intro. A veure què tal.

---

### Post by muleta on 2007-08-23
Sííííí !!!!!!!!!!!!!.

Ha sel·leccionat un munt de paquets de JAVA i de K3B, els ha instal·lat, em diu que els està configurant...  i s'ha quedat com esperant alguna altra ordre meva.

---

### Post by papapep on 2007-08-23
L'estat per defecte del terminal és esperar ordres teves.

Si tornes a veure "alló" que dius tu que acaba en "$", és que ja s'ha acabat la instal·lació :-D

Si vas al menú Aplicacions > So i video, hi trobaràs el K3B tot maco esperant-te ;-)

---

### Post by muleta on 2007-08-23
I, ara...

D'on trec el MAD aquest que vol?.

---

### Post by papapep on 2007-08-23
Fàcil !! ;-)

```
sudo aptitude install libk3b2-mp3 libmad0
```

---

### Post by muleta on 2007-08-23
I, tu, com ho saps?.

---

### Post by lluisanunez on 2007-08-23
> **muleta said:**
> I, tu, com ho saps?.

Ho sap perquè s'ho ha currat. Però tu pots saber-ho també si vas a can Synaptic, busques "MAD mp3", i et sortiran vàries coses entre les quals libmad0, si cliques sobre el seu nom veuràs que és la biblioteca MAD per a codificar MP3.

---

### Post by papapep on 2007-08-23
> **lluisanunez said:**
> Ho sap perquè s'ho ha currat.

No, si jo d'aquestes coses no en sé...m'ho ha xivat la meva gateta :-D

Conyes apart, com que tot no es pot saber de memòria, ho he buscat a internet.

Google, consulta "k3b mad library ubuntu", i la primera ocurrència és una nota d'error del Launchpad on comenten que els dos paquets necessaris són els que t'he indicat. 

(NOTA IMPORTANT: Has d'anar amb compte en no creure't TOT el que veus a internet. Has de tenir clar que la font és, com a mínim relativament, de fiar. En aquest cas el Launchpad d'Ubuntu és un bon lloc)

Com pots veure, no és important saber-ho tot, sinó saber on trobar-ho ;-)

---

### Post by muleta on 2007-08-23
VISCA, quantes coses que aprenc!.

No m'heu respost a allò dels crèdits o premis per agraïr els ajuds...

I, sí, Lluïsa, abans em déies que corro massa. Sé que s'ha d'anar a poc a poc per fer les coses bé però he d'acabar un munt de feina que havia començat quan aquell meravellós :^o altre sistema em va deixar fòra de combat.

Entre altres coses, havia descobert la pàgina mecanoscrit.com i estava descarregant un futimer de películes traduïdes al català. També tenia a mitges les sèries "RASCAL, el mapache" i "PERRINE, sin hogar" per a la meva filla. L'hi havia promès perque ella s'ho havia guanyat aprenent a nedar i a anar amb bicicleta. Ara no enten perque trigo tant a complir la meva paraula...

Doncs, som-hi!. El K3B no parla de gravar format AVI, només ISO. Com es resolt el tema?. Provaré això del Synaptic.

---

### Post by papapep on 2007-08-23
> No m'heu respost a allò dels crèdits o premis per agraïr els ajuds...

Tranquila, l'únic que has de fer és aprendre molt i ajudar als que en sàpiguen menys que tu, que ja veuràs que tot arriba.

(evidentment, no t'escaparàs de pagar un talladet si algun dia vens -cosa totalment recomanable - a algun dels actes que celebrem :-P)

> El K3B no parla de gravar format AVI, només ISO. Com es resolt el tema?

L'Avi (no el parent, el format de fitxers...) és un format que es grava com a dades, sense més. O sigui, al K3B, has de triar "Nou projecte de CD, o DVD, de dades" i ja està.

ACTUALITZACIÓ: Ara m'ha entrat el dubte de si quan dius "gravar format AVI" si vols dir passar un AVI  a suport CD o DVD, o preguntes com convertir d'algun altre format a AVI...què vols dir en concret??

---

### Post by muleta on 2007-08-23
Ja ho suposaves bé: Vull copiar en DVD les películes descarregades en format .AVI

Però, si en baixo alguna en .MPG què?.

I el K3B ja s'encarregarà de torrar-les i de fer tot allò que calgui o li he d'aportar codecs i mandangues?.

És que, clar, els altres programes m'ho féien tot i jo ni sé què féien. La meva filla i jo ens aixerpetellavem al sofà i miravem les películes a la tele.

---

### Post by papapep on 2007-08-23
Bé, en principi el que cal saber és què pot reproduïr el teu reproductor, valgui la redundància, de DVD que assumeixo que és el sistema que feu servir per a veure les películes.

Els "cremadors" de CD/DVD el que fan amb aquests fitxers és, "símplement", posar-los al suport òptic com aquell que els posa a un disc dur. No fa cap conversió especial.

Pensa que tant les películes en format AVI com en MPG són molt comunes, i per tant els reproductors actuals s'els solen menjar perfectament. 

En tot cas, com a molt et jugues un CD/DVD. Grava'l, i prova a veure què veus :-)

PS M'apunto el verb "aixerpetellar" .... :-D

---


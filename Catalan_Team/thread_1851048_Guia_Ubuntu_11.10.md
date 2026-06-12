---
title: "Guia Ubuntu 11.10"
date: 2011-09-27
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2011-09-27
Hola Ubuntaires!
Aquest cop he estat més ràpid que Canonical :)
Ja teniu disponible la nova guia a l'habitual enllaç:
[http://ca.wikibooks.org/wiki/Guia_Ubuntu](http://ca.wikibooks.org/wiki/Guia_Ubuntu)

Novetats:
He eliminat l'apartat "cóm descarregar la guia en pdf", donat que ja hi surt una tecla per descarregar-la en PDF a l'índex de la guia.
Parlo una mica del programari lliure, del Stallman i del Linux Torvalds.

També algun programa que altre nou, que ara no recordo, i he tret Synaptic :( tant que m'agrada!

Hem falta provar el tema d'entrar al sistema amb diferents escriptoris, però se m'ha esconyat la iso al virtualbox i ara no tinc temps per més experiments, que vaig molt enfeinat. Si puc, ho afegiré més endavant.

Espero us agradi a tots.
Salut i molt Ubuntu!

P.D.: Aquí també la guia, amb portada inclosa: [http://dl.dropbox.com/u/40989015/Ubuntu%2011_10.pdf](http://dl.dropbox.com/u/40989015/Ubuntu%2011_10.pdf)

---

### Post by akyra on 2011-09-28
La versió 11.10 ja??
Això si que és avanár feina.

Per cert que tal has vist aquesta nova versió?

Adeu

---

### Post by Miquel Ubuntero on 2011-09-28
[QUOTE=akyra;11292810]La versió 11.10 ja??
Això si que és avanár feina.

Per cert que tal has vist aquesta nova versió?

Doncs penso el mateix que la versió anterior, des de que van treure gnome, ja no m'agrada tant. Això del unity no hem fa el pes.
Prefereixo, per exemple, Xfce.
Salut!

---

### Post by wgarcia on 2011-09-29
Jo tinc la 11.10 a un sobretaula i un portàtil des de la versió Beta 1. 

Hi ha algunes novetats que no es noten a l'ús del dia a dia però que trobo força interessants. Per exemple s'ha canviat (provinent de Debian) la disposició de les llibreries i en principi ja no hi hauria d'haver-hi cap mena de problemes per usar la versió de 64 bits si es pot (es diu multiarch). Aquest canvi fins i tot sembla que permetrà passar d'una versió 32 bits a una 64 bits sense reinstal·lar. 

Quant a l'escriptori Unity, ja està plenament sobre Gnome 3, i a més les opcions s'han incrementat ja que a part de tots els escriptoris que es podien tenir amb Kubuntu, Xubuntu i Lubuntu, ara hi ha Unity 3D i 2D (els que manté Canonical per defecte), però es poden instal·lar i configurar fàcilment Gnome Shell, Gnome classic, i fins i tot alternatives que em semblen interessants com la que es mostra aquí:

[http://www.webupd8.org/2011/09/cairo-dock-240-released-with-custom.html](http://www.webupd8.org/2011/09/cairo-dock-240-released-with-custom.html)

L'escriptori Unity el noto més ràpid i més acabat en molts aspectes, tot i que encara queden alguns "bugs" a la versió Beta 2. Continua sent poc configurable, tot i que ja s'han incorporat alguns paràmetres nous com ara fer transparent el llençador i algunes coses més. S'ha simplificat força el menú de "Paràmetres de sistema", cosa útil pels usuaris novells però que empiparà els usuaris més avançat perquè ara han de buscar les configuracions en altres llocs. 

El Centre de Programari Ubuntu ha canviat de presentació, intentant fer-lo més atractiu per promocionar les aplicacions i perquè els desenvolupadors trobin convenient posar els seus programes a disposició dels usuaris d'Ubuntu.

L'arrencada també es força ràpida, i ara la sessió inicial per defecte es fa amb Lightdm que és més lleuger que Gdm i permet més configuracions. 

El que trobo més lent en els dos sistemes en què estic corrent la Beta 2 és l'apagada, però també tinc molts serveis corrent i encara no ho he investigat i potser que alguns dels serveis estigui fent la guixa en apagar el sistema (Apache, mysql, o alguns altre).

El nucli és 3.0.0 que incorpora diverses millores, i sembla que en una versió aviat vindrà finalment el pegat que arregla el problema d'ús de bateria d'alguns portàtils que s'arrossegava des de fa un temps als nuclis de Linux.

---

### Post by akyra on 2011-09-29
Jo estic esperant que arribi la nova versió per fer una instal·lació neta, sempre la faig.

A mi l'unity m'agrada força, i el que trobo a faltar és opcions de configuració (no trobo com afegir nous grups d'aplicacions i afegir accesos directes que es puguin posar a la barra).

Adeu

---

### Post by wgarcia on 2011-09-29
Per afegir accessos directes a la barra penso que el que s'ha de fer és crear-los a l'escriptori i després arrossegar-los a la barra. 

En quant a crear grups d'aplicacions penso que es fa amb el que es diu "quicklist" o alguna cosa així. Penso que s'explica en diversos llocs, si no ho trobes jo vaig crear un per a tenir un lloc únic on llençar diverses màquines virtuals amb el Virtualbox, puc repassar com ho vaig fer.

---

### Post by Miquel Ubuntero on 2011-09-29
Per afefir un accés directe a la barra esquerra, en tenir una aplicació oberta, li fas clic dret a la icona de la aplicació i prems "fixa aquí" o quelcom semblant.

---

### Post by lavinia.gac on 2011-09-30
M'he baixat la guia en pdf i l'he estat fullejant per sobre, trobo que pot ser un molt bon ajut i orientació per aquells que ens iniciem en l'apassionant món de GNU/Linux i de les distribucions Ubuntu. Jo sóc usuari de les anterior versions (les de l'escriptori Gnome) i m'està picant la curiositat de provar aquestes noves amb l'escriptori Unity. Em recomaneu fer el canvi? Hi ha molta diferència entre ambdos escriptoris?

Salut i moltes gràcies.

---

### Post by akyra on 2011-09-30
Les apliacions les pots afegir a la barra dreta si s'està executant, però no totes, per exemple el Netbeans i d'altres quan es tanca la aplicació desapareix.
Després altres aplicacions que s'exectuen amb el wine pasa el mateix, de fet força gent s'acabat afegint una aplicació tipus dock com "awn" o "gnome-doc".

Arrastrar aplicacions a la barra no funciona, pots afegir-ho a mà (obrint consola, navegant fins el /usr/share/applications/..., i modificant les característiques de l'accés directe), una mica conya.

Esperem que a la nova versió això ho millori.

Adeu

---

### Post by Miquel Ubuntero on 2011-10-01
Hola lavinia.
Sí que hi ha força diferencia entre gnome i unity. El millor és que ho comprovis pel teu compte.
La versió d'Ubuntu 11.04 permet d'entrar a l'escriptori tant amb unity com gnome clàssic des de la pantalla de login.
La recomanació és: Prova-ho i veuràs que bé t'ho passes! ;)

---

### Post by quitus on 2011-10-02
Entre gnome3, gnome clasic i unity... tinc a la meva família que no sap per quin mar navega, pobres. Cada dia que es lleven aprenen coses noves. Aquesta es la potencia del codi lliure.

salut.

---

### Post by wgarcia on 2011-10-03
Jo tenia por amb què passaria amb l'unity, però de moment les reaccions a la gent de la meva família han estat positives. El meu cunyat va començar al febrer amb Linux (Ubuntu) per primer cop, amb el gnome classic, i quan vaig tornar a veure'l s'havia actualitzat a natty tot sol i estava utilitzant unity sense queixa. La meva filla petita li vaig mostrar l'unity i va arronsar el nas però em va dir que volia actualitzar, va fer-ho i es va dir que s'havia adaptat però que no es canviés en un bon temps la interfície perquè no li agraden els canvis dràstics. La meva filla gran venia d'un netbook amb l'unity inicial i per tant es va adaptar de seguida.

---

### Post by savall on 2011-10-16
Hola Ubuntaires!

Sóc relativament nou en el món linuxero i concretament a ubuntu. A la nova versió 11.10 quan poso el pendrive a l'usb, s'obre automaticament el centre de programari i diu que no ha trobat res. La meva pregunta és, què carai busca? Sabeu què puc fer per que quan posi el pen, em mostri el seu contingut sense passar pel centre de programari?

Gràcies a tots i totes i espero alguna solució...

---

### Post by wgarcia on 2011-10-16
Hola Savall, millor si obres un fil per a la teva pregunta i no reaprofites un fil existent que no té res a veure amb el teu problema. 

Així si algú busca el mateix problema el pot trobar, aquí passaria desapercebut. 

Ara bé, a mi em passava el mateix i em sembla que el vaig solucionar de la següent manera: 

crea una carpeta qualsevol a l'escriptori

clica amb el botó dret i escull "obre amb una altra aplicació"

Escull "Fitxers"

A veure si això ho arregla

---

### Post by Lalaith on 2011-11-16
Hola!

m'he estat mirant la guia, és molt molt útil! Tot i així, pel que he estat llegint avui tinc alguns dubtes de l'apartat de seguretat. Els escric aquí perquè em sembla que és útil que es modifiquin a la guia, no (només) perquè els resolgueu per mi.

Basant-me en el següent fil: [http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177) que és un fil fixe de l'apartat de "security discussions", pregunto:

- quant a Tallafocs, tothom parla del UFW, en canvi a la guia es parla del Netfilter, que no n'he llegit per enlloc. Com és això? Quin ve per defecte? M'estranya que tothom parli de l'UFW i en canvi en una guia per a neòfits/es només es parli del Netfilter.

- pel que fa a l'apartat de Virus, justament al fil de més amunt desmenteixen que el sistema estigui lliure de virus, diu que encara que tinguis els ports tancats (que no sé què és però suposo que és el que tens per defecte) et podrien entrar i mirar-te dades. Et recomana que instal·lis el NoScripts pel teu navegador. 

- I el famós Apparmor que la gent comenta pels fòrums de seguretat, com és que tampoc hi surt?

- finalment, crec que seria molt útil incloure a la guia un apartat de "compatibilitats" o algo així, perquè alguns ordinadors tenen problemes en funcions molt bàsiques i cal saber que això és "normal" i és senzill d'arreglar (per exemple: problemes amb la il·luminació de la pantalla, el ventilador no deixa de funcionar al màxim encara que no calgui, l'ordindor no es suspèn, no es pot desactivar el mousepad...).  Simplement comentant que això pot succeir i guiar una mica per saber com cercar les solucions es faria un gran favor. Jo ja em pensava que m'havia comprat un ordinador mig-espatllat!

No sé si estic pixant fora de test, però m'he posat a mirar cosetes per evitar ensurts i no infectar l'ordinador nou i volia comentar això... perdoneu l'intromissió.:-\"

---

### Post by wgarcia on 2011-11-17
Crec que els teus comentaris són molt útils i de ben segur el Miquel els tindrà en compte que els vegi.

---


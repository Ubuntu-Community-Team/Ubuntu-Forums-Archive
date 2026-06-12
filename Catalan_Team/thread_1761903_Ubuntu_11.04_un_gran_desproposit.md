---
title: "Ubuntu 11.04: un gran desproposit?"
date: 2011-05-18
forum: Catalan Team
---

### Post by PatrickVogeli on 2011-05-18
Hola gent!

Encara que la veritat es que feia temps que no apareixia per aqui, encara estic viu i fent servir, com des de ja fa bastants anys, ubuntu! No ens rendim!

Bé, obro aquest fil perque tinc una opinió bastant crítica del Ubuntu 11.04, és amb diferència el que més problemes m'està donant, fins al punt que tinc baixa la versió 10.10 i m'estic plantejant fer un pas enrere.

En realitat, el problema no és tan tan greu, però si que hem toca molt els nassos. El que més m'afecta és:
1.- Compiz: no hi ha manera de que funcioni, ja que peta cada 2 per 3 i em quedo sense gestor de finestres. La solució que he trovat? Fer servir el metacity de sempre, quin remei. Això no m'havia passat mai!
2.- Problemes en el redibuixat de la pantalla: de sobte hi ha finestres que no es redibuixen, queden mig borrades com si la meitat hagues desaparegut. On més passa és amb el panell del gnome, que sovint queda tot fosc (el fons de pantalla el tinc negre), mig desaparegut.
3.- Últim i no m'importa tant perque no el faig anar però.. unity. No m'ha agradat gens ni mica, no ho trobo gens comode. I per adobar-ho, no funciona ni ràpid!

En fi, aquest problemes m'estan molestatnt molt, sobretot perque mai els havia tingut i el de la pantalla és molt molest. Tinc la impresió que s'han centrat massa en unity i la resta... ha quedat d'aquella manera.

No se, que en penseu vosaltres?? Heu tingut una experiencia més positiva amb la natty narwhal?

Salut!

---

### Post by wgarcia on 2011-05-19
Sembla un problema de la targeta gràfica, potser més atribuïble al nucli 2.6.38 que a Ubuntu directament, excepte la teva opinió de l'Unity que, com Gnome Shell, impliquen canvis importants respecte a l'experiència Gnome tradicional.

En el meu cas particular he actualitzat de moment un portàtil amb targeta Intel i un sobretaula amb targeta NVIDIA, i tot funciona bé. 

Quina targeta gràfica tens?

---

### Post by PatrickVogeli on 2011-05-19
una intel x4500.. drivers integrats al nucli. Ja he provat amb els repos xord-edgers que actualitzen tot aixo i no ha millorat res.

Probare instal·lant un kernel del ppa que hi ha.

Respecte al compiz... he vist que hi ha un bug penjat i tot, i sospito que no te res a veure amb la tarja grafica. Sempre peta per un 'segfault' degut a libregex.

---

### Post by wgarcia on 2011-05-19
La teva targeta gràfica sembla perfectament suportada. No he trobat tampoc informes d'error relacionats. A veure si amb el nucli del PPA millora la cosa.

---

### Post by PatrickVogeli on 2011-05-19
bé, amb el ppa tampoc s'ha millorat res.

El bug que tinc al compiz es aquest:

[http://bugs.opencompositing.org/show_bug.cgi?id=1339](http://bugs.opencompositing.org/show_bug.cgi?id=1339)

He buscat i no sembla que hi hagi gran cosa, no se'n parla molt ni res i, ara per ara, no tinc temps per embolicarme en aconseguir logs d'error, etc.


Salut!

---

### Post by CarlesOriol on 2011-05-21
Totalment en desacord amb tu en el tema del unity.

És fantàstic:

- ara no t'has de preocupar de la llista de programes que tens oberts ja no ho tens a la vista.
- Els menus superiors agilitzen la teva ment apareixent i desapareixent així com els butons de control de les finestres. 
- El menú d'aplicacions que abans s¡obria ràpidament ara son una serie de pantalles encadenades que et permenten gaudir dels nous dissenys de les icones
- I sobre tot el llençador abans alt+f2, ara alt+f2 o super+a o super+f et espera un temps raonable abans d'obrir les finestres per que clarifiquis els pensaments sobre el programa que vols obrir.

Com et dic... el unity és collonut.

Carles Oriol

---

### Post by PatrickVogeli on 2011-05-21
jajaja, esta clar que el meu punt de vista sobre el unity era completament erroni :D

---

### Post by CarlesOriol on 2011-05-21
M'oblidava... a més amplia els requeriments motivant el canvi de maquinari i creant un millor parc d'ordinadors.

---

### Post by wgarcia on 2011-05-22
CarlesOriol, demana que et tornin els diners aquests cabrons de Canonical ](*,)

---

### Post by akyra on 2011-05-23
Hola Patrick
A mi m'encanta Unity, i la instal·lació neta d'ubuntu no m'ha donat cap mena de problema, i la tarja gràfica em funciona perfecta, i és una ATI Radeon mobility 4500.

Has fet una instal·lació neta?

Salutacions

---

### Post by PatrickVogeli on 2011-05-23
si, primer vaig fer una actualització i, veient els problemes, vaig fer una instal·lació neta. I fa el mateix.

---

### Post by Xavi_Baix on 2011-05-23
Bones, acabo d'instal·lar-me la nova versió d'ubunt i tinc problemes amb el touchpad del portàtil. Em va passar ja amb l'anterior versió d'ubuntu però vaig poder-ho solucionar instal·lant el dkms i seguint els passos de: [http://ubuntuforums.org/showthread.php?t=1605430](http://ubuntuforums.org/showthread.php?t=1605430)
Aquesta vegada però això tampoc em funciona. Alguna solució? Gràcies!!

---

### Post by wgarcia on 2011-05-24
Per què no obres un fil específic per al teu problema amb un títol entenedor? Atraurà potser alguna persona que et pugui ajudar, aquí queda ocult en un fil de crítiques a l'Unity...

---

### Post by SiscoGarcia on 2011-05-25
Doncs a mi m'està funcionant molt bé, és cert que les versions alpha petaven molt més que en anteriors edicions, però des de la beta2 es va anar resolent.

Personalment crec que el despropòsit hagués estat no evolucionar l'escriptori, tot i que diria que han forçat molt la màquina per tenir-lo llest per la natty. Potser hagués estat millor madurar-lo més i publicar-lo amb l'oneiric, però també s'hagués trigat més a detectar errades (recordeu què va passar amb el KDE4, també van tenir un dilema semblant).

Un altre tema seria el que ha passat entre Canonical i Gnome, que ha impedit que s'unissin esforços i es treballés més junts en l'evolució del Gnome3 (un altre escriptori que canvia).

En qualsevol cas, crec que l'evolució de l'escriptori és molt interessant, tot i que costa una mica fer-te al nou, i algunes coses es troben a faltar, mentre que d'altres s'agraeixen...

... els meus 5 ¢

---

### Post by gunyoles on 2011-05-26
Jo el que puc opinar es que aquest llançament dona una mica més de feina al LoCo Team, però això passa amb totes les distribucions en que hi ha canvis importants. Recordo que en totes les evolucions hi ha problemes, sobretot perquè ens acostumem a un entorn i a una manera de fer les coses que quan ens ho canvien ens costa adaptar-nos al principi.
De moment a mi hem funciona be, potser perquè ja l'havia provat amb un portàtil.
De totes maneres recordeu companys que aquets problemes a l'hora de fer un canvi important en una distribució nova els hi passa a tots els SO, siguin lliures o no. Recordeu que passa amb la totpoderosa Microsoft o Apple, fan evolucions i la gent sempre creu que la versió anterior era la millor.
Hem de donar una oportunitat al Unity ja que te molt de futur per davant, si algú fa servir una pantalla tàctil que expliqui com li va, ja que aviat això serà d'allò més habitual.

---

### Post by wgarcia on 2011-05-26
Una altra reflexió és sobre la necessitat d'actualitzar o no. 

El cicle d'actualitzacions cada 6 mesos, i la versió de llarg termini de 2 anys, dóna l'opció d'actualitzacions més conservadores. 

És clar que et perds per un temps el Firefox 4, el LibreOffice, i altres versions noves que es van incorporant cada 6 mesos, però si el que vols és estabilitat la versió de 2 anys no et dóna tantes sorpreses com la de 6 mesos (tot i que he de dir que no sé si per sort o per què, vinc actualitzant tots els ordinadors que he tingut, sobretaula i portàtil, des de la versió 6.10 i mai no he tingut cap problema d'estabilitat, més enllà d'algun problema puntual amb el so o el sistema gràfic que sempre s'ha acabat solucionant força aviat). 

Fins i tot les versions de 6 mesos es poden anar actualitzant amb una mica de retard i això dóna temps a què es corregeixin coses o a sentir veus sobre la versió abans de llençar-se.

---

### Post by orestesmas on 2011-05-27
> **SiscoGarcia said:**
> 
Personalment crec que el despropòsit hagués estat no evolucionar l'escriptori, tot i que diria que han forçat molt la màquina per tenir-lo llest per la natty. Potser hagués estat millor madurar-lo més i publicar-lo amb l'oneiric, però també s'hagués trigat més a detectar errades (recordeu què va passar amb el KDE4, també van tenir un dilema semblant).


Coincideixo amb tu. Si no s'allibera aviat els usuaris no ho proven i els errors triguen molt a trobar-se. Va passar-nos el mateix amb el KDE4, i ara jo m'hi estic trobant amb el Moodle 2.0.

Penso que com a usuaris és un esforç que hem de fer per donar el nostre suport al programari lliure, que és al capdavall allò que fa funcionar els nostres ordinadors sense que ens costi un duro...

> **SiscoGarcia said:**
> 
Un altre tema seria el que ha passat entre Canonical i Gnome, que ha impedit que s'unissin esforços i es treballés més junts en l'evolució del Gnome3 (un altre escriptori que canvia).


Sense ser usuari de Gnome, també coincideixo en que aquest tema és força més preocupant, i farà alentir ben segur el progrés tant de Gnome3 com d'Unity.

En fi, sort, gnomeros...

---

### Post by wgarcia on 2011-05-27
No he seguit amb tots els detalls el culebró Gnome/Canonical, però pel que he pogut llegir les discrepàncies no són tan grans com semblen. 

La primera es va produir en Gnome rebutjar l'enfoc d'Ubuntu per als indicadors (això va passar el 2010). La segona òbviament en el desenvolupament i adopció com a escriptori principal d'Unity en comptes de Gnome Shell. 

Ara bé, per a la versió 11.10 l'Unity ja estarà plenament sobre GTK3 (ara està sobre GTK2). No s'ha alliberat sobre GTK3 perquè al moment de començar el cicle de desenvolupament de la versió 11.04 no hi havia encara una versió estable de GTK3. M'excuso si tècnicament dic alguna bajanada però em sembla que van per aquí els trets. 

Un cop que les llibreries siguin les mateixes les divergències seran menors.

---


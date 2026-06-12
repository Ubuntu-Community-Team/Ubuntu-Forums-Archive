---
title: "Problemes amb la gràfica'(suposo...)"
date: 2011-08-18
forum: Catalan Team
---

### Post by prostata on 2011-08-18
Bon dia, fa uns quants mesos vaig canviar l'ordinador, a grans trets és un:

Pentium Dual-Core CPU E5700-64bits
Gforce 210-1024 bits/PCI

Descripció del problema:

Tant en FF (6.= i d'altres inferiors), con en aplicacions tipus Gimp, amb molta freqüència, la pantalla de l'aplicació en la que estic treballant,es comença a des configurar, a perdre's per exemple la visió del seu contingut,comença per perdre la visió les les lìnies i apoc a poctota la pantalla es queda com si li hagues pasat un "sub-rayador" d'aquells reflorescent i la màquina es queda catatònica, no fa scrolling amb el mouse ni tan poc respon al teclat ni com dic al mouse haig de reiniciar.

Com deia crec que és un problema de la gràfica,però no tinc ni idea de com arreglar-ho. He mirat en Google i res de res.

Treballo am Ubuntu 10.10 i en general les aplicacions que faig servir més,son GIMP, FF, i poca cosa més, però en totes tard o dora acaba perdonar-me aquest problema.
Salut

---

### Post by snoopo71 on 2011-08-19
Quins drivers utilitzes?

---

### Post by prostata on 2011-08-19
Els que per defecte em proposa Ubuntu

---

### Post by snoopo71 on 2011-08-20
Prova d'activar els privatius, a mi no em donen cap problema.

---

### Post by prostata on 2011-08-20
Gràcies, aixi ho faré, et mantindré al corrent....

Salut

Edit: ara amb més temps he tornat a mirar ben bé els drivers que Ubuntu Maverick m'ha instal·lat, i és el 3.30.0 Nvidia 260.19.06 privatiu. Per altre costat he estat fent averiguacions per la xarxa i en molts llocs parlen de maverick i aquest drivers, al·legant que no son precisament una meravella i que en general presenten problemes,per tant ara encara estic més confós....¿?, què faig....

Salut

---

### Post by prostata on 2011-08-20
Finalment estic provant això....

[http://konsciencon.blogspot.com/2010/11/ubuntu-drivers-nvidia-v2601921.html](http://konsciencon.blogspot.com/2010/11/ubuntu-drivers-nvidia-v2601921.html)

---

### Post by prostata on 2011-08-20
Res, estem igual...continuaré investigant

---

### Post by snoopo71 on 2011-08-21
Bones, aviam jo utlitzo kubuntu 11.04 i tinc una GTX 280, ara mateix utilitzo els 270.41.06 privatius.
buscant al que seria el meu "synaptic" tinc instal·lats els paquets:

nvidia-current (drivers)
nvidia-common (arxius comuns)
nvidia-settings (gui per controlar clock, velocitat del ventilador i més coses)

Per instal·lar-los tu obre una consola i escriu:

sudo apt-get install nvidia-current nvidia-common nvidia-settings

Mira aviam si tens instal·lats el current i el common, i si no instal·la'ls. aviam que...
Sort.

---

### Post by snoopo71 on 2011-08-21
Si no passat per [aqui]("http://www.nvidia.es/object/linux-display-amd64-256.53-driver-es.html") i instal·lat aquests(256.53) que sòn el que et recomana nvidia.

---

### Post by prostata on 2011-08-22
> **snoopo71 said:**
> Si no passat per [aqui]("http://www.nvidia.es/object/linux-display-amd64-256.53-driver-es.html") i instal·lat aquests(256.53) que sòn el que et recomana nvidia.

Ja l'avia vist,però en descarregar s'obre una pàgina al ff com si fos un script molt gran....¿què faig...??. Esperava un .deb rpm o tar, no pas un script enorme...

Salut

Edit: he pogut descarregar el driver amb extensió .run, no tinc ni idea de com puc fer la instal·ació...

---

### Post by prostata on 2011-08-23
Company(s)
Aquests dies he provat versions diferents de linux,debian, lenny,sabayon i en totes la placa de video falla. He fet instal-lacions netas. Per contra la Gforce 210 em va molt bé en windows.¿que faig....? em compro una nova placa de video...voldria arrivar a comprendre com en el finestres,amb tot el què és,funciona i amb soft lliure em dona aquest problemes...ja estic molt cansat,porto dies cercan una sol-lució i ni de conya...

salut

---

### Post by snoopo71 on 2011-08-25
> **prostata said:**
> Company(s)
Aquests dies he provat versions diferents de linux,debian, lenny,sabayon i en totes la placa de video falla. He fet instal-lacions netas. Per contra la Gforce 210 em va molt bé en windows.¿que faig....? em compro una nova placa de video...voldria arrivar a comprendre com en el finestres,amb tot el què és,funciona i amb soft lliure em dona aquest problemes...ja estic molt cansat,porto dies cercan una sol-lució i ni de conya...

salut

És molt estrany, la 210 va bé, un company la tenia i cap problema, i no és la targeta ja que amb "window$" xuta, no ho entenc. Fes un liveUsb amb l'Ubuntu 10.10 a dins, instal·la'l i al cap d'un rato et dira que hi han drivers addicionals, activa'ls i aviam (si no t'ho diu fes ho manualment a   -> sistema -> drivers addicionals ). No sé que dir-te, la tarja és bastant comuna i l'ubuntu no hauria de tenir problemes amb ella. Em tens perdut! Per cert, això que et surt com amb subratllador son els drivers segur, que a mi a vegades m'ha passat(amb una ati 3870x2) amb el win7 i actualitzant ja no m'ho feia.

---

### Post by prostata on 2011-08-26
> **snoopo71 said:**
> És molt estrany, la 210 va bé, un company la tenia i cap problema, i no és la targeta ja que amb "window$" xuta, no ho entenc. Fes un liveUsb amb l'Ubuntu 10.10 a dins, instal·la'l i al cap d'un rato et dira que hi han drivers addicionals, activa'ls i aviam (si no t'ho diu fes ho manualment a   -> sistema -> drivers addicionals ). No sé que dir-te, la tarja és bastant comuna i l'ubuntu no hauria de tenir problemes amb ella. Em tens perdut! Per cert, això que et surt com amb subratllador son els drivers segur, que a mi a vegades m'ha passat(amb una ati 3870x2) amb el win7 i actualitzant ja no m'ho feia.

Company,doncs si tu estàs perdut imagina jo com estic. A drivers addicionals no més em surt "current". ¿Podria ser que hagués conflictes amb altres driver i per això...???¿hi ha alguna sentencia o conjunt de sentencies que em permeti fer per terminal nu "chekeo" controladors per tal de veure, si....?? I el mateix em pasa amb d'altres distros linux com ja he dit anteriorment.

Fa un més vaig estar per el teu poble,es molt bonic...felicitats!!!

Salut

---

### Post by prostata on 2011-08-26
He trobat aquesta pàgina i he fet el següent:

Terminal
Sudo lspci -n
El resultat ho pegat a la pàgina
Comprovar

I el resultat ha estat que: 10de0a65		nVidia Corporation	GT218 [GeForce 210] aquest dispositiu no en te controlador ni kernel....

La pàgina és [http://kmuto.jp/debian/hcl/index.rhtmlx](http://kmuto.jp/debian/hcl/index.rhtmlx)

---

### Post by snoopo71 on 2011-08-26
> **prostata said:**
> He trobat aquesta pàgina i he fet el següent:

Terminal
Sudo lspci -n
El resultat ho pegat a la pàgina
Comprovar

I el resultat ha estat que: 10de0a65		nVidia Corporation	GT218 [GeForce 210] aquest dispositiu no en te controlador ni kernel....

La pàgina és [http://kmuto.jp/debian/hcl/index.rhtmlx](http://kmuto.jp/debian/hcl/index.rhtmlx)

Deixam parlar amb el col·lega que te la 210 i aviam que em diu. Parlem dilluns o si puc demà! Au bon cap de setmana!

ps: A que si que és maco llívia!!

---

### Post by prostata on 2011-08-27
Ahir vaig tornar a fer una instal·lació neta de maverick,però vaig esculli ext3 en lloc de ext4.

I a partir d'aquí ¡¡¡¡sorpresa.....!!!!!!!!!!!, a drivers addicionals apareix "current" però aquest cop, (d'aquí la sorpresa), ara si que em diu que els drivers estan instal·lats  i a mes estan sent utilitzats. 

En el dia d'ahir només es va "penjar" la màquina un dos cops,es una quantitat de vegades que puc assumir,però de qualsevol manera no arribo a comprendre ni que siguin aquests dos o tres cops....penso que no s'haurien de penjar cap cop,com d'altre costat ens te acostumats ubuntu.

Seguiré informa'n....

Salut

---

### Post by snoopo71 on 2011-08-28
> **prostata said:**
> Ahir vaig tornar a fer una instal·lació neta de maverick,però vaig esculli ext3 en lloc de ext4.

I a partir d'aquí ¡¡¡¡sorpresa.....!!!!!!!!!!!, a drivers addicionals apareix "current" però aquest cop, (d'aquí la sorpresa), ara si que em diu que els drivers estan instal·lats  i a mes estan sent utilitzats. 

En el dia d'ahir només es va "penjar" la màquina un dos cops,es una quantitat de vegades que puc assumir,però de qualsevol manera no arribo a comprendre ni que siguin aquests dos o tres cops....penso que no s'haurien de penjar cap cop,com d'altre costat ens te acostumats ubuntu.

Seguiré informa'n....

Salut

Bé és molt estrany i segur que el problema segueix per allí però si pots anar tirant, me'n alegro!!

---

### Post by prostata on 2011-08-29
> **snoopo71 said:**
> Bé és molt estrany i segur que el problema segueix per allí però si pots anar tirant, me'n alegro!!

Gràcies: de moment sembla que no dona gaires problemes,ahir vaig treballar moltes raw i firefox, a més de Gimp...sense penjades...(no ho entenc), en cap altre de les moltes instal·lacions que vaig fer amb diferents distros,els drivers "current" sempre em deia"instal·lats però no utilitzats ¿?, ja veurem que passa d'aquí un quants dies/setmanes...

Salut

---

### Post by prostata on 2011-09-04
Desprès de l'ultim post meu de resposta i perdonar per definitivament solved el tema, només vull dir que des de fa dies vaig ins-talar l'Opera,com a conseqüència ja no he tornat a tenir cap mena de problema. el que he fet a estat deixar de banda firefox fins que al menys per a mi sigui més fiable...

Gràcies a tots per la vostra ajuda..

---

### Post by wgarcia on 2011-09-05
> **prostata said:**
> ... que vaig fer amb diferents distros,els drivers "current" sempre em deia"instal·lats però no utilitzats ¿?, ja veurem que passa d'aquí un quants dies/setmanes...


Aquest és un error que vaig informar ja fa uns mesos, l'estan mirant de solucionar, però encara no s'ha solucionat:

[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788)

---


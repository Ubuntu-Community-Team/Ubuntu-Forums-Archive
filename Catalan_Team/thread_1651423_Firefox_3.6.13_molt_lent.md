---
title: "Firefox 3.6.13 molt lent"
date: 2010-12-23
forum: Catalan Team
---

### Post by prostata on 2010-12-23
des de la darrera actualització de firefox veig que ara va molt lent en carregar les pàgines i tot ell en general. Ara es va actualitzar a la 3.6.13 i la lentitud és la característica principal d'aquesta actualització, si més no a la meva maquina que d'altre banda és la mateixa de sempre. Vaig mirar en aboput:config si algun paràmetre estava malament, però no trobo res anormal....¿algú de vosaltres te el mateix problema...??

bon dia i bones festes!!!!!

---

### Post by wgarcia on 2010-12-23
El meu va normal, tens moltes extensions habilitades? Pots provar de deshabilitar les extensions que tinguis, a veure si el problema desapareix, i si és el cas després anar actualitzant d'una en una a veure si pots identificar quina és la que causa el problema.

---

### Post by prostata on 2010-12-23
No més tinc 5 extensions, les de sempre i amb les quals sempre he treballat sense cap mena de problema. He fet el que em dius, ja ho havia provat abans però per si de-cas, i el problema continua igual, carregar per exemple aquesta pàgina pot trigar ben bé un minut i d'altres igual....

Salut

---

### Post by mrc2407 on 2010-12-23
Has provat amb algun altre navegador per comprovar si el problema és general o únicament del Firefox?

De fet, ara que ho dius a mi el Firefox també em va força lent... M'he passat a Chromium, però quan faig servir el Firefox tarda molt a obrir-se, a vegades la finestra es posa de color gris com si estigués a punt de col·lapsar-se... Suposo que el millor que es pot fer és eliminar-lo, eliminar els arxius de configuració i tornar-lo a instal·lar, aviam (fes còpia de seguretat dels marcadors, si vols).

---

### Post by prostata on 2010-12-23
tot el que em dius ja ho he fet, de fet, el test de velocitat dona els resultats esperats 12Mb baixada 1Mb pujada, els hi vaig explicar als de ONo i és cert no hi ha problema amb la velocitat de transmissió. De fet en altre màquina amb firefox però sota Windows, funciona perfectament...també he provat amb Opera 11, i Chromium i certament tampoc funcionen a "ple rendiment"... Opera es penja i Chromium més o menys..

Salut

---

### Post by prostata on 2010-12-24
Crec que ja se per on pot venir el problema de la lentitud de firefox 3.6.13 però el que no se és com solucionar-ho. Vegem:

Solament en iniciar-ho, miro en la Consola d'errors i apareixen un fotimé d'errors, per exemple:

Advertencia: Propiedad desconocida 'resize'. Declaración rechazada.
Archivo de origen: [http://www.vilaweb.cat/css/estils.css?1=1](http://www.vilaweb.cat/css/estils.css?1=1)
Línea: 38

Advertencia: Propiedad desconocida '-moz-opacity'. Declaración rechazada.
Archivo de origen: [http://www.vilaweb.cat/css/thickbox.css](http://www.vilaweb.cat/css/thickbox.css)
Línea: 98

Advertencia: Se esperaba un color, pero se encontró '#'. Error al interpretar el valor para 'background'. Declaración rechazada.
Archivo de origen: [http://ubuntuforums.org/clientscript...40f9-00098.css](http://ubuntuforums.org/clientscript...40f9-00098.css)
Línea: 1023

Advertencia: Se esperaba el final del valor pero se encontró '/'. Error al interpretar el valor para 'font-size'. Declaración rechazada.
Archivo de origen: [http://ubuntuforums.org/clientscript...40f9-00098.css](http://ubuntuforums.org/clientscript...40f9-00098.css)
Línea: 138

Però així de totes i cadascuna de les pàgines que visito, vegin-se les del propi fòrum.

Entenc que alguna cosa no camina bé amb el javascritp i d'aquí els problemes, la qual cosa no se com solucionar. He purgat firefox i reinstal·lat de nou però el problema persisteix, i no crec que en Linux-Ubuntu els problemes se solucionin com en Windows, o sigui desinstal·lant i reinstal·lant.

Alguna altra idea...???

---

### Post by wgarcia on 2010-12-24
Això de la consola d'error sembla normal, i té a veure amb petits errors i advertiments relacionats a les pàgines que estàs navegant. Jo també tinc un munt d'aquests errors i el meu Firefox va normal.

---

### Post by kimet on 2010-12-24
No serà el servidor DNS de ono el que va lent?

Salut.

---

### Post by prostata on 2010-12-25
Doncs no sé que pot ser, però ara estic en partició windows i funciona molt bé, faré un instal-lació neta de maverik i veurem....

---

### Post by Xirucat on 2010-12-25
Hola,
A mi em passa el mateix. La navegació va molt lenta des de la darrera actualització. Altres aplicacions d'Internet, com l'amule, funcionen bé, però el web va molt lent amb qualsevol navegador. La partició de Windows funciona bé, cap problema amb cap navegador. A veure si algú ens pot ajudar...

PD: Faig servir ONO (cablemodem)

---

### Post by quitus on 2010-12-25
A mi em va passar això mateix i va resultar ser el ipv6, per deshabilitar-ho en el firefox s'obre el navegador i en la barra de navegació "about:config"

cerquem network.dns.disableipv6 [COLOR="Red"]false[/COLOR]

i el modifiquem a [COLOR="Red"]true[/COLOR]

a veure si funciona.

salut

---

### Post by prostata on 2010-12-25
ja he fet lo del ipv6, però tampoc. de totes crec que el problema, a part d'alguna corrupció pot estar en la mateixa màquina, avui he tractat de fer una nova i neta instal-lació de maverik, però no hi ha forma d'arrencar l'ordinador. he fet servir gparted però un cop fet em dona error si no recordo malament...no boot no such partition, rescue grub, si no recordo malament, ara estic en un altre ordinador, parlo de memòria.  malgrat fer els canvis necessaris a la Bios per tal d'arrencar des de el maverik, també des de el cd de windows i des de el mateix super grub, sempre em fa fora, la màquina es para de forma aleatòria al no aconseguir "llegir" aquests cd's esmentats i ara ja la tinc "out off order". ja te uns quants anys 7 o 8 i penso que pot ser la pila de la BIOS, està gastada, penso però no estic segur, així que dilluns la portaré a que li facin un "tuning" i ja veurem que passa. he mirat per google tot el que podia fer que firefox no anés be i tot ho he provat... en fi, penso també que no sigui una instal-lació d'Opera la que hagi corromput el sistema, doncs pel visor de successos em donava molts errors que tenien a veure amb opera, no recordo quins però crec que tenia a veure amb player o flash player... en fi, gràcies per la vostra col-laboració.

Salut

Edito: haig de dir que tant en firefox com en opera com en chromium la navegació era molt i molt lenta, vaig mirar les DNS's de Ono i tot era correcte, per tant ho descarto en principi i més considerant que a la partició windows anava de fabula, i ara des de aquesta màquina que fa servir el mateix cable mòdem ONO, no tinc cap mena de problema en la velocitat de carrega de les web's.

---

### Post by Xirucat on 2010-12-27
> **quitus said:**
> A mi em va passar això mateix i va resultar ser el ipv6, per deshabilitar-ho en el firefox s'obre el navegador i en la barra de navegació "about:config"

cerquem network.dns.disableipv6 [COLOR=Red]false[/COLOR]

i el modifiquem a [COLOR=Red]true[/COLOR]

a veure si funciona.

salut

Ho he provat i segueix igual. Sospito que el problema és amb ONO ja que triga molt a connectar amb els servidors, o directament la connexió falla, però una vegada connecta, la pàgina carrega ràpid. El que m'estranya és que amb windows vagi bé...

---

### Post by prostata on 2010-12-27
> **Xirucat said:**
> Ho he provat i segueix igual. Sospito que el problema és amb ONO ja que triga molt a connectar amb els servidors, o directament la connexió falla, però una vegada connecta, la pàgina carrega ràpid. El que m'estranya és que amb windows vagi bé...

Perdona, però no, no és un problema d'ONO jo el vaig comprovar, i excepte que estigui molt equivocat, les DNS's d'un proveïdor no canvien en funció del SO que facis servir i si, com a mi, en entorn windows la carrega i navegació de pàgines va bé això m'indica que pot ser el que no va bé és el navegador. Clar que puc estar equivocat, però per això mateix em pregunto, ¿perquè en entorn windows si funciona la mateixa versió de firefox i en Ubuntu no? A totes les webs linux que he visitat per google per esbrinar la causa, tots o gaire be tots coincideixen que la 3.6.13 te seriosos problemes. Per tant ¿que et fa pensar que el problema és  d'ONO...??, més que res per saber-ho.A la màquina que estic ara va sobre windows i el firefox es la mateixa versió 3.6.13 i va que treu fum...¿per tant...on pot ser el problema, que amb Ubuntu no tira?

---

### Post by kimet on 2010-12-27
Els servidors DNS poden no ser els mateixos en els dos sistemes.
-Mira a etc/resolv.conf les direccions que hi apareixen i fes-hi ping i contrasta-ho em les respostes d'altres servidors (busca a google).
Pot ser que els servidors DNS que hi tens es saturin a determinades
hores o vagin lents en determinats llocs, proven d'altres companyies (no tenen per què ser de la mateixa amb la que tens l'adsl).

---

### Post by quitus on 2010-12-27
> **Xirucat said:**
> Ho he provat i segueix igual. Sospito que el problema és amb ONO ja que triga molt a connectar amb els servidors, o directament la connexió falla, però una vegada connecta, la pàgina carrega ràpid. El que m'estranya és que amb windows vagi bé...

mes que ONO, sembla un problema amb el router, es estrany que inhabilitant el ipv6 no funcioni, ja que aquests símptomes que expliques coincideixen del tot amb els del ipv6

---

### Post by prostata on 2010-12-27
> **kimet said:**
> Els servidors DNS poden no ser els mateixos en els dos sistemes.
-Mira a etc/resolv.conf les direccions que hi apareixen i fes-hi ping i contrasta-ho em les respostes d'altres servidors (busca a google).
Pot ser que els servidors DNS que hi tens es saturin a determinades
hores o vagin lents en determinats llocs, proven d'altres companyies (no tenen per què ser de la mateixa amb la que tens l'adsl).

Kimet, company...com ja he dit al llarg d'aquest fil tot això ja ho vaig provar, gràcies per la teva resposta...

Salut

---

### Post by prostata on 2010-12-28
> **quitus said:**
> mes que ONO, sembla un problema amb el router, es estrany que inhabilitant el ipv6 no funcioni, ja que aquests símptomes que expliques coincideixen del tot amb els del ipv6

Ja tinc de nou l'ordinador. He fet instal-lació limpia de Maverik, he tornat a inhabilitar ipv6 però continuo navegant molt lentament. si fos com dius quelcom del router, em podries dir per on  cercar...la veritat ja no se per on continuar...??

Salut i gràcies pel teu temps

---

### Post by wgarcia on 2010-12-28
En una altra part deies que havies mirat la velocitat de baixada i pujada i eren les esperades. Com ho vas fer? Pots fer des d'una terminal "ping" a alguna adreça d'Internet que coneguis i mirar la velocitat sota Ubuntu i sota Windows a veure si trobes diferència?

---

### Post by prostata on 2010-12-28
> **wgarcia said:**
> En una altra part deies que havies mirat la velocitat de baixada i pujada i eren les esperades. Com ho vas fer? Pots fer des d'una terminal "ping" a alguna adreça d'Internet que coneguis i mirar la velocitat sota Ubuntu i sota Windows a veure si trobes diferència?

Doncs la velocitat la vaig mirar en diferents webs de les tantes que hi han i en totes em donava els mateixos resultats. en general el cable d'ONO es molt estable i en gaire bé totes les webs em mostrava 12Mb de baixada i 1Mb de pujada.

He fet pings des de maverik i des de el finestres a les mateixes pàgines i de forma general no he trobat cap diferència significativa.El que si que vull dir es que per exemple ping des de la terminal cap problema, si ho faig per sistema>administració>eines de xarxa> eco (ping) no dona generalment cap mena de resposta i és que a més es penja aquesta eina. dins eines de xarxa la configuració que apareix és:

dispositiu de xarxa: bucle local (lo)
protocol: IPv6 ::1 masacara128  host
protocol: IPv4 127.0.0.1 

a connexions de xarxa apareix el següent:

cableada: Auto ethO  mai

Editant Auto ethO surt el següent:
ajustes IPv6 ignorada
ajustes IPv4: automàtic DHCP

Com podeu veure, crec que ho estic mirant tot, o al menys tot el que penso que puc mirar.

Per fer més comprovacions he instal-lat opera11 i fa el mateix o pitjor encara, no carrega ni en broma...i lo que fa trencar-me més el cap és no comprendre com essent la mateixa configuració del router, un cop funciona normalment ja no es toca mai, que amb la anterior versió de firefox tot anava com la seda i de sobte i tocant el valor de about.config, puc arribar a tenir aquests problemes. ¿ hi ha alguna forma de re-instal-lar novament al versió firefox 3.5...?? per provar una altre opció...que no quedi, clar

---

### Post by wgarcia on 2010-12-28
Si la velocitat fent "ping" és correcta, sembla un problema dels navegadors. Tot i que és estrany perquè fan servir configuracions diferents. Però per al firefox pots provar de canviar-li el nom al directori ".mozilla" de la teva carpeta d'inici i veure si això canvia alguna cosa, si tot segueix igual torna a restablir el nom de la carpeta per no perdre els favorits, etc.

---

### Post by prostata on 2010-12-29
> **wgarcia said:**
> Si la velocitat fent "ping" és correcta, sembla un problema dels navegadors. Tot i que és estrany perquè fan servir configuracions diferents. Però per al firefox pots provar de canviar-li el nom al directori ".mozilla" de la teva carpeta d'inici i veure si això canvia alguna cosa, si tot segueix igual torna a restablir el nom de la carpeta per no perdre els favorits, etc.


Doncs tot segueix igual..... ;-(

---

### Post by wgarcia on 2010-12-29
Mira a veure si seguint els suggeriments del següent enllaç:

[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

que van en la línia del suggerit per quitus, et serveixen d'alguna cosa.

---

### Post by prostata on 2010-12-29
PER PURA CASUALITAT.....Deu meu...........................!!!!!!!!!!!!!!!!!!

com que soc molt aficionat a la fotografia, amb el Gimp i RawTherapee, faig servir la meva Wacom Pen & Touch. fins fa pocs mesos no hi havia el Control Panel per tal de configurar-la i fer-la servir amb aquestes eines.

Fa ja un parell de mesos vaig trobar una darrera versió del Control Panel que si permet treballar de forma regular la Wacom esmentada.

Fa una estona quan la anava a re-instal-lar en Maverik em donava un avís d'error de dependències: python-gnome2-desktop-dev.
He nat a Synaptic i un cop instal-lada, el Firefox 3.6.13 TORNA A FUNCIONAR.........bé, com sempre. No funciona la Wacom, suposo que problemes amb Maverik que ja esbrinaré, però ara puc navegar a tota llet.

Perdoneu per la tabarra que us he donat, però el que jo menys m'imaginava, perquè no hi ha cap mena d'avís en firefox 3.6.13 en aquest sentit, es que aquesta dependència fos necessària per fer anar bé el FF.

Espero que ara tot continuï anant bé i que en apagar i encendre novament la màquina no s'he espatlli res de nou. Gràcies a tots pel suport i el temps.

Salut

---

### Post by Xirucat on 2010-12-29
Fins ahir cap novetat, navegació lenta. Aquest matí m'hi poso i quina és la meva sorpresa quan veig que, després d'un tall de servei d'un parell d'hores, torno a tenir connexió i tot va perfecte. El Firefox va tota pastilla com si res hagués passat. Ara ja estic segur que es problema és ONO. Fa 10 anys que en sóc client (abans era Menta) i no és la primera vegada que passa alguna cosa així. Truques al servei d'atenció al client i et diuen que el problema és el teu ordinador, fas les comprovacions de rigor (velocitats de pujada i baixada, ping) i sembla correcte, però la cosa no xuta. I de sobte, tall de servei i al cap de poc tot funciona com abans. Aquesta vegada ha estat una setmana, més o menys, de servei a mig gas. Altres vegades ha estat pitjor, talls constants, etc... 
En fi, sembla resolt, de moment. Gràcies a tots pels vostres consells

Edito: Ara he comprovat la velocitat i, casualment, ha pujat de 8 a 12M i de 300 a 500k... O sigui que és això, estaven remenant la xarxa.

---


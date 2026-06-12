---
title: "Necessito actualitzar NVIDIA-kernel modules"
date: 2007-10-07
forum: Catalan Team
---

### Post by sianeu on 2007-10-07
Al final he deixat correr la beta del Gutsy per que no m'en sortia amb l'acceleraciò gráfica. Però al tornar a Feisty m'ha sorprés trobara-me amb el mateix problema (i no m'hi havia trobat fins ara, tot i que ja la feia servir !!!!).

Tant es si intento instal·lar la última (100.14.11) com la penúltima (9755, es la que feia servir avans) versiò dels drivers NVIDIA, el que pasa es el mateix:

- Primer diu que faltan les llibreries **libc** de desembolupament
    instal.lo Linux-libc.dev i libc6.dev

- Després instl·lo el driver de Nvidia, i sebla anar bè.

Però quan reinicio el sistema grafic, no pot entrar. L'error que dona diu: 
API mismath: The NVIDIA kernel module has the version 1.0-7184 but this x module has the version 1.0-9755......   i que han de tenir la mateixa versio.

Com es fa aixó?

Per que les altres vegades que havia instal·lat el Feisty no m'hi havia trobat? Després de instal·lar-lo l'he actualitzat, tot menys els headers, image, i restricted-modules de la versió 2.6.20.16 que he llegit que donen alguns problemes (i jo en tenia i volia comprobar si era d'això). No crec que això hi tingui res a veure, oi?

Salut

---

### Post by pespin on 2007-10-07
```
API mismath: The NVIDIA kernel module has the version 1.0-7184 but this x module has the version 1.0-9755...... i que han de tenir la mateixa versio.
```

Com tu dius, això es un problema de compatibilitat de versions. Suposo que et baixes el .sh de la pàgina de nvidia. Has provat amb la paqueteria dels repositoris?

---

### Post by sianeu on 2007-10-07
Si, ja está provat. El primer cop que vaig instal·lar Feisty m'en vaig fer un fart de remanar fins que vaig aconseguir-ho amb els propietaris.

Salut

---

### Post by pespin on 2007-10-07
Quan dius que està provat et refereixes que et dona el mateix error? :confused:

---

### Post by sianeu on 2007-10-07
No. No recordo exactament els errors que donava en cada ciircunstancia, però no aconseguia acceleraciò 3d de cap manera.

Es molt dificil actualitzar el kernel de nvidia? Preferiria encarar-me cap aquesta soluciò si es posible.

Salut

---

### Post by jaume69 on 2007-10-07
Hola,bé,jo intentaré explicar una mica la experiéncia que he tingut amb Nvidia  Geforce Go 7300.(**Feisty**)
Quant instal.lo Ubuntu de seguida instal.lo Gestor Controlad.Restringits,i allà hi ha Controlador Nvidia.I cap problema,amb el **Kernel 2.6.20-16 restrictec modules.**
També hi tinc el kernel linux **386i **a part de **Generic** 2.6.20.**15 i 16** per què carrega més depresa en inici i off de la màquina,però jo arranco amb 2.6.20-16 generic.Si arranco amb 386i va més depresa al arrencar i off però després les aplicacions no van tan ràpides o lleugeres com en Kernel Generic.....,ves a saber perquè...?

I el Glx-new de Nvidia el vaig provar amb **gutsy** però instal.lat juntament amb Nvidia-glx i no vaig poguer instal.lar o l'un o l'altre sino tots dos...,em deia que per els efectes especials necessitava Nvidia glx-new.

També m'agradaria saber si es podria instal.lar el** Kernel 2.6.22-10 **u 11,12. en **Feisty**,crec que no...,en Gutsy si,que son els que porta per defecte.
Vaia roio....,perdó.:(

---

### Post by papapep on 2007-10-07
No passa res pel rotllo Jaume, la qüestió és si vols obrir un fil nou per fer alguna pregunta en concret i que la gent te la pugui respondre o no, ja que els temes queden molt dispersos si ho fem així.

---

### Post by sianeu on 2007-10-07
Ja ho he sol·lucionat. Però a la babalà, i per sort ha sonat la flauta.

Primer he actualitzat el nucli a la 6020.16, i res.

Després he recordat que el primer cop que vaig instal·lar Feisty primer vaig provar amb els "controladors restringits" del sistema (els que están en el menú "sistema") i només al final vaig atinar amb els drivers de Nvidia. Així que he repetit el cuento: amb els restringits del sistema no ha funcionat, com esperava, tot i que m'en he adonat que s'havia actualitzat el Nvidia-kernel module a la versiò 1.0-9631, que no es la del driver Nvidia (1.0-9755) però el error que donava ara no era aquest sino un altre que lamento no recordar. Aconsellava reinstal·lar el driver. No ho he fet i he reinstal·lat el driver Nvidia i ha funcionat.

Tot plegat es una mica liòs. Quan parlo del restringit em refereixo al de Nvidia que está en els repositoris del Feisty (sistema-administraciò-gestor de controladors restringits). Quan parlo de driver Nvidia em refereixo al descarregat de la seva página. Soposo que ara ja es imposible saber que passava...

El que no recordo i m'agradaria mirar, es l'ordre per saber la velocitat, els cuadres per segon. No se si era en aquest foro però no ho he trovat.

Salut

---

### Post by sianeu on 2007-10-07
Finalment NO ha funcionat bè. Al reiniciar l'ordinador s'en ha anat en orris altra cop.
Quan he dit que anava bè, simplement havia reiniciat les x amb gdm-restart. I juraria que funcionava l'acceleraciò i tot perque la pantalla m'havia agafat la seva resoluciò (1680x1050), cosa que només passa si tot va perfecte. Ara torno a estar a 1024x768 (canviant nvidia per nv al xorg.conf).

Ara el error torna a ser el del principi: tinc el Nvidia kernel 1.0-7184 i el driver va amb la 1.0-9755 i això no pot ser......

Ningú no sap com es canvia el kernel de Nvidia?

Salut

---

### Post by patrickfromspain on 2007-10-07
noi, tens fet un bon poti poti..

anem per parts. Desde synaptic tot:
nvidia-glx: desinsta&#322;lals tot (legacy, new, el normal.. qualsevol que puguis tenir insta&#322;lat)
nvidia-kernel-common: desinsta&#322;la'l.
Aplica els canvis i seguim.

linux-image-2.6.20-16-generic: reinsta&#322;la
linux-restricted-modules-2.6.20-16-generic: reinsta&#322;la. Si no ho tens insta&#322;lat, fes-ho ara.
nvidia-glx-new: insta&#322;la-ho.

Aplica els canvis. Obre el xorg.conf i torna a posar el driver nvidia. Reinicia. 

A veure si et va.

salut!

---

### Post by patrickfromspain on 2007-10-07
i per cert.. un altre cop, si insta&#322;les el driver de la web d'NVIDIA, assegura't que tens el linux-restricted-modules desinsta&#322;lat o, al menys, desactives el modul d'nvidia que incorporen. 

salut

---

### Post by sianeu on 2007-10-10
No ha funcionat. He fet  un munt de proves mès desinstal·lant i instal·lant paquets. Em rendeixo de moment, esperaré la versiò final de Gutsy. Gracies per les ajudes.

Salut

---

### Post by patrickfromspain on 2007-10-11
nomes un avis: no te res a veure ni amb gutsy ni amb feisty. Per un altre cop, sigues cuidados amb que insta&#322;les i de quina manera i sobre les incompatiblitats entre posibles paquets insta&#322;lats via synaptic i el que compi&#322;lis. Si tens insta&#322;lat el restricted-modules i insta&#322;les el driver d'nvidia de la web, et tornara a passar el mateix. Si vols fer una ultima proba: desinsta&#322;la els restricted-modules i insta&#322;lat el driver de la web n'Nvidia a vere si funciona. 

Salut!

---

### Post by Tomàs M. on 2007-10-11
> **sianeu said:**
> ...
El que no recordo i m'agradaria mirar, es l'ordre per saber la velocitat, els cuadres per segon. No se si era en aquest foro però no ho he trovat.

Salut

Per quan et torni a funcionar, que espero que sigui ben aviat: glxgears

---

### Post by CarlesOriol on 2007-10-11
El glxgears no és un programa de test de velocitat. Encara que a vegades s'ha usat és un error ja que et donarà una informació errònia ja que sols comprova un aspecte dels moltissims que té una gràfica + un servidor x + un controlador + llibreries 3d.

L'eina de configuració del compiz fusion té una opció per fer els benchmarks més complerta.

---

### Post by sianeu on 2007-10-14
He instal·lat el Gutsy rc2 i avans de fer res prefereixo consultar. He mirat el que Ubuntu ha instal·lat per defecte buscant amb el synaptic per paraules:

Per nvidia em marca com instal·lat:
*linux-restricted-modules-2,6,22,14 generic
*nvidia-kernel-common
*restricted-manager
*restricted-manager-core
*smartdimmer
*xserver-xorg-video-nv

Per linux:
*linux-restricted-modules-2,6,22,14 generic
*linux-restricted-modules-common
*linux-restricted-modules-generic

Estic obert a provar coses, però per anar cara a barraca (estic bastant fart d'aquesta historia) potser seria millor encarar directament cap el driver de la web de nvidia, que es el que m'havia funcionat fins ara (tot i que ja em fa dubtar)............  en fi, els qui en sabeu sou vosaltres. Què penseu que hauria de instal·lar i desinstal·lar ?

Ara tal com està tinc una resolució de pantalla de 1280x1024 sense acceleració gràfica. Una mica millor que amb la beta del Gutsy, però la necessito de 1680x1050. La meva tarjeta gràfica es una Asus geforce 7600 GS agp, que deu de tenir una configuració que es la font de tots els problemes. 

Potser també pot ser interessant el missatge de glxinfo:
sianeu@unicorn:~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

Si voleu cap altre informació, digueu-m'ho.

Salut

---

### Post by patrickfromspain on 2007-10-14
no es dificil: has d'insta&#322;lar el packet nvidia-glx-new i despres editar el fitxer xorg.conf  per activar el driver nvidia en ves del driver nv.

Tambe ho pots fer fent servir el restricted manager, activant el driver per la grafica i ja esta.

---

### Post by sianeu on 2007-10-14
He fet servir la primera opciò i no a funcionat. De tota manera el driver que estava actiu quan he modificat el xorg desprès de instal·lar el glx-new era el vesa i no el nv.

Salut

---

### Post by sianeu on 2007-10-14
He de corretgir, sí que funciona. Al principi he fet simplement 
/etc/init.d/gdm restart
per que tenia entès que era suficient.

Després he pensat que potser seria bo de saber quin error era el que donava. Aixi que he tornat  a posar el driver nvidia en el xorg i he reiniciat. I llavors ha funcionat.

Però la frecuencia no es la adecuada (50 Hz en comptes dels 60 de la pantalla) i tampoc tinc el programa de configuraciò de nvidia per conectar la sortida tv (que a més em sembla que sol·lucionaria el primer problema). Que he de instl·lar per tenir-lo (amb el driver de la web de nvidia venia per defecta) ?

Salut

---

### Post by patrickfromspain on 2007-10-14
el tens insta&#322;lat ja. Nomes has de posar en terminal (o be en la finestra que et surt al fer alt+F2) nvidia-settings i et sortira.

Salut

---

### Post by sianeu on 2007-10-14
Tot arreglat, moltes gràcies. 

Una última qüestiò: es normal que no funciones al reiniciar les x i hagès de reiniciar l'equip?

Salut

---

### Post by orestesmas on 2007-10-16
No sé si ha estat aquest el teu cas, però molt sovint els problemes venen perquè encara que instal·lis la mateixa versió del driver tant a la part del nucli com a la part de les X, normalment hom s'oblida que la versió del driver del nucli **que està corrent en aquests moments** és l'antiga, que encara està en RAM.

El que s'hauria de fer és sortir del mode gràfic, descarregar a mà el mòdul nvidia (l'antic) i carregar el nou, també a mà.

Normalment això es corregeix inadvertidament en rebotar la màquina, i per això tot funciona "de cop i volta".

---


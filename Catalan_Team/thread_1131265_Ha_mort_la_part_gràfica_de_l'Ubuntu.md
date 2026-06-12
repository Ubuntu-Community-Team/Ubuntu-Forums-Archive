---
title: "Ha mort la part gràfica de l'Ubuntu"
date: 2009-04-20
forum: Catalan Team
---

### Post by joana ebrenca on 2009-04-20
Hola,

ahir vaig estar instal·lant-me el Wengophone per fer trucades per internet. Arran això, este matí he anat a encendre l'ordinador i ha etat impossible encendre la versió gràfica. Al principi es veien unes ratlles vermelles estranyes a l'escriptori i no podia moure el ratolí. He reiniciat i m'ha donat errors. He fet fotos a les ratlles vermelles i als errors per veure si em podríeu ajudar.

Sento no especificar més però realment no entenc res. M'interessa molt recuperar la sessió perquè tinc dos treballs de la carrera desats a l'ordinador que encara no he pogut imprimir, i si ho perdo són molte shores de fanea que em tocarà repetir...

Moltes gràcies per la vostra ajuda.

---

### Post by SiscoGarcia on 2009-04-20
Hola Joana,

No m'hi entenc gaire però sembla que has perdut les X (això és que t'has quedat sense la part gràfica com bé dius). T'ho dic així perquè potser si vas cercant-ho d'aquesta manera igual trobes la solució. A part de googlejar, pots fer un cop d'ull per [aquí]("http://ubuntuforums.org/search.php?searchid=58236736"). A més, estaria bé que donessis més informació de la teua màquina (model d'ordinador, tarja gràfica que fa servir, etc.).

EDITO: Ja has fet el que et diu la pantalla negra: "Un cop fet el manteniment del sistema, prem CONTROL-D per tancar la consola de manteniment i reiniciar el sistema"?

Prova-ho perquè potser no et cal res més.

Ja diràs.

---

### Post by torracastanyes on 2009-04-20
Crec que primer t'haríes de fixar en el que diu més amunt:

UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY

Es a dir, que hi ha algún problema amb el sistema de fitxers que cal resoldre.
Només et cal escriure: sudo fsck /dev/sda1  i esperar que acabi.

---

### Post by joana ebrenca on 2009-04-21
He fet el que m'ha dit torracastanyes i he reiniciat l'ordinador. Se m'ha iniciat tot correctament, amb l'escriptori funcional  i tot. Però als dos minuts de moure el ratolí i obrir una finestra han tornat a aparèixer les ratlles vermelles i se m'ha quedat penjat, no podia moure res. He reiniciat i des de llavors cada vegada que obro l'ordinador m'apareixen ralles blaves, blanques i vermelles molt gruixudes en vertical que ocupen tota la pantalla i no em deixen fer res :?

Us n'adjunto una foto...

---

### Post by lluisanunez on 2009-04-21
Al menú de Grub, tria l'opció sense gràfics i fes login
Fes això:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by lo gambusí on 2009-04-21
Hola,

ara per no sé ben bé quin sant he pogut entrar amb les X. He recuperat tots els arxius importants i estic escrivint des del meu pc. Suposo que en qüestió de temps se'm penjarà, però bé...

He fet el que m'ha dit lluisa a la terminal i hem diu >  &#9474; En comptes d&#8217;haver de comunicar&#8208;se directament amb el maquinari de        &#9474; 
 &#9474; vídeo, podeu configurar el servidor X per tal que realitze algunes        &#9474; 
 &#9474; operacions, com el canvi de mode de vídeo, fent servir el controlador de  &#9474; 
 &#9474; «framebuffer» del nucli.                                                  &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; En teoria qualsevol de les aproximacions hauria de funcionar, però en la  &#9474; 
 &#9474; pràctica a voltes una ho fa i l&#8217;altra no.  Habilitar aquesta opció és     &#9474; 
 &#9474; l&#8217;elecció més segura, però no dubteu d&#8217;inhabilitar&#8208;la si vos sembla que   &#9474; 
 &#9474; causa problemes.                                                          &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Voleu emprar la interfície cap al dispositiu de «framebuffer» del nucli? Què faig? Sí o no?

PS: no vos espanteu per l'aparent esquizofrènia, joana ebrenca és la meua companya de pis :)

---

### Post by lluisanunez on 2009-04-21
Estem parlant d'un altre problema o has canviat d'identitat (i gènere)? :-(

Mai he hagut d'arreglar el framebuffer aquest però sembla que et diu clarament que aquesta opció és la més segura, no?

EDITAT: acabo de veure el PS sobre la Joana

---

### Post by lo gambusí on 2009-04-21
Ho he fet, seguint tots els passos.> logambusi@logambusi-laptop:~$ sudo dpkg-reconfigure xserver-xorg
[sudo] password for logambusi: 
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090421183959
logambusi@logambusi-laptop:~$ 


Ara què hauria de fer? Reinicio per comprovar que funcione? És que em fa temor rebentar-ho tot un altre cop i preferiria assegurar-me'n abans...

Gràcies

---

### Post by joana ebrenca on 2009-04-21
Efectivament s'ha penjat. He reiniciat i ara em diu el que surt a les fotos que adjunto.

Què puc fer?

PS: a l'opció que no es veu sencera diu "run ubuntu in low-graphics mode for just this session"

---

### Post by tanreb20 on 2009-04-21
Home lo logic seria reconfigurar els grafics no?

Segona opció!

---

### Post by torracastanyes on 2009-04-21
Exactament, i com que dels errors anteriors, els dos primers es refereixen al framebuffer, potser millor dir-li que no, aquest cop.

---

### Post by joana ebrenca on 2009-04-21
Quan ho faig em dona les tres opcions que podeu vore a la pantalla.

Si li dic la tercera no em fa res. Torna a aparèixer la mateixa pantalla una i altra vegada. Si li dic la primera o la segona es queda penjat. 

Llavors tiro enrere i entro en *low graphic mode* i se'm carrega l'escriptori de manera normal però en una configuració gràfica estranya, amb les icones i l'escriptori en general molt ampliat. En principi però puc fer-lo anar amb normalitat, excepte per això de les mides.

Ara puc fer servir la consola suposo. Alguna idea?

---

### Post by lluisanunez on 2009-04-22
Doncs diria que els errors estan arreglats i que ara vol saber quina configuració t'agrada. Com que dius que el tens amb baixa resolució, tria la segona opció (nova configuració)

---

### Post by lo gambusí on 2009-04-22
Quan trio la segona o la tercera opció no puc fer res, em torna a portar a triar les mateixes opcions una i altra vegada.

La clau seria entrar amb la primera opció i fer alguna cosa (el què?) perquè es veigués normal i no amb la pantalla desproporcionada i tallada. No sé si m'explico. Ara no tinc l'ordinador aquí, però si no m'he explicat a la tarda puc fer una foto.

---

### Post by lluisanunez on 2009-04-22
I si tornant enrera, a partir de 
```
sudo dpkg-reconfigure xserver-xorg
```
quan pregunti lo del framebuffer dius NO...?

---

### Post by lo gambusí on 2009-04-22
Em diu això:

> logambusi@logambusi-laptop:~$ sudo dpkg-reconfigure xserver-xorg
[sudo] password for logambusi: 
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090422171615
logambusi@logambusi-laptop:~$ 


---

### Post by joana ebrenca on 2009-04-22
Bé, donat que tot el que havia de recuperar ja ho he recuperat i que no hi tinc res a perdre, he decidit de reinstal·lar l'ubuntu des de zero, que ja tocava fer-ho des de fa un temps.

Gràcies igualment, però.

Salut!

---

### Post by quitus on 2009-04-22
seria bo, si vols tornar a instal·lar de nou, fer un format ext4, així estaríeu preparats per la jaunty.

salut

---

### Post by oriolsbd on 2009-04-23
És més, depen de com, ja que fas una instal·lació neta, potser vols aprofitar que avui mateix ja sortirà Jaunty...

Salut!

---

### Post by joana ebrenca on 2009-04-26
Ara sí que ja no entenc res.

He fet una instal·lació del 8.10 des de zero... i continuen apareixent-me les ratlles i tots els problemes gràfics! O_O

Crec que provaré de descarregar la 9.04 i provar a veure què passa, però no ho entenc en absolut :?

---

### Post by lo gambusí on 2009-04-26
He fet el que he dit com a Joana Ebrenca però amb la 9.04 em passa exactament el mateix :?

O mentre es carrega apareixen tot de ratlles roges i es queda penjat; o es carrega i al cap d'uns minuts comencen a aparèixer les ratlles i es penja llavors. 

Si entro com a LiveCD no tinc problema, per tant deduixo que si he d'instal·lar o tocar alguna cosa des d'allí podré fer-ho.

Em podeu ajudar?

---

### Post by lo gambusí on 2009-04-27
Crec que el problema és de l'ordinador i no de l'Ubuntu. Em baso en el fet que, depenent de la posició de les mans sobre l'ordinador i la pressió que faig mentre escric apareixen més o menys ratlles roges.

Si faig, per exemple, una mica de pressió amb la mà a la banda esquerra del *touchpad*, apareixen més ratlles a la pantalla que si no en faig. 

Esteu d'acord amb mi amb que el problema no és de programari sinó de maquinari? 

Teniu alguna proposta, més enllà de llençar l'ordinador a la paperera, tenint en compte que l'ordinador se'm penja als 10 minuts i no puc treballar?

Moltes gràcies

---


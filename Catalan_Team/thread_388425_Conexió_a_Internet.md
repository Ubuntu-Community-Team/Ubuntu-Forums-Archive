---
title: "Conexió a Internet"
date: 2007-03-19
forum: Catalan Team
---

### Post by Josep Maria on 2007-03-19
Acabo d'instal·lar l'ubuntu 6.10 i no hi ha manera de connectar-me a Internet.
Sabeu com puc fer-ho?
Gràcies

---

### Post by CarlesOriol on 2007-03-19
Quin tipus de conexió tens ? Router cablejat, wifi, modem ?

---

### Post by Josep Maria on 2007-03-19
Aviam: 
Avant tot gràcies Carles.
Tinc una connexió ADSL amb Ya .com, amb una IP fixa.
He anat a la finestra de Xarxa, i he posat totes les dades Ip, Mascara, Gateway,i també la DNS. 
El meu router és un D-Link DSL-524T, i crec que el problema deu venir d'aquí, ja que he arrencat un altre ordenador que és en la mateixa xarxa des del CD i tampoc el puc connectar.
Pot ésser que el Ubuntu no pugui reconèixer el meu router ?
Si haig de baixar un driver, com puc fer-ho sense connexió ?
L'Ubuntu és preciós, i fora d'això va del tot bé. Seria una llàstima no poder-lo utilitzar.

Moltes gràcies, de veritat.


Josep M. Miquel

---

### Post by Josep Maria on 2007-03-19
Carles, veig que m'he descuidat de dir-te que el meu router és cablejat.

---

### Post by orestesmas on 2007-03-19
Hola Josep Maria,

Quan dius que la teva ADSL té IP fixa, deus voler dir que la IP pública és fixa, però que les IP dins la teva subxarxa no tenen res a veure amb aquesta IP fixa, i és el router qui s'encarrega de fer la traducció (NAT) entre adreces privades i pública.

Jo no tinc experiència amb routers amb IP fixa, però jo de tu miraria de configurar el Linux per tal que configurés la xarxa automàticament a través del router via DHCP.

La manera exacta de fer-ho no la sé tampoc, perquè no utilitzo el Gnome, suposo que a la finestra de xarxa hi trobaràs alguna opció per indicar-li que agafi l'adreça per DHCP.

Salutacions i sort.

---

### Post by CarlesOriol on 2007-03-20
No has de tenir cap problema per que et funcioni.

Sembla que el **router no esta ben configurat** per DHCP. 

Pel que dius sembla que tens un ordinador amb un sistema operatiu privatiu. Si es així en aquest fes [FONT="Courier New"]Inici[/FONT] -> [FONT="Courier New"]Executar[/FONT] -> (escrius) [FONT="Courier New"]cmd[/FONT]. Se t'obrirà una finestra de comandes i allà escrius [FONT="Courier New"]ipconfig /all[/FONT]

Això et mostrarà la configuració de xarxa actual. 
(et copio un exemple que no ha de ser igual que el teu)

[FONT="Courier New"]Adaptador Ethernet XarxaLocal:

   Sufijo conexión específica DNS:
   Descripción . . . . . . . . . : Broadcom NetXtreme Gigabit Ethernet
   Dirección física. . . . . . . : 00-14-61-BC-C6-9D
   DHCP habilitado . . . . . . . : No
   Dirección IP. . . . . . . . . : **192.168.0.5**
   Máscara de subred . . . . . . : **255.255.255.0**
   Puerta de enlace predet.. . . : **192.168.0.1**
   Servidores DNS. . . . . . . . : **193.152.63.197**[/FONT]

Ens calen els darrers 4 nombres de 4 digits. apunta'ls

*... ara deixem-nos de joguines i tornem al linux.*

Pots anar a Administració -> Treball en xarxa i configurar-ho:
(em baso en l'exemple fictici anterior. Et recordo que aquests nombres que entro jo no seran iguals que els teus i si els escrius no et funcionarà).

---

### Post by patrickfromspain on 2007-03-20
en ves de configurar una ipfixa, pobra a posar obtenir una adressa a traves de DHCP

---

### Post by CarlesOriol on 2007-03-20
patrickfromspain: dhcp és la configuració per defecte, si no li agafa és que el router no ho té posat.

---

### Post by Josep Maria on 2007-03-21
Gràcies a tots.
He fet el que m'ha dit en Carles Oriol, i no funciona.
Després he mirat la configuració de xarxa, i m'he adonat que en windows funciona automàticament (DHCP) He tornat a entrar a l'Ubuntu i ho he provat de configurar així i tampoc rés.
Aviam, he pensat que podria ser que funciones si entrés al router i li demanés que assignés IP fixes, i li donés una a cada equip.
Com puc mirar dins de l'Ubuntu si tots els dispositius funcionen correctament, ja que sinó va amb tot això, només pot ser que no estigui treballant la Xarxa.
De fet la sortida Ethernet surt directament de la placa mare, una Intel Desktop board, i podria ser per això que no funcionés.
M'estranyaria molt, perquè he pogut entrar al router des del Firefox de l'Ubuntu.

No us havia escrit abans per no amoïnar-vos.

Moltes gràcies, de nou.


Josep Maria

---

### Post by patrickfromspain on 2007-03-21
aaaaah xic!!

Si has pogut entrar desde el firefox de l'ubuntu al ruter no hi ha problema, tot funciona :) Posa-ho tot de la mateixa manera que tenies quan has pogut entrar al ruter desde ubuntu.

El que passa es que deus tenir un problema de DNS.

Sistema -> Administració -> Xarxa, alla vas a DNS i poses aquestes 2:

208.67.222.222
208.67.220.220

Acceptes tot i ja hauria d'estar

salut!

Per cert, sobre el tema d'entrar al ruter per posar IP fixes, no has de tocar res. Com que sas la direccio del ruter, el que hauries de fer, es assignar a ubuntu (desde administracio -> xarxa) una ip fixa. La ip sera (suposant que el teu ruter sigui 192.168.0.1) 192.168.0.X, on X es un numero més gran que 1 (jo posaria 50 per exmple). La porta d'enllaç sera la direccio del ruter. No se si m'explico

---

### Post by ilku on 2007-03-21
Hola:
Despres de canviar la configuració de la xarxa a l'ubuntu, prova a reiniciar la maquina, perque sovint es queda una mica pillat.
Es a dir, si posses que sigui amb obtencio automatica de IP per DHCP reinicies i proves a veuire si accedeixes. Amb sembla que es un problema de sobreescriure el resolvconf, no n'estic segur.

---

### Post by CarlesOriol on 2007-03-21
totalment d'acord amb en patrick

---

### Post by Josep Maria on 2007-03-21
Funciona!
T'estic responent des de l'Ubuntu.
Eren les maleïdes DNS.

Gràcies és poc.

Josep Maria

---

### Post by Fornols on 2007-03-21
Hola,
Fa 2 dies que he instal·lat UBUNTU 6.06 i no he pogut conectar-me a internet.
He seguit amb molt interès les indicacions que heu donat per conectar-se, però en el meu cas ja començo amb alguna cosa diferent.
Si vaig a SISTEMA - ADMINISTRACIÓ - , no tinc la opció "XARXA", sino que només tinc la opció "EINES DE XARXA".


Tinc un router ADSL inalàmbirc.

La veritat és que no sé com seguir per fer la conexió a Internet.
Algú em pot ajudar?

---

### Post by patrickfromspain on 2007-03-21
eines de xarxa él mateix. Jo estic fent servir la versio 7.04 i aqui es xarxa. A la 6.06 i 6.10 hem sona que es el que dius, eines de xarxa.

Ves alla i  a veure si et detecta la tarjeta inalambrica.. ja t'aviso que segons quina tinguis, pot ser "puta" de configurar. Quina tens? Saps el chipset?

---

### Post by Fornols on 2007-03-21
Gràcies per respondre tan aviat.

Disculpa també perque en temes de routers no tinc massa clar els significats dels noms, però et diré que la tarja que tinc inserida al router és de telefònica i el fabricant és AMPER. Dir també que a l'ordinador hi tinc un conector USB que envia la senyal al router, i és del fabricant ZYXEL, model ZYAIR B-220.
A dins de Eines de Xarxa, hi han varies "pestanyes": Dispositius - Ping Estat de la Xarxa- Traça una ruta, etc.
Com ho veus?

---

### Post by patrickfromspain on 2007-03-21
a dispositius, alla hi hauria d'haver la teva inalambrica, ho veuras per la icona i la descripcio.. si no hi es.. haurem d'investigar si funciona el teu usb, amb quins drivers, etc etc

---

### Post by Fornols on 2007-03-21
Bé, a la pestanya DISPOSITIUS hi ha el següent:
Protocol: IPV4
Adreça IP 127.0.01
Màscara de xarxa/prefix 255.0.0.0
Difusió (en blanc)
Abast (en blanc)

Protocol: IPV6
Adreça IP ::1
Màscara de xarxa/prefix 128
Difusió (en blanc)
Abast HOST

iNFORMACIÓ DE LA INTERFICIE
Adreça del maquinri: Loopback
Multidifusió: Inhabilitada
UTM: 16436
Velocitat d'enllaç: (en blanc)
Estat: Activa

Què més et puc dir?

---

### Post by patrickfromspain on 2007-03-21
buaaaaaaaaa he ficat la pota, perdona...

ves a un terminal, i posa:

gksudo network-admin

alla tindras la pestanya conexions. Igual alla hi ha alguna cosa interesant. 
No tens res mes relacionat amb la xarxa  a Sistema -> administracio ???

---

### Post by Fornols on 2007-03-21
JA HO HE FET, I SURT:
(network-admin:9858):GnomeUI-WARNING**: While connecting to session manager:
Authentication Rejected, reason:None of the authentication protocols specified are supported and host-based authentication failed.

s'ha obert una finestra que diu PARMETRES DE XARXA, pestanya "CONEXIONS", i diu:
CONEXIÓ MÒDEM: La interficie ppp0 no està configurada.

Com va això?

NOTA: Estaré conectat al foro fins a les 20:15h

---

### Post by patrickfromspain on 2007-03-21
hauras d'instalar el drivers... manualment

he trobat això: [http://www.ubuntu-es.org/node/15743](http://www.ubuntu-es.org/node/15743) espero que serveixi d'ajuda

---

### Post by Fornols on 2007-03-21
Moltes gràcies, demà a la tarda entre les 17:00h i les 19:00h aprox, estaré conectat a aquest foro, i provaré el que m'has dit.

---

### Post by CarlesOriol on 2007-03-22
Millor que et connectis a l'irc si vols una participació més directa.

[https://wiki.ubuntu.com/CatalanTeam/IRC](https://wiki.ubuntu.com/CatalanTeam/IRC)

---

### Post by Fornols on 2007-03-22
Hola companys,
Es veu que sóc una mica negat per l'UBUNTU (en windows em defenso millor)
He trobat el driver, però us explico:
El foro l'escric des d'un ordinador amb WINDOWS.
L'UBUNTU el tinc instal·lat en un altre ordinador al costat, però això vol dir que quan em baixo un driver ho faig en l'ordinador amb Windows, però després no sé com passar-lo a l'ordinador UBUNTU, ja que no conec les sentencies amb linux dins del terminal.
Ara tinc el driver en un diskette, però no sé com copiar-lo al disc dur del UBUNTU.

NOTA:
El IRC crec que és un canal de xat, però tampoc el tinc instal·lat.

---

### Post by Fornols on 2007-05-02
Hola,
Fa dies que intento instal·lar IRC però pel que veig, necessito el KOPETE, i aquest programa només funciona amb UTUNTU.
Com us deia, us escric des d'un ordinador amb Windows, ja que a l'altre ordinador que tinc, hi tinc instal·lat UBUNTU però no funciona INTERNET.
Hi ha alguna altra manera de seguir les vostres instruccions?
Cordialment.

---

### Post by CarlesOriol on 2007-05-02
Jo uso l'xchat. Crec que existeix per a windows.

[http://www.xchat.org](http://www.xchat.org)

---

### Post by CarlesOriol on 2007-05-02
Vaig veure que m'havies enviat un missatge a l'irc però vaig respondre tard! Sento haver fastidiat la primera experiencia.

A veure si demà ens podem parlar.

[I]20:47 <Fornols> Hola a tothom. Gracies CarlesOriol, com pots veure ja he instal·lat el XChat
20:50 <Fornols> Demà a la tarda miraré de conectar-me al IRC per veure si em podeu ajudar a conectar l'UBUNTU  a Internet. Fins demà
20:52 <carlesoriol> Bona nit Fornols![/I]

---


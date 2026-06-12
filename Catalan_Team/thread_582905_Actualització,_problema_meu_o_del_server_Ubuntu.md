---
title: "Actualització, problema meu o del server Ubuntu??"
date: 2007-10-20
forum: Catalan Team
---

### Post by prostata on 2007-10-20
Bon dia companys:

Cada cop que intento actual-litzar a 7.10 em fa fora desprès d'una estoneta amb el següent messatge:

Error durante la actualización

Ocurrió un problema durante la actualización. Normalmente es debido a algún tipo de problema en la red, por lo que le recomendamos que compruebe su conexión de red y vuelva a intentarlo.


Failed to fetch [http://hendrik.kaju.pri.ee/ubuntu/dists/feisty/all/binary-i386/Packages.gz](http://hendrik.kaju.pri.ee/ubuntu/dists/feisty/all/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://hendrik.kaju.pri.ee/ubuntu/dists/feisty/all/source/Sources.gz](http://hendrik.kaju.pri.ee/ubuntu/dists/feisty/all/source/Sources.gz) 404 Not Found

fa  dos dies que estic repetin l'actual-lització pero sempre em passa el mateix.

Soc usuari ONO, i no sé si el problema el tinc jo o potser els servidors Ubuntu estan massa carregats.

Gràcies

---

### Post by papapep on 2007-10-20
Hauries de posar repositoris oficials al /etc/apt/sources.list, així evitaràs problemes d'aquests indeterminats.
En tot cas, edita'l i esborra la línia o línies que t'indica que et porten problemes.

---

### Post by prostata on 2007-10-20
> **papapep said:**
> Hauries de posar repositoris oficials al /etc/apt/sources.list, així evitaràs problemes d'aquests indeterminats.
En tot cas, edita'l i esborra la línia o línies que t'indica que et porten problemes.

Gràcies:
Cóm és posen  repositoris oficials al /etc/apt/sources.list??

A la terminal em surten un munts de sources.list, mira:

josep@josep-desktop:/etc/apt$ ls
apt.conf.d                        sources.list_backup_200709252045
secring.gpg                       sources.list_backup_200709261120
sources.list                      sources.list.d
sources.list~                     sources.list.distUpgrade
sources.list_backup_200709241238  sources.list.save
sources.list_backup_200709241722  trustdb.gpg
sources.list_backup_200709241759  trusted.gpg
sources.list_backup_200709241930  trusted.gpg~
josep@josep-desktop:/etc/apt$ gedit
josep@josep-desktop:/etc/apt$ gedit sources.list
josep@josep-desktop:/etc/apt$ 

Que hi hagi tants és normal?

Quan faig gedit sources.list i esborro les lìnies de referència doncs resulta que no em permet desar, diu que es només de lectura, i quan vaig a l'arxiu a veure els permisos no em permet activar cap ni un??

Una mica extrany tot plegat, no? no entenc tants sources.list, no entenc que no en pugui atorgar permisos.. en fin estic una mica despistat...

em fas un cop de má més...gràcies

---

### Post by lluisanunez on 2007-10-20
Per editar /etc/apt/sources.list primer has de ser administrador. obre un terminal i entra

```
gksudo gedit /etc/apt/sources.list
```
(el teu password)

i ja podràs editar i desar.

---

### Post by papapep on 2007-10-20
Per exemple, pots fer servir això:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe

Si en algun moment et calen els universe, símplement esborrant el caràcter "#" que hi ha al davant, faràs el fet.

---

### Post by prostata on 2007-10-20
> **papapep said:**
> Per exemple, pots fer servir això:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe

Si en algun moment et calen els universe, símplement esborrant el caràcter "#" que hi ha al davant, faràs el fet.

Gràcies, ja els he possat en el sources.list; i hara una pregunta "¿rara"?, a veure, m'agrdadira saber per exemple què és i com funciona i perquè el sources.list, també el que son les dependències, quina diferecia hi ha entre obrir una terminal com a sudo i/o com en dei la lluisanunez en l'altre post:

"Per editar /etc/apt/sources.list primer has de ser administrador. obre un terminal i entra

Code:

gksudo gedit /etc/apt/sources.list 

és a dir, llegeigo un munt de terminologìa que em puc imàginar el que és però que no se ben bé quina es la seva "filosofia", la seva funcionalitat, ¿on podrìa llegir quelcom que expliqui aquests conceptes per a una persona que no ve del mon de Unix-linux?

Gràcies

---

### Post by prostata on 2007-10-20
El sistema em diu que hi han actualitzacions però al temp m'envia aquest messatge:

Ha ocurrido un problema imposible de corregir cuando se inicializaba la información de los paquetes.

Por favor, informe de ésto como un fallo en el paquete «update-manager» e incluya el siguiente mensaje de error:

'E:Dynamic MMap ran out of room, E:Dynamic MMap ran out of room, 
¿qué vol dir aixó?.... el mateix text és repeteix infinitat de vegades...:confused:

---

### Post by papapep on 2007-10-20
A aquest post antic es parla d'aquest missatge d'error:

[http://ubuntuforums.org/showthread.php?t=506719](http://ubuntuforums.org/showthread.php?t=506719)

---

### Post by lluisanunez on 2007-10-21
> **prostata said:**
> ...ara una pregunta "¿rara"?, a veure, m'agrdadira saber per exemple què és i com funciona i perquè el sources.list, també el que son les dependències, quina diferecia hi ha entre obrir una terminal com a sudo i/o com en dei la lluisanunez en l'altre post...


* sources.list és simplement això, la llista de repositoris que utilitza apt (i per tant synaptic, aptitude, etc) per a insta&#320;lar programes i actualitzacions. "deb" i  "deb-src" distingeixen els repos d'executables dels de codi font o "source"
* Les dependències són els programes o llibreries que es necessiten per a córrer un determinat programa. Apt obté aquesta informació del repositori, i es cuida d'insta&#320;lar tots aquests programes quan li encarregues la insta&#320;lació. Sense un gestor de dependències com apt, hauries de buscar i insta&#320;lar manualment els programes requerits.
* **sudo** és un prefix per a co&#320;locar davant d'una comanda del sistema, indicant que s'executi aquesta comanda amb drets de root o administrador. Però aquesta indicació és només referida a aquesta comanda en concret. Si haguessis d'executar moltes comandes seguides des d'un terminal, per no repetir sudo cada vegada et seria més útil obrir el terminal amb drets de root per a totes les comandes que enviis en aquesta sessió. Té menys seguretat, és clar.

---

### Post by prostata on 2007-10-22
> **lluisanunez said:**
> * sources.list és simplement això, la llista de repositoris que utilitza apt (i per tant synaptic, aptitude, etc) per a insta&#320;lar programes i actualitzacions. "deb" i  "deb-src" distingeixen els repos d'executables dels de codi font o "source"
* Les dependències són els programes o llibreries que es necessiten per a córrer un determinat programa. Apt obté aquesta informació del repositori, i es cuida d'insta&#320;lar tots aquests programes quan li encarregues la insta&#320;lació. Sense un gestor de dependències com apt, hauries de buscar i insta&#320;lar manualment els programes requerits.
* **sudo** és un prefix per a co&#320;locar davant d'una comanda del sistema, indicant que s'executi aquesta comanda amb drets de root o administrador. Però aquesta indicació és només referida a aquesta comanda en concret. Si haguessis d'executar moltes comandes seguides des d'un terminal, per no repetir sudo cada vegada et seria més útil obrir el terminal amb drets de root per a totes les comandes que enviis en aquesta sessió. Té menys seguretat, és clar.

Gràcies Lluisa: tot aixó ja ho sabia, es poca cosa o si més no es bastant deductible, el que voldría saber es una mica més sobre tot el conjunt, per exemple, de la resposta que em vas donar l'alre dia, ""Per editar /etc/apt/sources.list primer has de ser administrador. obre un terminal i entra

Code:

gksudo gedit /etc/apt/sources.list

 quina es la diferència entre sudo i el kgsudo i el perquè d'aquesta diferència. Saps que em passa, doncs que faig el que faig però sense enterarme molt del què i sobre tot del perquè, i voldría saber-lo. Per exemple amb windows-ms-dos, cap problema i m'agradaria assolir el mateix nivell de competencia i conexiement amb els dos sistemes.

Per aixó demano una recomanació sobre quina mena de lectura em podrìa convenir per aclarir aquests i d'altres conceptes
Gràcies

---

### Post by papapep on 2007-10-22
Això que demanes és el coneixement que t'ha de portar el temps de barallar-te amb el sistema. Pots començar llegint-te això:

[https://wiki.ubuntu.com/JosepS%c3%a0nchez/documentaci%c3%b3/interpret_comandes](https://wiki.ubuntu.com/JosepS%c3%a0nchez/documentaci%c3%b3/interpret_comandes)

PD No és tant obvi el que t'ha explicat la Lluïsa quan hi ha quantitat de gent que no ho sap ni entèn i pregunta al respecte.
PD2. L'MS-DOS i el terminal de gnu/Linux disten anys llum, o sigui que no et queda cosa ni res per aprendre (i a mi igual, no et pensis que només ets tu...)

---

### Post by lluisanunez on 2007-10-22
> **papapep said:**
> ...Pots començar llegint-te això:

[https://wiki.ubuntu.com/JosepS%c3%a0nchez/documentaci%c3%b3/interpret_comandes](https://wiki.ubuntu.com/JosepS%c3%a0nchez/documentaci%c3%b3/interpret_comandes)



Gràcies, Papapep, com que el tenies sempre a la signatura, no me l'havia apuntat enlloc i ara que no l'hi tens no el podia recomanar aquí al company prostata

**gksudo:** jo només sé que és la versió de **sudo** que cal utilitzar quan s'executen programes amb GUI (com Gedit)

---

### Post by papapep on 2007-10-22
Estic començant a preparar un document de PMF-Preguntes més freqüents, per intentar respondre aquests temes reiteratius.

Aquí 

[https://wiki.ubuntu.com/JosepS%c3%a0nchez/documentaci%c3%b3/PMF_UbuntuCat](https://wiki.ubuntu.com/JosepS%c3%a0nchez/documentaci%c3%b3/PMF_UbuntuCat)

estic posant les coses que veig o recordo que la gent pregunta un i altre cop.

Suposo que un cop el tingui més adelantat el passarem al wiki o plana web de l'equip.

PD S'accepten col·laboracions... ;-)
PD2 Vaaaaal, torno a posar la url del manual a la signatura :-D

---

### Post by lluisanunez on 2007-10-24
Quan el posis al wiki, encantada de co&#320;laborar en el que pugui

**editat:** Ahaaa si ja l'has posat! I ja hi he co&#320;laborat!   :-D

---


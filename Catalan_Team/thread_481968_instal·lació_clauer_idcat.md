---
title: "instal·lació clauer idcat"
date: 2007-06-23
forum: Catalan Team
---

### Post by bratac on 2007-06-23
Bones, 

tinc un certificat digital idcat, a través del seu web m'he baixat els connectors per a linux i les instruccions em diuen que he de fer el següent:

$ cd ClauerLinux-x.ydir

	$ ./configure

Un cop fet el ./configure em diu:

configure: WARNING: We can't links against the ssl library
configure: error: Perhaps you need to use the --with-ssl-libraries directive

jo ho he compilat des de l'escriptori, potser ho havia de fer des del llàpis usb que em van donar.

Després d'això em diu que he de fer el make, però no sé si fer-lo o no...

Algú em pot ajuda?

---

### Post by RainCT on 2007-06-23
Prova fent això abans:

```
sudo apt-get install libssl libssl-dev
```

---

### Post by bratac on 2007-07-02
Bones,

després de fer el sudo  que m'heu proposat, la terminal m'ha donat aquest missatge:

El paquet libssl no té versió disponible, però un altre paquet
en fa referència. Això normalment vol dir que el paquet falta,
s'ha tornat obsolet o només és disponible des d'una altra font.
E: El paquet libssl no té candidat d'instal·lació

Conseqüentment no puc continuar la instal·lació. Em podeu ajudar de nou?

Gràcies, 

bratac

---

### Post by bratac on 2007-07-02
he fet el ./ i sí, em dóna el següent error:

configure: WARNING: We can't links against the ssl library
configure: error: Perhaps you need to use the --with-ssl-libraries directive


com puc instal·lar el ssl-libraries directive?

gràcies, 

bratac

---

### Post by bratac on 2007-07-10
He trobat una solució i m'ha sortit algun problema.

La solució al problema anterior rau en instal·lar:

sudo apt-get install libnss-dev libssl-dev

després puc fer el

make
i el

sudo make install

ara em diu que el primer cop que instal·li el llapis he de fer:

\# /etc/init.d/clos start

algú em pot traduir això tipus primer a terminal escriu ..... després s'ha de posar.... i aixi fins al final?

gràcies

Bratac

---

### Post by orestesmas on 2007-07-13
No veig el problema. Nome&#347; està dient que executis com a root el programa "clos" situat al directori /etc/init.d/ i que li passis el paràmetre "start". Això es fa exactament amb la línia que et diu (posant "sudo" al davant si no ets root):

sudo /etc/init.d/clos start

Això el que fa és iniciar un programa resident en memòria (clos) que suposo que és el que s'encarrega de gestionar el clauer idCAT quan s'insereix...

---

### Post by Komionu on 2007-11-22
Doncs a mi em posa a la terminal que el programa ja va:
root@jaume-laptop:~#  /etc/init.d/clos start
Starting clos ...
clos is already running, try doing clos restart
root@jaume-laptop:~# 

Pero jo el pugrama no el veig enlloc.

I no em deixa fer servir el certificat digital.

A vosaltres us va ?

Vinga salut,

PS : aixo del linux es molt complicat...

---

### Post by CarlesOriol on 2007-11-23
GENIAL !!

try doing clos restart ... a veure si funciona :-)

:-D  :-D  :-D :-D  :-D

---

### Post by calbasi on 2007-12-31
> **bratac said:**
> He trobat una solució i m'ha sortit algun problema.

La solució al problema anterior rau en instal·lar:

sudo apt-get install libnss-dev libssl-dev

després puc fer el

make
i el

sudo make install

ara em diu que el primer cop que instal·li el llapis he de fer:

\# /etc/init.d/clos start

algú em pot traduir això tipus primer a terminal escriu ..... després s'ha de posar.... i aixi fins al final?

gràcies

Bratac

Em sembla que amb el paquet libssl-dev n'hi ha prou (com a mínim en el meu cas, ubuntu 7.10). L'altre paquet que dius, el libnss.dev, entra en conflicte amb una llibreria del calendari de l'Evolution.

Salut,

calbasi

---

### Post by pserra on 2010-06-08
Estic amb el mateix problema que el company...
però seguint els seus passos no em funciona:

faig el configure: darreres linies:
```
hecking for pthread_create in -lpthread... yes
checking for RSA_sign in -lcrypto... no
configure: WARNING: We can't links against the ssl library
configure: error: Perhaps you need to use the --with-ssl-libraries directive

```
faig la instalació del company:
```
pere@pere-laptop:/tmp/ClauerLinux-3.0.4$ sudo apt-get install libnss-dev libssl-dev
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
E: No s'ha pogut trobar el paquet libnss-dev
```
i faig el seguent pas que es el make:
```
pere@pere-laptop:/tmp/ClauerLinux-3.0.4$ make
make: *** No targets specified and no makefile found.  Stop.
pere@pere-laptop:/tmp/ClauerLinux-3.0.4$ 

```
que em falla??

Merci

---

### Post by papapep on 2010-06-08
Pserra,

Has ressucitat un fil de fa 3 anys. N'hauries d'obrir un de nou, ja que el problema i la solució poden ser la nit i el dia respecte el fil original.

---

### Post by xomix on 2010-06-19
Hola pserra,

jo acabo d'instal·lar-ho a una Lucid per a netbooks.
Crec que les biblioteques que necessites són les contingudes en els paquets següents:

libssl-dev - SSL development libraries, header files and documentation
libssl0.9.8 - SSL shared libraries

així: 
sudo apt-get install libssl-dev libssl0.9.8

Un cop instal·lades, repeteix el ./configure
Si aquest finalitza sense errors, executa make. Sino, envia els errors del configure.
Finalment, com a root, cal executar l'instal·lació: sudo make install

Després cal instal·lar el dispositiu de seguretat al firefox. A mi m'ha fallat amb l'script firefox-install-pkcs11.sh i ho he fet manualment.

Bona sort!
Jaume

---

### Post by akyra on 2010-06-20
Jo hem vaig fer dos scripts per instal·lar idcat. Us els puju per si us pot ajudar.
És important si algú els vol executar de fer abans "sudo su".
Jo ho vaig fer la versió 3.0, mire-ho si ha canviat la versió del clos. Dins de l'script "idcat.sh" s'ha de canviar el directori a on teniu guardat el clos, en el meu cas "/home/jordi/Documents/..." pel vostre
Espero que a algú li serveixi.

Salutacions

---


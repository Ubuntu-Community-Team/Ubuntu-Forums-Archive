---
title: "Problemes diversos"
date: 2007-09-24
forum: Catalan Team
---

### Post by venusfenix on 2007-09-24
Hola a tots;

aqui, un rookie del ubuntu, amb dos problemas, i que no tinc n'idea per on començar!

El primer i mes simple es sobre el driver de pantalla.
de manera automatica, el Ubuntu va triar tots els drivers, pero, després de traballar varies setmanes, hi han colors i textures que van cambian. Pero la veritat es que no se com cambiar el driver de la VGA, així com, on trobar el que li correspongui.


El segon problema, crec jo, mes complexe, desde fa uns tres dies que Ubuntu em diu que hi han actualitzacions, pero no hi ha manera que ho faci, no em demana la clau root, i surt el cursor de "ongoing" pero es queda hores i sense fer res. Per altra banda, varies aplicacions del menu sistema, no funcionen. que puc fer??


moltes merces!!

---

### Post by papapep on 2007-09-24
Hola Venusfenix,

El primer que caldria és que ens donessis més informació, sinó estem cecs.
Quina gràfica tens? Amb quin driver estàs treballant?

Respecte les actualitzacions, posa a un terminal:

```
sudo aptitude update
```

i un cop fet això, si funciona correctament, fes:

```
sudo aptitude upgrade
```

En qualsevol cas, si et dóna errors enganxa la resposta del terminal aquí i mirarem què s'hi pot fer.

Salutacions.

---

### Post by venusfenix on 2007-09-24
Hola,

moltes merces per respondre.
Respecte a la VGA, es una S3 prosavage.

respecte al tema de actualitzacions, em respon de la següent manera:
jose@Jupiter:~$ sudo aptitude update
sudo: unable to lookup Jupiter via gethostbyname()
jose is not in the sudoers file.  This incident will be reported.
jose@Jupiter:~$ 


???
que puc fer?

---

### Post by papapep on 2007-09-24
Tens la xarxa ben configurada??? Estas escrivint des d'el mateix ordinador que tens problemes?
L'usuari que fas servir, és el que vas crear al fer la instal·lació? o l'has creat tu posteriorment?

Del tema targeta gràfica, a quina ressolució la tens configurada? Prova amb diferents a veure quin resultat et dóna.

---

### Post by venusfenix on 2007-09-24
tot esta igual que quan faig instal.lar l'Ubuntu, menys el tema de la contrasenya root que la vaig cambiar, pero em vaig adonar que no havia surtit efecte.
la xarxa funciona, puc accedir a l'internet aixi com tambe amb un altre ordinador (windows), correu, etc...

l'aplicacio per cambiar la contrasenya, ara per ara, no funciona, i porto tot el mati amb el gestor d'actualitzacions i res, continua sense fer res.

ara per ara, el tema es arreglar aquest tema, l'altre problema es secundari.

moltes merces!!

---

### Post by papapep on 2007-09-24
Fes un cop d'ull al fitxer /etc/hosts:
(primer fes-ne una còpia):

```
cp /etc/hosts /etc/hosts.original
```

Ara edita el fitxer:

```
sudo nano /etc/hosts
```

i busca que hi surti:

```
127.0.0.1 localhost
```

Si no hi és, ho has de ficar.

Si hi veus això:

```
order hosts,bind
multi on

```

esborra-ho.

A veure què tal així.

---

### Post by venusfenix on 2007-09-26
Perdona, pero no m'he pogut posar davant de l'ordinador fins avui.

he fet l'ultim que m'indicas, i fracas total:

jose@Jupiter:~$ sudo aptitude update
sudo: unable to lookup Jupiter via gethostbyname()
jose is not in the sudoers file.  This incident will be reported.
jose@Jupiter:~$ sudo aptitude update
sudo: unable to lookup Jupiter via gethostbyname()
jose is not in the sudoers file.  This incident will be reported.
jose@Jupiter:~$ cp /etc/hosts /etc/hosts.original
cp: no s'ha pogut crear el fitxer ordinari «/etc/hosts.original»: Permission denied
jose@Jupiter:~$ sudo nano /etc/hosts
sudo: unable to lookup Jupiter via gethostbyname()
jose is not in the sudoers file.  This incident will be reported.

other options??
merces!!

---

### Post by Ferri on 2007-09-26
Segur que no tens cap altre usuari? Trobo molt estrany que un usuari desaparegui de la llista dels sudoers "espontàniament".
Dius que vas canviar la contrasenya de root. A Ubuntu no hi ha superusuari (root) en una instal·lació normal i per fer la feina del superusuari es fa servir el comandament "sudo". És possible, però, activar el superusuari i potser és això el que vas fer. Intenta fer això:```
su
```i després introdueix la contrasenya (probablement la que dius que no et va canviar). Si et funciona, pots fer tot el que t'han dit, sense posar "sudo" al davant.
Si fos així, ja parlarem més endavant de com tornar a afegir el teu usuari a la llista dels "sudoers" (que són els usuaris que tenen dret a fer servir el comandament sudo, per defecte el primer usuari sempre hi és).

---

### Post by jaume69 on 2007-09-26
Hola,sóc nou i bé,espero estar algunes estones per aquí,si puc.:confused:

No sé si ho has provat però....,podries anar a Sistema,Administ.,Usuar.Grups,i allà vas a **root**,Propietats,i si no recordes la contrasenya li dius que en generi una.La recordes i entres al terminal amb la mateixa.

Pregunta:No hi ha cap manera de recordar la contrasenya perduda?,o regenerar-la de manera més còmoda?.
O tornar posar una contrasenya seleccionada per a tú i no el root.
Gràcies.

---

### Post by Ferri on 2007-09-27
> **jaume69 said:**
> Pregunta:No hi ha cap manera de recordar la contrasenya perduda?,o regenerar-la de manera més còmoda?.
O tornar posar una contrasenya seleccionada per a tú i no el root.
Gràcies.

Per fer això el sistema que conec és iniciar en "recovery mode" i posar:
```
passwd elteuusuari
```
Et demanarà dos cops la contrasenya i la podràs canviar.
Per motius de seguretat, no hi ha manera, que jo sàpiga, que puguis esbrinar una contrasenya oblidada.

---

### Post by venusfenix on 2007-09-27
buenas,

totes aquestes opcions, estam mes que probades, qualsevol aplicacio de sistema, no funciona, en altres paraule no s'executa.
qualsevol opcio del menu sistema, no funciona, pero tampoc aplicacions-altres, com per exemple, el terminal root.
i encara que el terminal si que funciona, en rebutja qualsevol ordre o en  diu que no tinc drets de root, o em demana el password, i ja heu vist el resultat.

encara soc un rockie amb aixo del linux, i com vinc de Windows, al final he decidit (com que la maquina de moment es per "trastejar") doncs, aixo, un "borrar, y empezar de nuevo".

malgrat tot, moltes gracias a tots, he apres coses noves, i n'he pagat les novatates!!!

merci!

---


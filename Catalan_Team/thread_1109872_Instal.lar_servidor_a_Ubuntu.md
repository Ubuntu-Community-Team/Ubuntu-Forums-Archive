---
title: "Instal.lar servidor a Ubuntu"
date: 2009-03-29
forum: Catalan Team
---

### Post by jaume69 on 2009-03-29
Hola,algú sap com instal.lar a **Ubuntu Intrepid** un servidor,suposo primer local,o al hosting,per a fer rutllar alguna web.

[COLOR="Navy"]O si hi ha algun **tutorial** que sigui compressible per a usuaris novells,per instal.lar **PHP,Apache,MySQL**,**a Ubuntu**[/COLOR]

Jo ho vaig provar fa temps i em donava errors a **phpmyadmin**,ara no recordo exactament..
**Apache** si que anava bé,si posava **localhost** a la barra de direccions em sortia la carpeta de sistema que hi tenia,Wordpress.

Vaig provar a instal.lar **XAMPP** per Linux,i tampoc em va rutllar bé.

Gracies!!.

---

### Post by papapep on 2009-03-29
[https://help.ubuntu.com/8.10/serverguide/C/index.html]("https://help.ubuntu.com/8.10/serverguide/C/index.html")

i a qualsevol buscador, per poc que busquis, podràs trobar autèntiques muntanyes de informació al respecte, per a tots els nivells, i en tots els idiomes, segur.

---

### Post by marteljorge on 2009-03-29
> **jaume69 said:**
> Hola,algú sap com instal.lar a **Ubuntu Intrepid** un servidor,suposo primer local,o al hosting,per a fer rutllar alguna web.

[COLOR="Navy"]O si hi ha algun **tutorial** que sigui compressible per a usuaris novells,per instal.lar **PHP,Apache,MySQL**,**a Ubuntu**[/COLOR]

Jo ho vaig provar fa temps i em donava errors a **phpmyadmin**,ara no recordo exactament..
**Apache** si que anava bé,si posava **localhost** a la barra de direccions em sortia la carpeta de sistema que hi tenia,Wordpress.

Vaig provar a instal.lar **XAMPP** per Linux,i tampoc em va rutllar bé.

Gracies!!.

Doncs jo cuasi no tinc problemes amb Apache.
[http://marteljorge.no-ip.org](http://marteljorge.no-ip.org)

---

### Post by marteljorge on 2009-03-29
```
sudo apt-get install apache php5 mysql
```

---

### Post by kukat on 2009-04-01
També pots insta&#320;lar-ho anant a "Sistema", "Administració", "Gestor de Paquets Synaptic". I després "Edita", "Marca els paquets per Tasques" i marques el de "LAMP Server" que és el que vols:D (Linux, Apache Mysql i Php o LAMP)

Salut!

---

### Post by jaume69 on 2009-04-05
Ara no estic a Ubuntu,però recordo que em va donar problemes el **PHP**,no sé si era la versió PHP5.
Tota manera al final funcionava en **localhost**.
A més jo estic en un hosting **Windows**.
Gràcies per les respostes.

P.D.És molt car tenir un servidor propi o dedicat,o val la pena?,suposo que els de **Windows** son més cars,tan si és compartit com dedicat,ep..,no sé..

---

### Post by totalkiller on 2009-05-02
Tenir un servidor propi és molt fàcil, i animo a la gent que s'hi interessi a provar-ho, jo vaig començar a provar i a investigar i en setmanes tenia un portatil que servia una pàgina web, es instal·lar l'apache, el php5 i el mysql, fer que s'entenguin, redirigir el port 80 del router cap a la teva ip i voilà, l'únic problema que tindreu, es que per veure la vostra pàgina escribint la vostra IP pública al navegador, ho haureu de fer desde fora de la vostra red local, o us semblarà que no ha funcionat com em va passar a mi.

P.D: Si vols fer servir el teu PC de servidor, et recomano linux, quan jo el tenia amb windows també anava bé, però amb el temps et veuràs limitat

---


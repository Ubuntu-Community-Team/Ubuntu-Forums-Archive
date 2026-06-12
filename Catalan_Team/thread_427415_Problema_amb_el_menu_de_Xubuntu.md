---
title: "Problema amb el menu de Xubuntu"
date: 2007-04-29
forum: Catalan Team
---

### Post by albert-I on 2007-04-29
Em presento i ja demano solucions :) 
Em dic Albert Teixidor i amb el 7.04 m'he passat completament a Xubuntu,:popcorn: 

Abans tenia el kubuntu i m'havia instal·lat l'escriptori de Xfce per motius de potencia del meu pc.
Fins al dia que vaig decidir treure el KDE (que trobo a faltar) no habia tingut mes que els problemes normals i més o menys fàcils de resoldre. Pero ara que sols tinc les llibreries del Xfce pq he fet una reinstal·lació total i em trobo que el menú es esquifit i sols hi tinc el navegador, el thunar i el terminal. 

Que haig de fer per tenir una altre vegada tots els programes amb les seves divisions de jocs, oficina? 
Haig de anar muntant un per un cada divisió i posar-hi els programes?
No hi ha una manera senzilla de tindre un menú arregladet que ja surt al LiveCD?????????

Gràcies per tot

Albert

---

### Post by CarlesOriol on 2007-04-29
sudo apt-get install kubuntu-desktop.


Però si as curt de recursos pot ser és millor un escriptori gnome en comptes de kde.

---

### Post by albert-I on 2007-04-30
Be, gràcies per la contesta, no era això el que m'esperava o potser m'he explicat malament.

Amb això aconsegueixo l'escriptori de KDE i el que vull es l'[COLOR="Magenta"]aplicatión Menu[/COLOR] que ja m'estic fent a estones però entenc que hi ha d'haver un sistema senzill per tenir el menú.

[IMG]http://hewphoria.com/themes/icons/836732/blankon-for-xfce.png[/IMG]
[IMG]http://www.freesbie.org/share/1.1/manual/xfce.png[/IMG]

---

### Post by CarlesOriol on 2007-05-01
A la llista de correu de l'equip català em sembla que hi ha més d'un apassionat del xfce. 

Posa la consulta allà a veure si ho saben. 

 [https://lists.lafarga.cpl.upc.edu/mailman/listinfo/ubuntucat-info](https://lists.lafarga.cpl.upc.edu/mailman/listinfo/ubuntucat-info)

---

### Post by PellRoja on 2007-05-01
és un problema bastant comu en l' escrpitori xfce 4

[http://www.ubuntu-es.org/index.php?q=node/18473](http://www.ubuntu-es.org/index.php?q=node/18473)

[http://www.nicoman.com.ar/blog/2007/02/28/problema-con-el-menu-de-xfce/](http://www.nicoman.com.ar/blog/2007/02/28/problema-con-el-menu-de-xfce/)

---

### Post by albert-I on 2007-05-03
Doncs ja està arreglat, el que passa per mirar els forum anglesos i no els castellans :DD mira que es facil a vegades. 

Sols he copiat el fitxer del menu al seu lloc i ja funciona: :)

cp /etc/xdg/xfce4/desktop/menu.xml .config/xfce4/desktop/menu.xml

Gracies a tothom.

Albert

---

### Post by Alber_Maresmenc on 2007-06-06
Merci Albert, jo tenia el mateix problema.
Per cert, a tu et funciona l'Amarok? Jo el tenia instal·lat a l'Ubuntu amb gnome abans de passar-me al Xubuntu i no anava, pero encara no l'he pogut instalar al Xubuntu. Digues-me alguna cosa!

Apa siau!

---

### Post by papapep on 2007-06-06
Alber_Maresmenc: si vols consultar una altra cosa hauries d'obrir un fil nou. Sinó ho fem així, si algú busca el mateix problema que estàs plantejant no el trobarà, ja que estarà sota un títol que no hi correspon.

Salutacions.

---


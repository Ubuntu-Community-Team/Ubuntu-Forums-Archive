---
title: "No funciona Bluetooth a Jaunty"
date: 2009-05-14
forum: Catalan Team
---

### Post by iSoc on 2009-05-14
Hola, bones algú sap com s' instal·la omnibook per fer anar el bluetooth d´un thosiba satelite u-400 ? crec que es un modul de bluetooth que fan servir alguns portàtils thosiba també dir-vos que am intrepid funcionava perfecte però amb Jaunty no funciona. un salut.;)

---

### Post by SiscoGarcia on 2009-05-14
Sembla que St. Gooble té [alguna idea]("http://www.google.es/search?hl=ca&client=firefox-a&rls=com.ubuntu%3Aca%3Aunofficial&hs=yEL&q=omnibook+jaunty&as_q=toshiba&btnG=Cerca+dins+dels+resultats"), la [tercera opció]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/45021") parla d'un possible bug (però fa referència a un nucli vell, el 2.6.22). No sé, remena a veure què.

---

### Post by iSoc on 2009-05-14
Gracies SiscuGarcia, ja ho e llegit abans però no entrec l´aigua clara. I no e torbat res mes, no se ni si funciona omnibook amb Jaunty, Gracies per respondre tornare a enredar a veure que puc fer. Un salut.

---

### Post by iSoc on 2009-05-15
Bona nit després de esta buscant i buscant al final e trobat la solució d'activar el bluetooth a jaunty i va perfecte aquí os deix-ho l'enllaç per si algú li fa falta. Un salut.

[http://docs.google.com/View?docid=dgd53r6d_36hqmmh4hn](http://docs.google.com/View?docid=dgd53r6d_36hqmmh4hn)

---

### Post by CarlesOriol on 2009-05-16
Ara instal.leu-vos el blueman i comenceu a flipar i plorar d'alegria. (cal reiniciar un cop instal.lat encara que no ho digui)

[http://blueman.tuxfamily.org/](http://blueman.tuxfamily.org/)

[https://launchpad.net/blueman/](https://launchpad.net/blueman/)

---

### Post by iSoc on 2009-05-16
Gracies Carles tinc que provar-lo a veure que tal. Llàstima que utilitzo el wicd i no es compatible....

---

### Post by PatrickVogeli on 2009-05-16
a jaunty fas servir el wicd? Per primera vegada trobo que el network manager funciona millor que el wicd..

---

### Post by iSoc on 2009-05-16
Bueno jo vaig tindre problemes amb el wifi, no m'agafaba be la senyal al menjador i amb el wicd tinc mes senyal no se per que sera , estic acostumat a wicd de totes maneres m'agradaria probar el network manager. I el blueman. Un salut.

---

### Post by Albert Que on 2009-05-16
Tinc un toshiba satellite A200-1AG amb BIOS phoenix i la ubuntu 9.04. En ubuntu no funciona el bluetooth (ni la 9.04 ni cap de les anteriors, amb el WVista que portava de nou si que funcionava).

Vaig aplicar la solució que es dóna aquí [http://docs.google.com/View?docid=dgd53r6d_36hqmmh4hn](http://docs.google.com/View?docid=dgd53r6d_36hqmmh4hn) i només va funcionar fins que vaig apagar l'ordinador. Repetir el procés no resulta, només va anar un cop.

He buscat per tot arreu i només trobo la solució anterior i altres que no resulten. Alguna idea?

---

### Post by CarlesOriol on 2009-05-17
> **iSoc said:**
>  Y el bluemon. Un salut.

I el bluemAn.

---

### Post by iSoc on 2009-05-17
> **Albert Que said:**
> Tinc un toshiba satellite A200-1AG amb BIOS phoenix i la ubuntu 9.04. En ubuntu no funciona el bluetooth (ni la 9.04 ni cap de les anteriors, amb el WVista que portava de nou si que funcionava).

Vaig aplicar la solució que es dóna aquí [http://docs.google.com/View?docid=dgd53r6d_36hqmmh4hn](http://docs.google.com/View?docid=dgd53r6d_36hqmmh4hn) i només va funcionar fins que vaig apagar l'ordinador. Repetir el procés no resulta, només va anar un cop.

He buscat per tot arreu i només trobo la solució anterior i altres que no resulten. Alguna idea?


Hola de nou, a mi em funciona perfectament. Crec que serà per culpa del ectype ja que cada model de thosiba fa servir diferents no se si el teu es diferent al U-400. Te prova això.

Aquí en ves de posar.

[B]Changes Feb 2009  omnibook module of version svn20090227-1
[/B]

 *** note *** a new version of the omnibook module was released at the end of Feb 2009 (for Debian users)
 and now it is necessary to add bluetooth=1
 so step 4 above becomes:

  

 [FONT=Courier New]```
options omnibook ectype=14 userset=0 lcd=0 display=0 blank=0 battery=0 ac=0 bluetooth=1
```[/FONT]
  

 5) you don't need to reboot. You can do this
 ```
sudo modprobe omnibook ectype=14
```Poses. Aixo.

```
options omnibook ectype=12 userset=0 lcd=0 display=0 blank=0 battery=0 ac=0 bluetooth=1
``````
sudo modprobe omnibook ectype=12
```Si no funciona poses 14,13,11,10 a veure quin es el teu. Tenia localitzada una llista dels models amb els seus corresponents ectype pero no la trobo....;)

Un salut a veure si et funciona

P.D. També et volia comentar ja que tens un thosiba similar al meu. Si tens multi-lector de targetes i et llegeix les Memory Sticks (mmc). de sony.

---

### Post by Albert Que on 2009-05-18
iSoc: no ho sé, no m'ha funcionat mai el lector de targetes, però em pensava que era perquè de nou en nou l'hi vaig posar una targeta petita sense adaptador i la vaig haver de treure en plan McGyver. Ja ho investigaré.

---


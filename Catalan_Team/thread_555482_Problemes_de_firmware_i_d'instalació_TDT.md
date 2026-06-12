---
title: "Problemes de firmware i d'instalació TDT"
date: 2007-09-20
forum: Catalan Team
---

### Post by cesvi87 on 2007-09-20
Bones companys!

Per primer cop escric i és que em vaig comprar un adaptador USB de TDT ( Hauppauge WinTV nova) resulta que he estat mirant forums, i m'enllaçen tots cap aquí [http://thadathil.net:8000/dvb/fw/dvb-usb/dvb-usb-dib0700-01.fw](http://thadathil.net:8000/dvb/fw/dvb-usb/dvb-usb-dib0700-01.fw)  per a que em baixi el firmware, però la pàgina no tira... he entrat a linuxtv.org però no m'hi aclaro massa. 
Algú em podria ajudar a trobar algun altre lloc on pogués disposar d'aquest firmware?

Estic seguint aquest tutorial, i la veritat vaig seguint els passos que hi diu tot i no saber massa de que tracta... :(  --> [http://www.mod-pc.com/modules.php?name=Forums&file=viewtopic&t=16609](http://www.mod-pc.com/modules.php?name=Forums&file=viewtopic&t=16609)

Aviam si m'ajudeu companys!

Salut!

EDITO: Em sembla que el firmware ja l'he trobat i l'he pogut descarregar, però tot i dir-li al terminal que sóc sempre el master i per tant no em demani sudo, no puc enganxar  l'arxiu del firmware a la carpeta /lib/fw .... que faig?

---

### Post by papapep on 2007-09-20
> EDITO: Em sembla que el firmware ja l'he trobat i l'he pogut descarregar, però tot i dir-li al terminal que sóc sempre el master i per tant no em demani sudo, no puc enganxar l'arxiu del firmware a la carpeta /lib/fw .... que faig?

Si no ens expliques exactament què has fet i què t'ha contestat el terminal és complicat aconsellar-te correctament. Difícilment si poses sudo o ets root no et deixarà fer el que vulguis. Una altra cosa és que et doni errors que tu no entens.
En conclusió, que ens enganxis què intentes fer i quin error o missatge et dóna el terminal :-)

---

### Post by cesvi87 on 2007-09-20
M'he descarregat el firmware.
El tinc ficat a l'escriptori.
I ara vull copiar l' arxiu.fw a la carpeta  /lib/firmware ho intento fer des de gnome amb copiar-pegar però no em deix, quin comandament he de fer per copiar l'arxiu a la carpeta que vull?


ps: poc a poc, però me'n sortiré amb la tdt :)

Gràcies company


EDITO: mirant posts he entrat al que vas crear de comandaments, resulta doncs que em diu: 

cp fitxer1 dir1   (Copia el contingut de fitxer1 (en un fitxer anomenat fitxer1) dins del directori dir1)

el fitxer és:  dvb-usb-dib0700-03-pre1.fw

el directori és:  root@cesvi87-laptop:/lib/firmware# 

COM HO ESCRIC?

---

### Post by papapep on 2007-09-20
Doncs obres un terminal i fas:

```
sudo cp /home/elteuusuari/Desktop/elnomdelfitxerdelfirmware /lib/firmware
```

Això et copiarà el fitxer allà on vols. Quan et demani la contrassenya, fica la del teu usuari normal.

---

### Post by cesvi87 on 2007-09-20
> **papapep said:**
> Doncs obres un terminal i fas:

```
sudo cp /home/elteuusuari/Desktop/elnomdelfitxerdelfirmware /lib/firmware
```

Això et copiarà el fitxer allà on vols. Quan et demani la contrassenya, fica la del teu usuari normal.

root@cesvi87-laptop:/# sudo cp /home/cesvi87/Desktop/dvb-usb-dib0700-03-pre1.fw» /lib/firmware
cp: ha fallat stat() sobre «/home/cesvi87/Desktop/dvb-usb-dib0700-03-pre1.fw\»»: No such file or directory


Juuu... papapep ja podria deixar apretar el botó dret  enganxar, i deixar copiar de forma visual ¬¬

---

### Post by papapep on 2007-09-20
> root@cesvi87-laptop:/# sudo cp /home/cesvi87/Desktop/dvb-usb-dib0700-03-pre1.fw**[COLOR="Red"]»[/COLOR]** /lib/firmware
cp: ha fallat stat() sobre «/home/cesvi87/Desktop/dvb-usb-dib0700-03-pre1.fw\»»: No such file or directory


El caràcter que t'he marcat en negreta i vermell sobra. Al meu missatge anterior juraria que no hi és... :-D

Per cert, jo que tu no treballaria com a root. I menys amb la poca experiència que tens. Ho pots destrossar tot sense voler.

---

### Post by cesvi87 on 2007-09-20
> **papapep said:**
> El caràcter que t'he marcat en negreta i vermell sobra. Al meu missatge anterior juraria que no hi és... :-D

Per cert, jo que tu no treballaria com a root. I menys amb la poca experiència que tens. Ho pots destrossar tot sense voler.

Vaja treballo com a root per no haver de teclejar tota l'estona el sudo i al password, i és que tinc l'Ubuntu instalat al portatil, i no passa res si se'm esborren coses, ja que per això l'utilitzo per iniciar-me amb Linux.

Sobre el tema. Ara ja he pogut copiar el fitxer.fw a la carpeta del firmware i segons el tutorial em diu que escrigui: make config. Abans ja ho he ficat i  m'ha començat a mirar moltes coses, però ara no sé perquè em surt aquest missatge:

root@cesvi87-laptop:~# make config
make: *** No rule to make target `config'. Stop.


Com és això?

---

### Post by papapep on 2007-09-20
> Sobre el tema. Ara ja he pogut copiar el fitxer.fw a la carpeta del firmware i segons el tutorial em diu que escrigui: make config. Abans ja ho he ficat i m'ha començat a mirar moltes coses, però ara no sé perquè em surt aquest missatge:

root@cesvi87-laptop:~# make config
make: *** No rule to make target `config'. Stop


M'hi jugo un pèsol a que no executes el "make config" al directori on tens el controlador que estàs intentant compilar.

---

### Post by cesvi87 on 2007-09-20
> **papapep said:**
> M'hi jugo un pèsol a que no executes el "make config" al directori on tens el controlador que estàs intentant compilar.

Bé doncs ara ja està solucionat tot el tema, per fi ho he sapigut fer... això sí , i el més important obro kaffeine, fico l'anteneta de la tdt-usb a prop de la finestra, fico buscar canals... i res de res... no rep senyal.

Que creieu que puc fer per tenir una bona senyal? Me faig una antena casolana? I a algú que tingui tdt per pc?

Salut!

---

### Post by papapep on 2007-09-21
Això ja són figues d'un altre paner.
Estàs segur que es reben canals on ets? Jo personalment tinc un dispositiu dvbt usb i rebo amb prou qualitat uns quants canals, però a cada cantonada varia això.

Apart, si no tinc connectat el dispositiu **abans** d'engegar el Kaffeine, no em funciona correctament el tema.

---

### Post by ilku on 2007-09-21
Hola company:
Mira't aquest wik [http://bitacoles.enging.com/doku.php?id=dvb:start]("http://bitacoles.enging.com/doku.php?id=dvb:start")i, es una mica antic, però els responsables estem aquí per poder-te ajudar, en el cas d'aquest article és el Carles Oriol.

Una salutació i sort

---

### Post by CarlesOriol on 2007-09-21
Quin embolic... he trigat 3 minuts en entendre això dels "responsables" Ili. Vols dir els "responsables" de l'article!

Puff..

Per cert... els que sempre esteu "missing" passeu pel : [https://wiki.ubuntu.com/CatalanTeam/GrescaGutsy](https://wiki.ubuntu.com/CatalanTeam/GrescaGutsy) i comenceu a  reservar el dia 20 d'octubre per la festa.

---

### Post by cesvi87 on 2007-09-24
Vaja a mi em sembla que el problema és de l'antena que ve junt amb el pack de l'usb-tdt.

Ja que vaig conectar l'usb amb l'antena colectiva i al cercar, vaig trobar alguns canals la majoria de TVC i TVE.

Això sí al anar a ficar el ''play'' me van sortir diferents errors:


14:55:22: xine: couldn't find demux for >/home/cesvi87/.kaxtv.ts<
14:55:22: xine: found input plugin : file input plugin
14:55:22: video_decoder: no plugin available to handle 'XviD'
14:55:22: xine: found demuxer plugin: AVI/RIFF demux plugin
14:55:22: xine: found input plugin : file input plugi


que vaja suposo que diuen que me de baixar certs códecs, que ara buscaré aviam com ho puc fer per baixar-me'ls.

I per cert aviam si algú te algun enllaç a poder ser en català on es parli de com ficar nous repositoris.

Gràcies

---

### Post by CarlesOriol on 2007-09-24
Anem per passos:

Prova d'usar el kaffeine de kde per veure si et localitza els canals correctament.

Sobre el tema:

> **cesvi87 said:**
> 
I per cert aviam si algú te algun enllaç a poder ser en català on es parli de com ficar nous repositoris.
Gràcies

No et calen més repositoris dels que ja tens. El fet d'insta&#320;lar altres origens als mantinguts per la comunitat d'ubuntaires sols et portarà problemes.

---

### Post by papapep on 2007-09-24
> a que vaig conectar l'usb amb l'antena colectiva i al cercar, vaig trobar alguns canals la majoria de TVC i TVE.

Doncs aleshores sembla clar que el problema el tens en el senyal que t'arriba a casa teva que no és prou fort com per que la petita antena del usb t'ho capti.

Respecte el suposat error de còdecs, quin programa te'l dóna i en quin moment? Arribes a veure la televisió o no?

> I per cert aviam si algú te algun enllaç a poder ser en català on es parli de com ficar nous repositoris.

Nous repositoris?? Per substituir els actuals que no et van bé? O per afegir-hi alguna cosa en concret?? Tingues present que seria bo que obrissis un fil nou per un nou tema ;-)

---

### Post by cesvi87 on 2007-09-24
Jo cerco canals, grabo l'ona de freqüència li fico al ''play'' al KAFFEINE  i just en el moment que en teoria hauria de veure la tele, me dona error  per culpa del xine.... 

I he buscat coses per google per treure'm l'error aquest.... i res de res... nosé que diu dels còdecs quan en el programa cutre que et ve a Ubuntu per defecte puc veure dvd's, avi's, dvix, etc.....

---

### Post by papapep on 2007-09-24
Crec que aquí pots trobar solució al teu problema (tot i que tu no estiguis intentant ara llegir DVD's):

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by patrickfromspain on 2007-09-24
sudo apt-get install libxine1 libxine1-ffmpeg libxine-extracodecs kaffeine-xine

salut!

---

### Post by cesvi87 on 2007-09-24
Gràcies a tots!!

Malgrat que l'antena que ve al pack no vagi bé, al conectar-ho a l'antena col·lectiva ja se'm veu i se'm senten els canals de TDT, Tot i que no sé perquè  pero al rastrejar automàticament i al rastrejar des de el repetidor de la Mussara, només m'agafa els canals de TVE i TVC.

---


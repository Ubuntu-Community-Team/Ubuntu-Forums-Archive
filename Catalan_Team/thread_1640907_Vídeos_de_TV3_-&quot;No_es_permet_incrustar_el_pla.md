---
title: "Vídeos de TV3 -&quot;No es permet incrustar el player en aquest site&quot;"
date: 2010-12-08
forum: Catalan Team
---

### Post by jinglada on 2010-12-08
Faig servir 5 navegadors: Chromium, Firefox, Galeon, Epiphany i Seamonkey i en tots 5 veig bé els videos de YouTube, TED, RTVE i qualsevol dels incrustats a qualsevol lloc web, excepte els de TV3, tant si són des de tv3.cat com si són incrustats a qualsevol web. 
Surt sempre el següent missatge: "No es permet incrustar el player en aquest site".
En el mateix ordinador, sota windows els veig bé.
Què hauria de fer?
Gràcies a la bestreta,
Joan Inglada

---

### Post by wgarcia on 2010-12-08
Et deu faltar alguna extensió per als navegadors. Tens tots els còdecs de vídeo instal·lats?

---

### Post by jinglada on 2010-12-08
> **wgarcia said:**
> Et deu faltar alguna extensió per als navegadors. Tens tots els còdecs de vídeo instal·lats?

Gràcies per respondre. Em pots dir com es fa per saber-ho. No fa gaire que tot funcionava bé i no he modificat res més que les actualitzacions recomenades.

---

### Post by jinglada on 2010-12-08
> **jinglada said:**
> Gràcies per respondre. Em pots dir com es fa per saber-ho. No fa gaire que tot funcionava bé i no he modificat res més que les actualitzacions recomenades.

He vist en un altre fil que suggeries fer:

*sudo aptitude search flash | grep ^i*

i no ha donat res així que he fet el següent

*sudo apt-get install ubuntu-restricted-extras*

i ja veig els videos de TV3 en tots els navegadors.

Gràcies!

---

### Post by marteljorge on 2010-12-09
> **jinglada said:**
> He vist en un altre fil que suggeries fer:

*sudo aptitude search flash | grep ^i*

i no ha donat res així que he fet el següent

*sudo apt-get install ubuntu-restricted-extras*

i ja veig els videos de TV3 en tots els navegadors.

Gràcies!

De segur que era el java o el javascript el que no anava...

---

### Post by CarlesOriol on 2010-12-11
Si... o la cpu i la cache oi?

A veure. El web de tv3 no té java i el javascript no és una tecnologia amb cap restricció, per tant no té res a veure amb el que comenta en jinglada. 

Evidentment mancaven codecs de reproducció de video com comenta en wgarcia.

---

### Post by jinglada on 2010-12-18
Ja torno a tenir problemes. Dels 5 navegadors: Chromium, Firefox, Galeon, Epiphany i Seamonkey, només veig bé els videos de TV3 en Chromium i Seamonkey.En els altres, Firefox, Galeon i Epiphany, surt sempre el fatídic missatge: "No es permet incrustar el player en aquest site".

sudo aptitude search flash | grep ^i
i A flashplugin-installer           - Adobe Flash Player plugin installer       
i   flashplugin-nonfree             - Adobe Flash Player plugin installer (trans

Què faig?

---

### Post by lpargemi on 2010-12-19
A mi em passa el mateix amb firefox (no faig anar altres navegadors sobre Ubuntu 9.04 de 64 bits. Amb aquesta ordre surt:

```
sudo aptitude search flash | grep flash
v   abrowser-flashblock             -                                           
v   abrowser-flashgot               -                                           
v   firefox-flashblock              -                                           
v   firefox-flashgot                -                                           
v   flashblock                      -                                           
p   flashgot                        - transitional dummy package                
i   flashplugin-installer           - Adobe Flash Player plugin installer       
p   flashplugin-nonfree             - Adobe Flash Player plugin installer (trans
p   flashrom                        - Identify, read, write, erase, and verify B
p   flashybrid                      - automates use of a flash disk as the root 
p   m16c-flash                      - Flash programmer for Renesas M16C and R8C 
p   python-webflash                 - Portable flash messages for Python WSGI ap
v   seamonkey-flashgot              -                                           
v   thunderbird-flashgot            -                                           
p   vrflash                         - tool to flash kernels and romdisks to Agen
p   xul-ext-flashblock              - mozilla extension to block Adobe Flash con
p   xul-ext-flashgot                - Turns every supported download manager int
v   xulrunner-flashgot              -      
```

I tinc instal·lat ubuntu-restricted-extras.

Salut!  

Lluís

---

### Post by PatrickVogeli on 2010-12-19
podeu posar un enllaç d'alguna cosa que no funciona??

---

### Post by jinglada on 2010-12-19
> **PatrickVogeli said:**
> podeu posar un enllaç d'alguna cosa que no funciona??
Ës curiós perquè veig els vídeos de la Marató que estan a: [http://www.tv3.cat/](http://www.tv3.cat/) però aquest: [http://www.tv3.cat/videos/3274950/Retallades-culturals-a-Valencia](http://www.tv3.cat/videos/3274950/Retallades-culturals-a-Valencia)  o els de la Riera: [http://www.tv3.cat/lariera](http://www.tv3.cat/lariera) no me'ls deixa veure, posant el missatge "No es permet incrustar el player en aquest site".

sudo aptitude search flash | grep flash
[sudo] password for joan: 
p   flashblock                      - transitional dummy package                
i A flashplugin-installer           - Adobe Flash Player plugin installer       
i   flashplugin-nonfree             - Adobe Flash Player plugin installer (trans
p   flashrom                        - Identify, read, write, erase, and verify B
p   flashybrid                      - automates use of a flash disk as the root 
p   libroxen-flash2                 - Flash2 module for the Roxen Challenger web
p   m16c-flash                      - Flash programmer for Renesas M16C and R8C 
p   python-webflash                 - Portable flash messages for Python WSGI ap
p   vrflash                         - tool to flash kernels and romdisks to Agen
p   xul-ext-flashblock              - mozilla extension that replaces flash elem

---

### Post by lpargemi on 2010-12-20
> **jinglada said:**
> (...) però aquest: [http://www.tv3.cat/videos/3274950/Retallades-culturals-a-Valencia](http://www.tv3.cat/videos/3274950/Retallades-culturals-a-Valencia)(...)  

Entrant a aquest enllaç em passa el mateix. Fent click amb l'altre botó i triant "About Adobe Flash Player" vaig a parar a la impressió de pantalla que us afegeixo:

On hi diu que tinc instal·lada la versió 10.0.45.2 però que hi ha disponible la versió 10.1.102.65. El Problema és que buscant per la pàgina d'Adobe la versió 10.1 que trobo és per a 32 bits i no per a 64. Jo estic fent servir Ubuntu 10.04 de 64 bits.

Pot anar per aquí la cosa?

---

### Post by jinglada on 2010-12-21
> **lpargemi said:**
> Entrant a aquest enllaç em passa el mateix. Fent click amb l'altre botó i triant "About Adobe Flash Player" vaig a parar a la impressió de pantalla que us afegeixo:

On hi diu que tinc instal·lada la versió 10.0.45.2 però que hi ha disponible la versió 10.1.102.65. El Problema és que buscant per la pàgina d'Adobe la versió 10.1 que trobo és per a 32 bits i no per a 64. Jo estic fent servir Ubuntu 9.04 de 64 bits.

Pot anar per aquí la cosa?

Mireu que acabo de trobar:
[http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)
[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)
[http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html](http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html)
en totes tres diu:
We have closed the Flash Player 10 for 64-bit Linux program on Adobe Labs and have made Flash Player “Square” available. Learn more and download Flash Player “Square.”
que és aquí:
[http://labs.adobe.com/technologies/flashplayer10/square/](http://labs.adobe.com/technologies/flashplayer10/square/)
i aquí hi ha el plugin:
[http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)
[http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz)

A una altra pàgina antiga ([http://www.laconsolablog.com/2009/02/06/instalar-flash-player-10-en-ubuntu-64-y-32-bits/](http://www.laconsolablog.com/2009/02/06/instalar-flash-player-10-en-ubuntu-64-y-32-bits/)) recomanen desinstal·lar el flashplugin-nonfree:

# Bajar el archivo:

# Descomprimirlo (Recuerda estar situado en el directorio donde bajaste el archivo):
tar zxvf (el fitxer baixat)

# Desinstalar las versiones antiguas (Si están instaladas):
sudo apt-get remove flashplugin-nonfree

# Copiarlo a la carpeta de plugins de Mozilla:
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/

---------------------------------------

Quina és la opinió dels experts?

---

### Post by lpargemi on 2010-12-22
> **jinglada said:**
> 
# Copiarlo a la carpeta de plugins de Mozilla:
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/


Hola de nou. 

He seguit això. Amb el meu anglès de fireta em sembla entendre que des d'Adobe diuen que han deixat de treballar en l'Adobe Flash Player per a Linux 64 bits i recomanen provar amb aquest Adobe Flash Square.

L'he descarregat, és un fitxer compactat amb un sol fitxer: libflashplayer.so d'uns 10 Mb. 
He substituït el que hi havia del mateix nom al directori indicat pel nou (guardant el vell a una altra banda) i m'ha funcionat i he vist el video de l'enllaç la primera vegada. Quan n'he provat un altre ja no ha anat de nou.

Finalment he anat al directori /usr/lib/firefox/plugins/ -que també existeix- i hi he creat un enllaç al fitxer del mozilla amb el mateix nom
```
sudo ln -s /usr/lib/mozilla/plugins/libflashplayer.so libflashplayer.so
```

Des d'aleshores que puc veure el vídeos. A veure quan dura

Salut

Lluís

---

### Post by jinglada on 2010-12-23
> **lpargemi said:**
> Hola de nou. 

He seguit això. Amb el meu anglès de fireta em sembla entendre que des d'Adobe diuen que han deixat de treballar en l'Adobe Flash Player per a Linux 64 bits i recomanen provar amb aquest Adobe Flash Square.

L'he descarregat, és un fitxer compactat amb un sol fitxer: libflashplayer.so d'uns 10 Mb. 
He substituït el que hi havia del mateix nom al directori indicat pel nou (guardant el vell a una altra banda) i m'ha funcionat i he vist el video de l'enllaç la primera vegada. Quan n'he provat un altre ja no ha anat de nou.

Finalment he anat al directori /usr/lib/firefox/plugins/ -que també existeix- i hi he creat un enllaç al fitxer del mozilla amb el mateix nom
```
sudo ln -s /usr/lib/mozilla/plugins/libflashplayer.so libflashplayer.so
```

Des d'aleshores que puc veure el vídeos. A veure quan dura

Gràcies Ipargemi. Jo només he fet una còpia (/usr/lib/mozilla/plugins/) i em funciona.

---

### Post by jmanel on 2012-07-06
Jo nomes vaig haver d'actualitzar el non-free plugin a la versió 11 del flash. El vaig esborrar i el vaig tornar a instal·lar y ell sol va fer la feina.
  Vaig copiar el fitxer 
   /usr/lib/flashplugin-nonfree/libflashplayer.so
al lloc on els busca el firefox.

---


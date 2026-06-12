---
title: "No funciona el efectes de compiz"
date: 2011-04-01
forum: Catalan Team
---

### Post by dariusill on 2011-04-01
Hola a tots i totes,

El compiz em funcionava molt bé i els efectes que aquest programa comporta. Ara no sé que em passa que no funciona. Algú em pot ajudar? Gràcies

---

### Post by Funk'u on 2011-04-02
Home dariusill, a grosso modo et diria que no ho sé, però si pots explicar més detalls: 

Et funciona el 3D?, has mirat si et dona algun error?, mira que no se't hagi desconfigurat la tarja gràfica, etc.

Ja diràs, salut!

---

### Post by wgarcia on 2011-04-03
Un suggeriment senzill inicial és anar al menú Sistema -> Preferències -> Aparences, i a la pestanya "Efectes visuals" mirar si està marcat "Efectes especials".

---

### Post by dariusill on 2011-04-03
Hola,

A Sistema -> Preferències -> Aparences, i a la pestanya "Efectes visuals" mirar si està marcat "Efectes especials" no esta marcat ni em deixa marcar. Quan ho intento **em diu que no estan instal·lats els controladors necessaris. **

Per altra banda, no puc fer gran la imatge dels videos d'Streaming i a vegades ni els videos en format petit. Quan no puc veure-ho ni em petit m'apareix una informació que em diu que el **connector ADobe flash ha fallat**. 

Puc mirar pelis i series al VLC, això si. 

NO tinc cap efecte 3D. COm miro que no s'hagi desconfigurat la targeta gràfica?


Merci !

---

### Post by kukat on 2011-04-05
MMm......
Ara no tinc l'Ubuntu a mà, però tens que anar a 
"Sistema" i buscar un apartat de "Controladors de maquinari" o quelcom semblant. 
Hi ha una opció que t'instal·la els controladors propietaris.

---

### Post by kukat on 2011-04-05
per cert, quina targeta gràfica tens?? 
Quanta RAM, quin processador????

Amb ordinadors antics el Flash dona problemes (almenys amb la meua ATi 9550 i el meu AMD de l'any de la picor). No està gens optimitzat el Flash per a funcionar ràpid a màquines antigues.

---

### Post by dariusill on 2011-04-05
Ei Hola!

El meu portàtil és molt nou, amb prou feines té 3 mesos. No és per tant un problema d'obsolescència.

Per a saber quina targeta gràfic tinc he fet això :

  	 	 	 	 	 	  spci | grep -i vga
 

 **La que tinc**:  
 
 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

---

### Post by wgarcia on 2011-04-06
Per descartar més coses, verifica si tens els mòduls d'Intel instal·lats. Per això des d'una terminal entra:

sudo dpkg -l xserver-xorg-video-intel

a veure què et diu.

---

### Post by dariusill on 2011-04-06
Ei wgarcia,

Quan faig aquest comendament a la terminal: sudo dpkg -l xserver-xorg-video-intel, Em surt això : 

[B]Desitjat=desconegUt/Instal·la/supRimeix/Purga/retín(H)
| Estat=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Estat,Err: majúsc.=dolent)
||/ Nom            Versió        Descripció
+++-==============-==============-============================================
ii  xserver-xorg-v 2:2.12.0-1ubun X.Org X server -- Intel i8xx, i9xx display d
[/B]

Merci

---

### Post by wgarcia on 2011-04-06
D'acord, sembla que tens instal·lat correctament els controladors de la targeta gràfica. Ara es pot mirar el directori on es guarden els fitxers de configuració del sistema gràfic X per veure si hi ha algun problema aquí. per això des de la terminal fes:

ls -l /etc/X11

a veure quins fitxers hi ha a aquest directori.

---

### Post by dariusill on 2011-04-06
ls -l /etc/X11
total 72
drwxr-xr-x 2 root root  4096 2010-10-07 18:14 app-defaults
drwxr-xr-x 2 root root  4096 2010-10-07 18:14 cursors
-rw-r--r-- 1 root root    14 2010-10-07 18:15 default-display-manager
drwxr-xr-x 6 root root  4096 2010-10-07 18:10 fonts
-rw-r--r-- 1 root root 17394 2010-05-28 03:59 rgb.txt
lrwxrwxrwx 1 root root    13 2011-02-25 12:37 X -> /usr/bin/Xorg
drwxr-xr-x 3 root root  4096 2010-10-07 18:14 xinit
drwxr-xr-x 2 root root  4096 2010-04-15 14:12 xkb
-rwxr-xr-x 1 root root   709 2010-08-09 12:20 Xreset
drwxr-xr-x 2 root root  4096 2010-10-07 18:01 Xreset.d
drwxr-xr-x 2 root root  4096 2010-10-07 18:01 Xresources
-rwxr-xr-x 1 root root  3730 2010-08-09 12:30 Xsession
drwxr-xr-x 2 root root  4096 2011-02-27 14:17 Xsession.d
-rw-r--r-- 1 root root   265 2010-05-28 03:59 Xsession.options
-rw------- 1 root root   601 2010-10-07 18:01 Xwrapper.config


wgarcia recora'm que t'he de convidar a un sopar

dàrius

PD visaca el barça!

---

### Post by wgarcia on 2011-04-07
Encara ha quedat pendent la resposta a suggeriments d'altres fils:

1) has pogut entrar com un altre usuari i continues sense efectes especials?

2) tens altres nuclis d'arrancada al Grub que pots provar?

I una altra pregunta:

Quina versió d'Ubuntu tens instal·lada?

(des d'una terminal "lsb_release -d")

---

### Post by dariusill on 2011-04-08
Hola,

Responc preguntes:


[LIST]
[*]La versió d'ubuntu és la última 10.10.
[*]No canvia res si entro des de un altre usuari.
[*]No sé que és això del Gurb....
[/LIST]

Un fet que potser és rellevant és que em vaig instal·lar un emulador d'interfície MAC. Funcionava molt bé i m'agradava fins que la targeta gràfica per algun fet inesperat ha deixat de funcionar i amb ella els efectes especials que són molt útils ( com per exemple anar directe a l'escriptori o poder veure totes les finestres i aplicacions que tinc obertes per poder anar a una concreta. 

En fi.... espero sol·lucionar-ho...

Merci!!!

---

### Post by wgarcia on 2011-04-08
El Grub és una pantalla inicial que et surt on pots escollir entre diversos sistemes operatius, si els tens instal·lat, i que et manté nuclis de linux antics a més del més recent. Si no la veus en iniciar l'ordinador és possible que o bé ho tinguis configurat per entrar directament a un nucli, o tinguis un sol nucli i cap altre sistema operatiu. 

Abans d'investigar més com ho tens això i si pots entrar en algun nucli més antic, pots provar des d'una terminal la següent ordre:

sudo apt-get install --reinstall xserver-xorg-video-intel

a veure si s'ha desconfigurat alguna cosa, perquè és estrany que quan vols activar els efectes inicials et digui que necessites el controlador, quan el tens.

---

### Post by dariusill on 2011-04-08
Aquest és el resultat ...
sudo apt-get install --reinstall xserver-xorg-video-intel
[sudo] password for darius: 
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
El paquet següent s'ha instal·lat automàticament i ja no serà necessari:
  kfind
Empreu «apt-get autoremove» per a suprimir-los.
0 actualitzats, 0 nous a instal·lar, 1 reinstal·lats, 0 a suprimir i 12 no actualitzats.
Es necessita obtenir 250kB d'arxius.
Després d'aquesta operació s'empraran 0B d'espai en disc addicional.
Bai:1 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main xserver-xorg-video-intel i386 2:2.12.0-1ubuntu5.2 [250kB]
250kB baixats en 0s (853kB/s)              
(S'està llegint la base de dades … hi ha 226597 fitxers i directoris instal·lats actualment.)
S'està preparant per a reemplaçar xserver-xorg-video-intel 2:2.12.0-1ubuntu5.2 (fent servir …/xserver-xorg-video-intel_2%3a2.12.0-1ubuntu5.2_i386.deb) …
S'està desempaquetant el reemplaçament de xserver-xorg-video-intel …
S'estan processant els activadors per a man-db …
S'està configurant xserver-xorg-video-intel (2:2.12.0-1ubuntu5.2) …
S'estan processant els activadors per a libc-bin …
ldconfig deferred processing now taking place

---

### Post by wgarcia on 2011-04-08
D'acord, però ja pots posar els efectes especials?

També pot ser interessant veure quin nucli estàs fent servir:


uname -a

des d'una terminal.

---

### Post by dariusill on 2011-04-08
hOLA,

Com a resposta al comandament   **uname -a**:



Linux Acer-TravelMate-5335 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux


No...no em funcionen els efectes especials.... :( 

Ill

---

### Post by wgarcia on 2011-04-15
D'acord, sembla estar tot al dia. Et suggereixo una altra cosa, per descartar que hi ha hagi alguna cosa mal configurada a la teva instal·lació actual que no som capaços de trobar. 

Intenta crear-te un USB o un CD per al Maverick amb la imatge per instal·lar i per provar "Live" el sistema. Si tens algun CD de la instal·lació original del Maverick ja serveix. Inicia el sistema al CD i escull "Provar Ubuntu" (i no instal·lar), i un cop que s'iniciï la sessió intenta activar els efectes especials a veure què et diu i si ho pots fer.

---


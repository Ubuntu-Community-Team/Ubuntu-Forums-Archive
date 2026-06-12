---
title: "Unity ha petat a ubuntu 14.04"
date: 2015-03-21
forum: Catalan Team
---

### Post by Txaume on 2015-03-21
Bones !
Fa uns dies que el ubuntu 14.04 hem donava erros del sistema ( reportar error, etc...) i es penjava el gestor d'actualitzacions.
Llavors he actualitzat pel terminal i ja no m'ha funcionat més. He canviat l'entorn d'escriptori a gnome i sembla que funciona. però si poso unity queda penjat.

A veure si algú sap com solucionar-ho...

Gràcies

---

### Post by wgarcia on 2015-03-21
Sembla ser un problema del sistema gràfic. Saps quina targeta gràfica tens? Si no ho saps ho pots esbrinar obrint una terminal i entrant:

```
lspci | grep -i vga
```

Un cop sàpigues la targeta gràfica s'haurà de veure si no s'ha de reconfigurar el sistema gràfic.

---

### Post by Txaume on 2015-03-21
La targeta grafica es una Nvidia.
El teminal diu :  VGA compatible controller: NVIDIA Corporation C61 [GeForce 7025 / nForce 630a] (rev a2)

Gracies !

---

### Post by wgarcia on 2015-03-22
L'actualització per terminal s'ha completat? Està ara tot actualitzat?

---

### Post by Skaperen on 2015-03-22
> **Txaume said:**
> Bones !
Fa uns dies que el ubuntu 14.04 hem donava erros del sistema ( reportar error, etc...) i es penjava el gestor d'actualitzacions.
Llavors he actualitzat pel terminal i ja no m'ha funcionat més. He canviat l'entorn d'escriptori a gnome i sembla que funciona. però si poso unity queda penjat.

A veure si algú sap com solucionar-ho...

Gràcies

Unity og Ubuntu 14.04.2 ut til å virke fint for meg.

---

### Post by Txaume on 2015-03-22
Si, ara està tot actualitzat i continua fallant.

---

### Post by wgarcia on 2015-03-22
Pots entrar una terminal:

```
ubuntu-drivers devices
```

Això et dirà quins controladors necessita la teva targeta gràfica. Després el que es pot fer és intentar desinstal·lar el controlador propietari i usar el no-propietari (nouveau). Si no et va bé el controlador lliure, després es pot buscar alguna altra versió del controlador propietari a veure si va millor.

---

### Post by Txaume on 2015-03-22
El controlador lliure no es penjava el unity, però no hem trobava la resolució de pantalla ( tot molt gros i deforme ), he probat els altres i tots s'hem penja.
[CENTER][CENTER][COLOR=#000000][FONT=sans-serif][CENTER][COLOR=#000000][FONT=sans-serif][ [img]http://thumbs.subefotos.com/bd30934323b9e11609e757388b5cd887o.jpg[/img]](http://subefotos.com/ver/?bd30934323b9e11609e757388b5cd887o.png)[/FONT][/COLOR][/CENTER]  [/FONT][/COLOR][/CENTER]
[/CENTER]

---

### Post by wgarcia on 2015-03-23
D'acord, llàstima que el controlador lliure sembli no funcionar bé per a la teva targeta gràfica, perquè cada cop va millor en la meva experiència. Potser no tens els últims controladors propietaris de la targeta nvidia. La versió 304 sembla ser una mica antiga. La versió 331 em sembla que també dóna suport a la teva targeta. Intenta instal·lar-la fent :

```
sudo apt-get install nvidia-331
```

i després a veure si et surt a la llista de controladors addicionals i la pots provar.

---

### Post by Txaume on 2015-03-23
Hola

Amb el 331 no hem funciona ni unity ni gnome.

He iniciat en "recovery mode" he tornat a instalar la versió 304 teclejant "sudo apt-get install nvidia-304".

Buscant he trobat aquesta pagina : [https://csargomez.wordpress.com/2014/08/01/instalar-nvidia-driver-en-ubuntu/](https://csargomez.wordpress.com/2014/08/01/instalar-nvidia-driver-en-ubuntu/)
He seguit les passes per instalar la última versió del controlador, torna a passar el mateix, miro els controladors i segueixo tenint el 304.
Llavors no sé si el 304 és realment la última versió del controlador o si la pagina aquesta funciona o no...

---

### Post by wgarcia on 2015-03-24
Has provat de posar-li "nomodeset" a l'arrencada d'Ubuntu? Per provar si fa alguna diferència, al menú d'arrencada de linux (el grub) has d'entrar en "Opcions avançades", i prémer la tecla "e" per editar els paràmetres d'arrencada. 

Al final de la línia que comença amb "linux /vmlinuz root=UUID=..." has d'escriure "nomodeset" i després arrencar el sistema (hi ha una tecla per fer-lo, ara no recordo quina és però t'ho posa a la mateixa pantalla). 

Això és temporal, sols val per aquesta arrencada, però si funcionés després es pot posar perquè ho recordi.

---

### Post by Txaume on 2015-03-24
Ho he fet, però es queda igual.

Deu ser un problema de controladors, ja que posant el Nouveau unity funciona, però només hem deixa opció de pantalla 800x600, o sigui baixa resolució i tot gros i un pel deformat.
De moment vaig tirant amb gnome...

---

### Post by wgarcia on 2015-03-25
Pots enganxar la sortida de la següent ordre a una terminal?:

```
dpkg -l nvidia*
```

---

### Post by Txaume on 2015-03-25
Hola 

Si, hem surt :
> dpkg-query: no s'ha trobat cap paquet que correspongui amb nvidia-bug-report.log.gz


---

### Post by wgarcia on 2015-03-26
Què estrany!, t'haurien de sortir els paquets corresponents als controladors nvidia. Per exemple a mi al meu sistema em surt:

```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
rc  nvidia-304     304.84-0ubun amd64        NVIDIA binary Xorg driver, kernel
rc  nvidia-313-upd 319.60-0ubun amd64        Transitional package for nvidia-3
rc  nvidia-319-upd 319.60-0ubun amd64        NVIDIA binary Xorg driver, kernel
rc  nvidia-331     331.38-0ubun amd64        NVIDIA binary driver - version 33
rc  nvidia-331-upd 340.76-0ubun amd64        Transitional package for nvidia-3
un  nvidia-331-upd <none>       <none>       (no description available)
un  nvidia-331-uvm <none>       <none>       (no description available)
ii  nvidia-340-upd 340.76-0ubun amd64        NVIDIA binary driver - version 34
ii  nvidia-340-upd 340.76-0ubun amd64        NVIDIA Unified Memory kernel modu
ii  nvidia-common  1:0.4.1      amd64        transitional package for ubuntu-d
rc  nvidia-current 304.84-0ubun amd64        Transitional package for nvidia-c
un  nvidia-driver- <none>       <none>       (no description available)
rc  nvidia-libopen 331.38-0ubun amd64        NVIDIA OpenCL Driver and ICD Load
rc  nvidia-libopen 331.113-0ubu amd64        NVIDIA OpenCL Driver and ICD Load
un  nvidia-libopen <none>       <none>       (no description available)
un  nvidia-libopen <none>       <none>       (no description available)
un  nvidia-opencl- <none>       <none>       (no description available)
rc  nvidia-opencl- 331.38-0ubun amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl- 340.76-0ubun amd64        Transitional package for nvidia-o
ii  nvidia-opencl- 340.76-0ubun amd64        NVIDIA OpenCL ICD
un  nvidia-persist <none>       <none>       (no description available)
ii  nvidia-prime   0.8          amd64        Tools to enable NVIDIA's Prime
ii  nvidia-setting 346.47-0ubun amd64        Tool for configuring the NVIDIA g
un  nvidia-setting <none>       <none>       (no description available)
rc  nvidia-setting 319.60-0ubun amd64        Tool for configuring the NVIDIA g
un  nvidia-setting <none>       <none>       (no description available)
un  nvidia-uvm     <none>       <none>       (no description available)
un  nvidia-va-driv <none>       <none>       (no description available)
un  nvidia-vdpau-d <none>       <none>       (no description available)

```

Em mostra quins paquets tinc instal·lats (ii) i alguns altres que en algun moment vaig fer servir (aquest és un sistema que vinc actualitzant des de fa uns anys). 

Prova de nou la mateixa ordre però posa-li "sudo" endavant, jo crec que no fa falta per llistar els paquets, però potser sí. Si tornés a sortir el mateix prova:

```
sudo apt-get install nvidia-304
```

però segons el que dius t'hauria de sortir que ja està instal·lat.

---

### Post by Txaume on 2015-03-26
Si, surt que ja està instal.lat...
> S'està llegint la llista de paquets&#8230; Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet
nvidia-304 ja es troba en la versió més recent.
Els paquets següents s'han insta&#320;lat automàticament i ja no són necessaris:
  bbswitch-dkms nvidia-prime
Empreu «apt-get autoremove» per a suprimir-los.
0 actualitzats, 0 nous a insta&#320;lar, 0 a suprimir i 10 no actualitzats.


---

### Post by wgarcia on 2015-03-28
Fixa't que a l'ultima línia de la sortida que has posat, diu "0 actualitzats, 0 nous a insta&#320;lar, 0 a suprimir i 10 no actualitzats."  Sembla que hi ha alguns paquets retinguts. Per instal·lar-los pots fer:

```
sudo apt-get dist-upgrade
```

Però compte. Abans d'acceptar l'actualització repassa què farà, a vegades per paquets retinguts el sistema d'actualització demana desinstal·lar coses importants, como ara ubuntu-desktop o coses així. En aquest cas abans de fer l'actualització s'haurà de veure què fer amb això, normalment reinstal·lant el que es desinstal·la ja està, però millor anar en compte.

Si veus que no desinstal·la res, o desinstal·la un paquet per reinstal·lar una versió més nova, es pot acceptar sense problemes.

---

### Post by Txaume on 2015-03-30
Bones 
Unity continua fallant
He fet tal com deies, he mirat que no desinsta&#320;lés res i he acceptat.
He actualitzat el sistema, he tornat a canviar els controladors a veure si anava, però tot continúa igual...

---

### Post by wgarcia on 2015-03-31
Has provat si entrant amb un usuari diferent al teu també falla l'Unity? Si tens l'usuari "Guest" pots entrar amb aquest usuari a veure què passa, i sinó crear-te un de nou i entrar amb aquest nou usuari. Per descartar que no sigui alguna configuració incorrecta del teu usuari el que estigui causant el que descrius.

---

### Post by Txaume on 2015-03-31
Perta igual als demés usuaris, a la "sessió de convidat" també.

---

### Post by wgarcia on 2015-04-01
Sembla estrany que el teu sistema no funcioni, perquè no sembla una targeta gràfica massa complicada. Penso que pot ser un problema de mala configuració del controlador de Nvidia. Una cosa que em sembla encara no s'ha provat és:

```
 sudo dpkg-reconfigure xserver-xorg 
```

---

### Post by Txaume on 2015-04-23
Bones.

Després de intentar 1000 coses vaig decidir fer net i reinstal.lar ubuntu 14.04, però continuava fallant.

He esperat a poder baixar-me el 15.04 (Vivid Vervet), l'he instal.lat i de bones a primeres m'ha fallat també. 
He cambiat el controlador "Nouveau" pel de Nvidia i de moment sembla que funciona. Creuaré els dits...

Salut i gracies per tot !

---

### Post by wgarcia on 2015-04-24
Aquesta edició de l'Ubuntu porta uns controladors propietaris de NVIDIA força actualitzats, potser sigui això. La veritat que és un mal de cap aquest tema dels controladors propietaris, jo sempre que puc faig servir targetes gràfiques Intel que sols tenen controladors oberts. Però no sempre és possible, hi ha un munt d'ordinadors que venen amb targetes NVIDIA i ATI.

---


---
title: "videocamara"
date: 2007-06-16
forum: Catalan Team
---

### Post by l'últim mico on 2007-06-16
Hola,

estic intentant editar videos que tinc grabats amb videocam.

El problema es que no tinc manera de llegir el contingut de la camera, amb cap dels programes que he probat (VLC, kino, etc...).

La camera es Panasonic NV-GS37, MIni DV, i conecta via USB.

En el mateix port USB on la conecto he conectat Memory sticks o reproductors mp3, i els reconeix al momemt (com si fossin discos externs)., per tant en principi el port funciona.

He probat varies configs dels programes i no aconsegueixo veure res.

Si teniu alguna pista.

Dani

---

### Post by orestesmas on 2007-06-16
Probablement la càmera no estigui suportada pel nucli (no hi ha controlador). Potser els de Panasonic fan que les videocàmeres seves tinguin una manera "no estàndard" de presentar-se al Sistema Operatiu.

Veig que ho has preguntat en un fòrum anglès fa 6 dies, però que no t'han respost encara.

A veure què hi podem fer:

- Segons sembla, la càmera disposa d'una sortida Firewire. Si el teu PC també en té una, prova de connectar-la per allí.

- Les càmeres de vídeo no són un perifèric com les memòries flash. Necessiten un controlador USB especial que es diu USB Video Class. Hi ha un projecte en marxa per suportar aquests dispositius ([http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)), però de moment a la secció "supported devices" no he vist la teva càmera (però hi ha una NV-GS27 que s'hi deu assemblar força). Sovint passa que els models més nous triguen uns mesos en ser suportats, per la qual cosa potser has d'esperar una mica, i eventualment baixar-te la darrera versió i compilar-la manualment (si tens pressa). De tota manera, sempre pots preguntar al seu fòrum, a veure què tal.

Sort.

---

### Post by AlexMuntada on 2007-06-17
Estic amb l'Orestes, habitualment la millor manera de connectar les càmeres de vídeo és a través del firewire (i-link o 1394, segons la marca s'anomena d'una manera o una altra).

---

### Post by l'últim mico on 2007-06-19
Gràcies, nois.

disculpeu el meu desconeixement ABSOLUT, però suposo que si no pregunto no n'aprendré mai.

No tinc firewire al PC, per tant haig de probara amb l'USB.

Vull intentar-ho amb el controlador del la Nv-gs27. Això com funciona? Descarrego el controlador i l'instal.lo  i a correr (com en win), o te alguna complicació més?

---

### Post by orestesmas on 2007-06-19
A veure: tu pretens utilitzar un controlador d'un dispositiu diferent al que tu tens. Això no seria senzill ni en windows (bé, crec que en windows seria poc menys que impossible. En linux podries apanyar-te-les per enganyar el sistema).

El motiu de tot això és que cada dispositiu USB queda identificat per un número. Si obres una consola i tecleges "lsusb" (sense cometes, evidentment) veuràs quelcom del tipus:

Bus 002 Device 005: ID **04e8:323a** Samsung Electronics Co., Ltd
Bus 002 Device 002: ID **046d:c207** Logitech, Inc. WingMan Extreme Digital 3D
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID **058f:6362** Alcor Micro Corp.
Bus 001 Device 001: ID 0000:0000

Els números en negreta són als que em refereixo. Els controladors de dispositius (drivers) utilitzen aquests números per saber si el dispositiu que ells "saben" controlar és present al sistema. Si no és així refusaran de funcionar (amb bon criteri, és clar).

A la pàgina web que t'indicava especifica amb detall el dispositiu NV-GS27:

**04da:231d  	Panasonic Camcorder NV-GS27EG  	Panasonic**

És a dir, un dispositiu amb ID= 04DA:231D. Fes un "lsusb" quan tinguis la càmera endollada al USB, i si no surt el codi aquest, doncs no ho tens gaire bé.

Potser es podria modificar el codi font del driver per tal que "simulés" ser un controlador per una càmera com la que tu tens, però el més probable és que no funcioni en absolut o que funcioni només parcialment. Amb mala sort, podries carregar-te la càmera i/o el contingut de les cintes de vídeo, si el controlador intenta enviar ordres que no pertoquen.

Potser l'opció més sensata és:

1) contactar amb els desenvolupadors del projecte UVC a veure com porten el tema del teu model de càmera. Potser tu els pots facilitar informació necessària per desenvolupar el controlador.

2) Adquirir una targeta capturadora IEEE 1394 compatible amb Linux (i un cable firewire). No són pas cares i et poden solucionar el problema de forma més elegant.

---

### Post by Tomàs M. on 2007-10-13
Si utilitzeu kino, penseu que sembla que hi ha un bug i només es pot capturar com a root: [http://ubuntuforums.org/showthread.php?t=352441](http://ubuntuforums.org/showthread.php?t=352441)

Tomàs.

---


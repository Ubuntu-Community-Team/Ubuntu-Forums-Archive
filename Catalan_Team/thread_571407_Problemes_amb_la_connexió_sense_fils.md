---
title: "Problemes amb la connexió sense fils"
date: 2007-10-09
forum: Catalan Team
---

### Post by eduardsola on 2007-10-09
Hola a tothom, sóc nou amb això de l'Ubuntu i no sé com em puc connectar a Internet, he provat lo de configurar la xarxa amb la xarxa que feia servir per Windows i no em funciona... tinc un router de telefonica i una targeta de xarxa Conceptronic... he intentat instal·lar els drivers que venen amb el cd d'instal·lació i no em deixa perquè com que són .exe, el Linux no els pot executar.

Ara em puc connectar des del portatil que volta per casa, però no sé quan durarà, a part, que m'agradaria fer servir Ubuntu plenament i oblidar-me del Windows.

Que algú m'ajudi, em podeu enviar la resposta per aquí: [email]eduard.1714@gmail.com[/email] o bé contestar-me aquí al fòrum.

Moltes gràcies per avançat.

Salut!

---

### Post by Ferri on 2007-10-09
Podries explicar una mica millor quin és el problema?
Ubuntu et reconeix la tarja de xarxa?
És una tarja interna o la connectes a un port USB, per exemple? Podries posar exactament el model?
Qin tipus de xarxa fas servir? Tens IP fixa, fas servir DHCP? Has posat bé els servidors DNS?
Si et detecta la tarja, posa què et diu si intentes fer ping al router (molt sovint, 192.168.1.1, igual que la teva passarel·la per defecte). Si pots fer ping al router, posa què et surt fent "route -C".

---

### Post by eduardsola on 2007-10-09
A veure, jo crec que sí que me la reconeix, car quan vas a System-->Administració-->Xarxa, hi ha una entrada que hi diu "Wireless connection (wlan0)" jo he configurat aquesta, però no es connecta ^^'

És una tarja connectada a un port USB, és Conceptronic 54Mbps Wireless Network Card/Adapter [Version 2.0], això és el que posa al cd d'instal·lació, fa força temps que la tinc i amb Windows funcionava de conya, però ara amb l'Ubuntu no sé com fer-la funcionar.

La xarxa és DHCP, IP dinàmica. Això del DNS m'agradaria saber què és xD i que hi he de posar allà, car crec que és aquest el problema que tinc.

Gràcies!

Salut!

---

### Post by CarlesOriol on 2007-10-09
Saps quin xipset du la targeta de xarxa? (broadcom, ralink... a vegades es pot veure al xip, sinó el model exacte també ajuda).

---

### Post by eduardsola on 2007-10-09
C54RU és el model que hi posa a radere la tarja.

Al cd d'instal·lació hi posa aquests números:

C54Ri/C54RC/C54RU

^^'

---

### Post by pespin on 2007-10-09
Llavors has d'instal·lar segurament els xips ralinktech [http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page")

---

### Post by eduardsola on 2007-10-09
D'acord, vaig a fer-ho.

Gràcies a tots per ajudar-me!

---


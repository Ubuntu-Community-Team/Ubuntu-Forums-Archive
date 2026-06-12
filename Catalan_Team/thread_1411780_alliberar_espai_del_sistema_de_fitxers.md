---
title: "alliberar espai del sistema de fitxers"
date: 2010-02-20
forum: Catalan Team
---

### Post by loles on 2010-02-20
Hola!

Tinc el ubuntu instal·lat al meu ordinador i ja fa un temps que m'apareix aquest missatge d'error.

"El volum arrel del sistema de fitxers només li resta 58,9MB espai de disc. Podeu alliberar espai de disc suprimint programes o fitxers que no utilitzeu o movent fitxers a un altre disc o partició."

Tinc sols dos particions, una per als programes d'ubuntu i eixes coses (no ho tinc massa clar) i l'altra per a la resta dels meus documents. 

Aquest missatge m'apareix quasi sempre que estic veien alguna pel·lícula on-line o algun vídeo. 

Aquests fitxers es queden de forma permanent al meu disc? Com puc esborrar-los?

Tampoc sé quin tipus de fitxers puc canviar a l'altra partició, perquè pel que tinc entès, en aquesta partició sols hi han els programes instal·lats i pel que veig els arxius temporals...

Podeu ajudar-me?

Moltes gràcies

---

### Post by indiosincracia on 2010-02-20
per alliverar espai al disc;
sudo apt-get autoclean  (et borrarà els fitxers ".deb")
sudo apt-get autoremove  (borra llibreries instal·lades, que no utilitza cap programa)

si tinguesis la carpeta /home a la mateixa partició també pots mirar la carpeta  elteunom/.local/share/Trash

els videos s'enmagatzemen a la carpeta temporal /tmp no es queden de forma permanent cada cop que inicies l'ordinador els anteriors desapareixen

si encara tens poc espai pots ampliar la partició o eliminar algun programa que no utilitzis, vinga salut.

---

### Post by loles on 2010-02-22
Hola

Açò que em proposes no em dóna solució. A banda, cada dia va quedant-me menys espai al disc... ara dispose d'uns 80MB. Què va a passar-me?

Pense que això que dius del temp... en el meu cas no em funciona. Apague el PC i continue tenint poc molt poc espai...

Què puc fer?

---

### Post by oriolsbd on 2010-02-23
Hola,

Com a comanda complementària a la que t'ha enviat idiosincràcia, prova aquesta:
sudo apt-get clean

Si no t'acaba de fer tot l'espai que necessites, caldria analitzar-ho més a fons. Abans que res, quant espai hi tens, a la partició arrel? Després, mira com tens distribuït l'espai amb l'analitzador de discos ("Aplicacions>Accessoris>Analitzador de discos"). Quan l'obris, vés al menú "Analitzadors>Escaneja el sistema de fitxers". Segurament t'ensenyarà el motiu de la falta d'espai.

Salut!

---

### Post by loles on 2010-09-12
Ahhh!!!

Açò passa per no solucionar-ho del tot bé.

Continue amb el mateix problema que vos vaig comentar fa uns mesos. Vaig provar tot el que em vareu dir però res.

Agrairia molt si algú em pogués ajudar

---

### Post by lluisanunez on 2010-09-13
Quan espai tens a cadascuna de les particions? Ho pots mirar com et diu oriolsbd (Aplicacions>Accessoris>Analitzador de discos) o bé reiniciant des d'un CD Ubuntu i obrint (Aplicacions>Sistema>Editor de particions)

---

### Post by RainCT on 2010-09-14
O més fàcil encara:
```
df -h
```

---

### Post by marteljorge on 2010-09-15
Hi ha un programa gràfic anomenat bleachbit i et pot ajudar a fer una mica d'espai, però, no tens espai per instal·lar-lo. sincerament, no tinc informació per fer més ajuda de la què ja t'han fet. Seria bona idea tenir la sortida del que indica el RainCT.

---


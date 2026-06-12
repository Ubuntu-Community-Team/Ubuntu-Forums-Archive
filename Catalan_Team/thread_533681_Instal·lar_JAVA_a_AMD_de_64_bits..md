---
title: "Instal·lar JAVA a AMD de 64 bits."
date: 2007-08-24
forum: Catalan Team
---

### Post by muleta on 2007-08-24
Sembla que he trobat instruccions oficials per poder insttal·lar Java però no trobo el Sistema->Administración->Propiedades del software

---

### Post by papapep on 2007-08-24
Si noia, a vegades als traductors els haurien de fer una lobotomia per verificar que tenen la neurona buida:

Quan diuen "propiedades del software", es refereixen al Synaptic: Sistema > Administració > Gestor de paquets Synaptic.

Un cop dins, ves a Paràmetres > Repositoris.

---

### Post by muleta on 2007-08-24
Agraeixo el teu ajud però no trobo res de res i no entenc les instruccioons que em dona la guía: [https://help.ubuntu.com/ubuntu/desktopguide/es/extra-repositories.html](https://help.ubuntu.com/ubuntu/desktopguide/es/extra-repositories.html)

Potser hauré d'admetre que no tinc el nivell suficient.

---

### Post by papapep on 2007-08-24
No trobes el Synaptic? O no trobes el que hi ha d'haver dins que et comento jo? 

Vull assumir que si que trobes el Synaptic dins Sistema i Administració. Sinó hi és aleshores si que tens un problema de configuració del sistema.

Aleshores, suposant que hi és, clica a l'opció Preferències del menú del Synaptic, i dins d'aquí cliques a Repositoris, et trobaràs una imatge com aquesta, on podràs clicar per a definir de quins repositoris vols agafar software. (que és el d'afegir repositoris que et diu el document)

---

### Post by muleta on 2007-08-24
Ara m'ho tornaré a mirar... És que crec que havia agafat una ruta equivocada. Però, primer, he de reiniciar el pc per treure aquest requadre blanc que s'instala a la pantalla cada vegada que intento obrir el gxine buscant un reproductor de video que em funcioni.

No hi ha manera de treure-la,

---

### Post by muleta on 2007-08-24
Bé, ara obriré un altre post pel tema Reproductors, però continoant amb aquest del Java:

He arribat a aquesta pantalla i jo ho tinc tot activat, fins i tot l'última opció. 

Tornaré a intentar la instal·lació de Java desde aquelles instruccions, si les torno a trobar.

---

### Post by muleta on 2007-08-24
Què vol dir :

Java (1.5)
[Nota] 	

Las siguientes instrucciones son solo para sistemas i386 y amd64 . Para máquinas PowerPC , por favor mire el Wiki de Ubuntu (en inglés).

   1.

      Para instalar el Entorno de Ejecución de Java (Java Runtime Environment) para ejecutar programas Java, instale el paquete sun-java5-jre **[COLOR="Red"]desde el repositorio Multiverse[/COLOR]** (vea “Repositorios adicionales”).

---

### Post by dulbirakan on 2007-08-24
WOW, that was enlightening...[-o<

What was that all about?:confused:

---

### Post by pespin on 2007-08-24
Vol dir que has de tindre el repositori multiverse descomentat/actiu perquè el paquet sun-java5-jre es troba allà. 

Pots afegir/editar/comentar repositoris des del synaptics o editant l'arxiu corresponent:

```
sudo gedit /etc/apt/sources.list
```


Si al editar trobes les línies 

```
deb http://es.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://es.archive.ubuntu.com/ubuntu/ feisty multiverse
```

precedides per caràcters '#' vol dir que estan comentats, per tant desactivats. Per a activar-los simplement borra els caràcters '#' d'aquestes dues línies.

Guarda i seguidament:
```
sudo aptitude install sun-java5-jre
```

---

### Post by muleta on 2007-08-24
No, veus què em surt?. I això que hem comprovat amb papapep si tenia activades les universe i les multiverse.

Quan entro el password, s'obre aquesta pantalla en blanc.

---

### Post by muleta on 2007-08-24
aquesta...

---

### Post by pespin on 2007-08-24
No se exactament què és, si el gedit se t'ha penjat o si tens el fitxer buit :confused:

Enganxa el que et posa quan fas 'sudo aptitude update', així veurem si realment no tens repositoris xD

---

### Post by lluisanunez on 2007-08-24
ARGHH em sembla que tens obert el gedit amb /etc/apt/sources.list obert (i guardat en sessió, i penjat). Per això el Synaptic se't queixa cada vegada. 
Crec que la solució més senzilla és que obris el menú Sistema >> Adminisració >> Monitor del sistema. A la pantalla "Processos" busca el Gedit, selecciona'l i clica a "Finalitzar" (o similar, el meu va en anglès i ho estic traduint)

---

### Post by muleta on 2007-08-24
Se m'havia penjat, ho fa sempre quan demano el gedit.

M'ha sortit això:

Obté:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Obté:2 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) feisty Release.gpg [191B]       
Obté:3 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) feisty/main Translation-ca [393B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-ca  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-ca        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-ca   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-ca 
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) feisty/restricted Translation-ca        
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) feisty/universe Translation-ca          
Obté:4 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) feisty/multiverse Translation-ca [14B]
Obté:5 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) feisty-updates/main Translation-ca             
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) feisty-updates/restricted Translation-ca       
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) feisty Release                                
Obté:6 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release [50,9kB]              
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) feisty-updates Release                        
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) feisty/main Packages                          
Obté:7 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages [73,9kB]
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) feisty/restricted Packages      
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) feisty/main Sources             
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) feisty/restricted Sources       
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) feisty/universe Packages        
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) feisty/universe Sources         
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) feisty/multiverse Packages      
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) feisty/multiverse Sources       
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) feisty-updates/main Packages    
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) feisty-updates/restricted Packages
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) feisty-updates/main Sources     
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) feisty-updates/restricted Sources
Obté:8 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages [5992B]
Obté:9 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources [12,8kB]
Obté:10 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources [953B]
Obté:11 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages [26,9kB]
Obté:12 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources [3537B]
Obté:13 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages [5412B]
Obté:14 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources [1052B]
S'han recollit 182kB en 1s (128kB/s)                       
S'està llegint la llista de paquets... Fet

---

### Post by pespin on 2007-08-24
Val, si t'hi fixes a la llista que has posat surt el repositori multiverse per allà, així que sí que tens els repositoris mutliverse activats. Només et queda instal·lar-lo:
```

sudo aptitude install sun-java5-jre
```

I amb lo del gedit.... proba a reinstal·lar-lo a veure si millora. A mi no m'ha donat gaires problemes.

> sudo aptitude reinstall gedit

---

### Post by muleta on 2007-08-24
> **lluisanunez said:**
> ARGHH em sembla que tens obert el gedit amb /etc/apt/sources.list obert (i guardat en sessió, i penjat). Per això el Synaptic se't queixa cada vegada. 
Crec que la solució més senzilla és que obris el menú Sistema >> Adminisració >> Monitor del sistema. A la pantalla "Processos" busca el Gedit, selecciona'l i clica a "Finalitzar" (o similar, el meu va en anglès i ho estic traduint)

No hi era el gedit en la llista de processos. Crec que ho he arreglat amb les indicacions de Pespin.

A veure si començaré a tenir menys dificultats...

---

### Post by muleta on 2007-08-24
No s'ha instal·lat el java. Canvio de Firefox.

Gràcies per intentar-ho.

---


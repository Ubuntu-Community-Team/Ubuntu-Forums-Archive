---
title: "No puc iniciar ubuntu amb altres usuaris"
date: 2011-10-14
forum: Catalan Team
---

### Post by akyra on 2011-10-14
Hola
M'acabo d'instalar ubuntu 11.10 64 bits, i quan intento iniciar la sessió d'un altre usuari em retorna a la pantalla de inici de sessió, no em dóna temps a veure cap fallo, així que només puc iniciar la sessió amb el meu usuari, però el sistema no em va gaire bé.
També he perdut el só, de cop no el tinc, o sigui que en el hardware no apareix i fa una hora sí, i no he fet res relacionat amb el só.

No puc apagar ubuntu, quan intento apagar em retorna a la pantalla de inici de sessió.

Algú té alguna idea? És una mica desesperant canviar a una nova versió i que et deixin d'anar totes les coses que en l'anterior anaven bé.

Gracies

---

### Post by wgarcia on 2011-10-15
Has posat la sessió d'inici "lightdm"? Potser algun problema d'incompatibilitat amb la teva targeta gràfica i aquest gestor d'inici. Tens una "ati" per casualitat? Prova de tornar a "gdm" a veure si aquests problemes desapareixen. 

Des d'una terminal

sudo apt-get install gdm

o 

sudo apt-get install --reinstall gdm

i et preguntarà si vols tenir aquesta sessió d'inici. 

La versió 11.10 ve amb el nou gestor d'inici "lightdm" que es pot configurar molt però no hi ha res que es pugui fer amb aquest nou gestor que no es pugui fer amb el tradicional "gdm", almenys de moment.

---

### Post by akyra on 2011-10-15
Hola Wgarcia
Sí tinc una ATI que anava perfecte amb les versions anteriors.
Estic provant a descarregarme el gdm i no funcionen els repositoris, en surt aixó:

> jordi@jordi-Ubuntu:~$ sudo apt-get install gdm
Leyendo listas de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Paquetes sugeridos:
  uswsusp gnome-mag gok
Se instalarán los siguientes paquetes NUEVOS:
  gdm
0 actualizados, 1 se instalarán, 0 para eliminar y 0 no actualizados.
1 no instalados del todo o eliminados.
Necesito descargar 1733 kB de archivos.
Se utilizarán 7598 kB de espacio de disco adicional después de esta operación.
0% [Conectando a es.archive.ubuntu.com (150.214.5.135)] - connect (113: No existe ninguna ruta hasta el «host»)
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/universe/g/gdm/gdm_3.0.4-0ubuntu11_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/universe/g/gdm/gdm_3.0.4-0ubuntu11_amd64.deb)  No se pudo conectar a es.archive.ubuntu.com:80 (150.214.5.135). - connect (113: No existe ninguna ruta hasta el «host»)
E: No se pudieron obtener algunos archivos, ¿quizás deba ejecutar «apt-get update» o deba intentarlo de nuevo con --fix-missing?


També m'he trobat que quan deixo l'ordinador només amb bateria em diu que la tinc casi esgotada i que entrará en hibernació, cosa que és mentida, la bateria era la mateixa que abans d'instal·lar aquesta nova versió d'Ubuntu i el conky em marca el 100%.

Un altre misteri...

Respecte al só alguna idea?

Gracies

---

### Post by wgarcia on 2011-10-15
Quant a la baixada de "gdm", tens connexió a Internet? Si tens i aquest dipòsit et continua donant problemes podries provar de canviar a un altre, per exemple "http://ftp.caliu.cat" que el tenim aquí a prop.

Quant al so, pots provar amb un USB o CD autònom de la versió 11.10 i mirar si tens so aquí?

Quant a la bateria pot ser algun problema del nucli de Linux actual, hi ha alguns informes de regressions en temes de gestió d'energia amb el nucli 3.0.0, si pots provar amb algun nucli més antic a veure si no t'apareix el problema t'ho pot confirmar. També he llegit que fent servir un paquet que es diu "jupiter" es pot resoldre alguns d'aquests problemes.

---

### Post by akyra on 2011-10-15
Hola wgarcia,
El repositori continua donant problemes. 

El so el tenia tan amb el liveCD, com recient instal·lat l'ubuntu.
Després només he instal·lat els drivers restringits de l'ATI i el google chromiun, i uns quans programes més no relacionats amb el so.

Acabo de baixar-me desde el repositori el "gdm_3.0.4-0ubuntu11_amd64.deb" i l'he instal·lat, i ara ja està com estava abans.
Per cert ja funciona el só, i no he fet res més.

Bé, queda quan faig login amb un algre usuaria em surt el missatge "Could not update ICEauthority /home/laia/.ICEauthority"

Però com a mínim ara puc tancar l'ordinador.

Alguna idea més?

Aquest repositori que m'has pasat el podem afegir a origens del software?

Salutacions.

---

### Post by wgarcia on 2011-10-15
Per allò d'Iceauthority, mire si és un problema de permisos, cosa que t'ho podria arreglar entrant des d'una terminal:

sudo chown -R laia:laia /home/laia/.ICEauthority

I sí, pots agregar aquest dipòsit, és un dipòsit oficial d'Ubuntu com qualsevol altre.

---

### Post by akyra on 2011-10-15
Els usuaris segueixen donant el mateix problema, després de fer el que m'has dit, segueixo buscant.

Segueixo tenint problemes amb la bateria, en el moment que trec la corrent em diu que tinc la bateria en estat de carrega critica i que si no torno a endollar el corrent, no podrà a posar-se ni a ivernar. A les hores l'endollo i es posa a ivernar, sino ho faig directament s'apaga.

Deu nido amb aquesta actualització !!!!  :(

---

### Post by wgarcia on 2011-10-16
El problema de la bateria pot ser un error que he vist d'alguns models de portàtils. Potser podries obrir un informe d'error així queden registrats totes les especificacions del teu portàtil, ja el veuré al "launchpad". Et passo les instruccions per fer l'informe d'error que és molt fàcil, l'única dificultat és que s'ha d'escriure en la "lingua franca", l'anglès. 

1) Amb ALT F2 entra "ubuntu-bug gnome-power-manager"

2) Contesta totes les preguntes, t'obrirà el navegador i trigarà una estona fins que carrega els informes

3) Quan et deixi escriure al navegador, al "subject" posa

Battery incorrectly reported as exhausted when full and laptop shutting down

4) Al lloc per escriure "full report" posa

As soon as I unplug the laptop it closes down reported the battery as exhausted when it is fully charged. This started happening with the update to 11.10, under Natty it was working perfectly.

5) Lliura l'informe d'error

En quant al problema dels usuaris  perquè no obres un nou fil i descrius exactament què passa, ara no sé si el problema continua sent l'ICEAuthority, o no pots entrar en altres usuaris, o què.

---

### Post by akyra on 2011-10-16
Hola wgarcia,

Vaig de mal en pitjor.

Ahir a la nit després de fer el "sudo chown -R laia:laia /home/laia/.ICEauthority" als diferents usuaris, resultava que si en un podia entrar en l'altre no. Després vaig fer un "sudo chown -R usuari:usuari /home/usuari/.*" a on usuari es el nom de cada usuari, que ho havia vist el alguns forums per problemes semblants. El resultat el mateix.

Finalment de seguin fent aquestes proves, el meu usuari ja no entrava, només entrava el de la meva filla. 
Vaig optar per tornar a instal·lar l'ubuntu amb el live CD, però quan vaig acabar, i em demana nom d'usuari, en aquest cas el meu, tota l'estona em retornava al menú de login.
Ara sí que no ho entenc, suposo que dins del meu /home ha d'haver quedat alguna configuració extranya que no permet entrar.
En tot això no tinc internet, si no és que entri amb el liveCD com ara estic, així que cada vegada es complica més.

Dic, si la versió 11.04 m'anava bé, tornem-la a instal·lar. Doncs tampoc funciona, l'usuari entra però l'escriptori no es veu.

Bé ja estic una mica desesperat, i el que estic fent es copiant els arxius importants dels /home de cada usuari i si puc aquesta nit formatejaré també la partició /home, i faré una instal·lació completament neta.

Cal a dir que amb el liveCD de l'ubuntu 11.10 tot funciona perfectament.

No sé que et sembla wgarcia. tu que penses?

Gracies

---

### Post by wgarcia on 2011-10-16
Ara mateix és difícil dir què passa perquè has fet unes quantes coses i no és fàcil saber l'estat del sistema. També s'hauria de saber exactament quin tipus d'instal·lacions/actualitzacions has fet, com tens les particions, etc.

La incapacitat d'entrar a l'escriptori sembla un problema de controladors gràfics, potser els hauries de reinstal·lar un cop acabada la instal·lació.

En tot cas la instrucció que esmentaves per si un cas podria ser

```
sudo chown -R usuari:usuari /home/usuari
```

perquè potser el que té malament els permisos és el propi directori d'usuari. Aquesta instrucció fa propietari a l'usuari des del directori mateix i recursivament a tots els subdirectoris i fitxers.

---

### Post by akyra on 2011-10-16
L'unic que he fet ha estat una instal·lació des del liveCD.

Les particions tinc les primeres 3 per windows, i després una per la "/", una per la "swap" i una per la "/home", crec que una tipica configuració.

El que no acabo d'entendre com pot ser que amb el live CD vagi bé i amb la instal·lació no, suposo que deu agafar alguna configuració dels arxius de configuració del "/home".

El problema que tinc ara és que només puc fer alguna cosa des de la consola com a root, suposo que aquí podria fer alguna cosa, com donar d'alta els usuaris.

Intentaré això que dius tu, com ja t'he dit ho vaig fer amb "sudo chown -R usuari:usuari /home/usuari/.*" pels arxius ocults.

Bé, a veure si m'han surto, sinó formatejaré la "/home" a veure si val per alguna cosa.

Per cert amb el liveCD també hi ha el problema de la bateria.

Salutacions

---

### Post by fvilaubi on 2011-10-16
Hola Akyra,

jo acabo de passar de 11.04 a 11.10; i ho he fet amb amb l'automatisme del gestor d'actualitzacions. No m'ha reportat cap problema, i jo si puc iniciar les sessions amb altres usuaris.

Però he arribat a aquest fil venint del teu anterior, a mi tampoc en funciona ARA amb 11.10 la placa de so. Però te un comportament erràtic, vull dir que ara per exemple va. Puc apagar l'equip i deixa de funcionar, es veu molt ràpid doncs a la icona del altaveu de la barra superior hi ha dos guions. Si obro "paràmetres del so" a la pestanya "Hardware" NO hi ha cap placa!. Simplement deixant-ho estar, al cap d'una estona ara hi ha placa i tinc sò.

I l'altre efecte que tinc es una Web-cam que funcionava sense problemes des de la versió 9.10, ara torno a tenir els problemes de les versions anteriors: haig de desendollar l'USB i tornar a endollar per que reconegui la càmera.

Veig que haurem de tenir molta paciència amb la 11.10!!

---

### Post by wgarcia on 2011-10-17
akyra i fvilaubi, tot reconeixent que teniu diversos problems i és molt desesperant, convindria obrir fils un per un per a cada problema perquè sinó és fa molt difícil trobar els problemes, sempre i quan us interessi continuar mirant de solucionar-los.

Tornant al problema més seriós que és el problema d'arrencada de l'akyra, googlejant alguns diuen que tenen un fitxer que es diu Xauthority que no és propietat de l'usuari i que no els deixa entrar. Això explicaria perquè s'entra bé des del CD autònom, perquè aquí les propietats de fitxers no importen. Mira doncs si tens aquests fitxers i fes des d'una terminal:

sudo mv ~/.Xauthority ~/.Xauthority.backup
sudo service lightdm restart

---

### Post by wgarcia on 2011-10-17
Per al problema de so proveu el següent que alguns diuen que s'ho ha solucionat:

Esborreu ~/.pulse

aquest directori es recrea cada cop que s'inicia el sistema.

Reinstal·leu alsa-base, alsa-utils, esound-common, pulseaudio and pulseaudio-utils. Per exemple:

```
sudo apt-get install --reinstall alsa-base ... etc.
``` 

Reinicieu el sistema.

---

### Post by akyra on 2011-10-17
Bé, amb el "sudo chown -R usuari:usuari /home/usuari" executat com a root des de la consola vaig aconseguir alguna cosa, però no sé ben ve qué.
Després des de la consola he aconseguit instal·lar el gdm i he aconseguit entrar a la sessió.
Després m'he baixat els drivers de ATI (un arxiu run) i els he instal·lat.

Ara el problema que tinc és que no em surt ni la barra lateral de l'unity, i l'únic que tinc és el menú superior antic del gnome de Arxiu, Editar, Veure, Anar, Marcadors, Ajuda.

Bé com a mínim he aprés una mica més, però no sembla anar fi.

A mi si que em funciona el só i la camera web que porta el portatil.

Continaurem provant.

Adeu

---

### Post by wgarcia on 2011-10-17
Has provat entrar en mode recovery i donar la instrucció


```
sudo dpkg --configure -a
```

a vegades això acaba de arreglar els controladors gràfics.

---

### Post by akyra on 2011-10-17
Bé, després de seguir provant he decidit formatejar la carpeta /home també i he fet una instal·lació completament neta.

Com a resultat Ubuntu engega perfectament amb el lightdm i la bateria del portatil no em marca del tot bé, ja que em diu que només em queda un 18%, ja ho pasaré al launchpad.
El só funciona perfectamet i la gràfica també, ull !!, no he instal·lat els drivers privatius que per cert em diu que en tinc 2 tipus "Controlador de gráficos FGLRX propietario de ATI/AMD (actualizaciones post-lanzamiento)" i "Controlador gráfico FGLRX privativo par ATI/AMD", no sé quina diferencia hi ha en cada cas.

Si intento instal·lar el primer quan està casi acabant diu que no es pot, i el segon aquesta vegada no l'he provat, ja que en les anteriors instal·lacions era el que tenia instal·lat. 
Sabeu en quin cas hauria d'activar els controladors propietaris de ATI, com ho sé? Jo pel que veig em van bé els que venen per defecte.

Algú sap en quina fase estan aquest controladors per aquesta distribució? En alguns llocs posa que encara són una fase beta, en aquest link es parlar d'aquest mateix problema
[http://www.ubuntu-es.org/node/160268]("http://www.ubuntu-es.org/node/160268")

D'altra banda fvlaubi, crec que a tu t'anat bé perquè has fet un upgrade, i et deu haver conservat els drivers de l'ubuntu 11.04. Quan jo vaig fer el upgrade també m'anava bé la gràfica però tenia el problema del só.

Bé, el que sembla clar, és que ubuntu deu guardar la configuració que tenies en alguna carpeta del "/home" i quan instal·les ubuntu, encara que formategis la partició "/" ho segueix mantenint, sinó no sé com explicar-ho.

Us segueixo informant....

---

### Post by akyra on 2011-10-18
Una pregunta, com afegeixo el repositori "http://ftp.caliu.cat/" en els origens del software?

Gracies

---

### Post by fvilaubi on 2011-10-18
Jo ho he posat obrint "centre de programari del Ubuntu", Amb la finestra activa, puja el punter a la barra superior i tria "edita" > "fonts de programari" i a la pestanya "programari Ubuntu" hi ha "baixa de" que es un despleglable. Si trias "un altre" et traurà una llista i penjant d'Espanya (espero una indicació geogràfica i no política) hi trobes "ftp.caliu.cat".

Wgarcia, com pots veure al meu anterior escrit ja menciono que vinc d'un fil "no tinc so" que està tancat, i indica que segueix a aquest. 

Per actualitzar la situació, he acceptat l'actualització de paquets d'avui donat que en hi havia una del ALSA. Estic igual, engego l'ordinador i no tinc so, si demano "paràmetres del so" a la pestanya hardware no tinc cap placa.... però espero 15 o 20 minuts, sense fer rés més que pujar el tirador de volum de tant en tant, i quan es deixa, vull dir que em queda a mitja barra per exemple, si comprovo "hardware" ja surt la placa i el so em funciona correctament, puc reproduir qualsevol arxiu de so.

No se que fer, no sembla un problema hardware, per que quan funciona va bé i a més ha coincidit amb la 11.10. Sense fer rés reconeix el hardware i va.... 

Agrairé idees!!

---

### Post by wgarcia on 2011-10-19
fvilaubi, sempre pots obrir un fil nou amb un títol més indicatiu, ningún no trobarà res sobre el so en aquest perquè el títol és "No puc iniciar ubuntu amb altres usuari". A més segurament el teu maquinari serà molt diferent del de l'akyra.

---

### Post by akyra on 2011-10-19
A mi m'havia pasat el mateix amb el só, i va ser quan vaig canviar de lightDm a GDM que es va solucionar, però no crec que sigui la solució.

Actualment tinc una instal·lació fresca amb el lightdm que vé de "serie" però no tinc els controladors gràfics privatius instal·lats, crec que aquí és a on està el problema, encara que sembli que no té res que veure la gràfica amb el só, però jo no havia tocat res del só i es va solucionar amb el canvi d'entorn gràfic i sobretot no habilitant els controladors restringits de la gràfica ATI.

Adeu

---


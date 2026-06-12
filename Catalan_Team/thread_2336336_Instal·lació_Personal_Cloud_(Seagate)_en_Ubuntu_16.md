---
title: "Instal·lació Personal Cloud (Seagate) en Ubuntu 16.04"
date: 2016-09-07
forum: Catalan Team
---

### Post by annafur on 2016-09-07
Hola,
Necessitava un disc dur extern i he optat per Personal Cloud de Seagate. A la botiga em van dir que no hi havia problema per instal·lar-lo a Ubuntu, però quan he volgut baixar el  dashboard per fer còpies de les carpetes, no m'ha deixat. El Wine feia el procés de baixar els arxius, però a la meitat s'aturava i donava un missatge dient que no havia pogut descarregar els arxius.
Vaig escriure un missatge al mur de FB de  Seagate i m'han contestat que Personal Cloud està pensat per Windows i Mac, però que és possible instal·lar-lo a Linux.

 Estic molt contenta amb el funcionament d'Ubuntu, però els meus coneixement són bàsics. Algú em podria confirmar si hi ha manera d'instal·lar Personal Cloud i com fer-ho? Moltes gràcies.

---

### Post by wgarcia on 2016-09-07
Segons el que dius, sembla que vols fer servir el disc dur extern per fer còpies de seguretat. Per fer això, en la meva opinió el millor seria fer servir algun programa nadiu de linux, i no Personal Cloud a través de wine.

Però abans d'això, el disc es munta bé i es pot veure des de l'Ubuntu?

---

### Post by annafur on 2016-09-07
Gràcies wgarcia. Efectivament, l'objectiu és fer còpies de seguretat i també volia compartir arxius amb els portàtils que tenim. Wine m'ha permés baixar alguns arxius que em permeten veure els ordinadors en xarxa i accedir-hi, però per tal de poder fer còpies haig de baixar el Seagate dashboard i no em deixa.
Em podries informar de quin programa de Linux podría fer servir per tenir còpies al núvol i on puc trobar información per instal·lar-lo?.Gràcies

---

### Post by wgarcia on 2016-09-07
Perdona, ho miro una mica més, pensava que allò feia una còpia de seguretat senzilla d'un ordinador a un disc dur, però pel que expliques té més funcionalitats. Buscaré una mica per veure com funciona.

---

### Post by wgarcia on 2016-09-09
He llegit una mica més sobre Seagate Personal Cloud i entenc que el que fa és servir-se com a volum compartit a una xarxa on hi ha altres ordinadors. Per tant la primera pregunta és:

Es pot veure el volum del Seagate al navegador de fitxers? És a dir, si obres el navegador de fitxers, a la barra de l'esquerra es pot veure el Seagate?

---

### Post by annafur on 2016-09-12
Quan vaig a la xarxa veig el meu ordinador,  3 personal cloud (2 de compartiment de fitxers) i un user-PC i una carpeta 'xarxa windows'.L'administrador del Personal Cloud està instal·lat en un portàtil amb W10. T'envio imatge.[https://drive.google.com/a/xtec.cat/file/d/0B-cWXzp7KYMhWXJIUjZXaHpBR1U/view?usp=sharing ]("https://drive.google.com/a/xtec.cat/file/d/0B-cWXzp7KYMhWXJIUjZXaHpBR1U/view?usp=sharing")

Moltes gràcies!!

---

### Post by wgarcia on 2016-09-12
Llavors, si ho entenc bé, necessites una aplicació que faci còpies de seguretat de les dades del teu Ubuntu i les desi a un d'aquests volums Personal Cloud. Suposo que aquests volums són escrivibles des del teu Ubuntu.

L'aplicació que ve per defecte per a còpies de seguretat no et va bé? Aquí pots definir quines dades vols desar, on les vols desar (escollint les carpetes al Personal Cloud on ho vols desar) i la periodicitat. Es pot accedir anant a Paràmetres de Sitstema -> Còpies de seguretat, que està a la secció "Sistema".

---

### Post by annafur on 2016-09-12
Quan obro l'aplicació de Paràmetres de Sistema per fer còpies de seguretat i surt 'Ubicació d'enmagatzematge', hauria de veure 'PersonalCloud' per poder entrar a la carpeta on vull desar les dades, a més de les ubicacions: FTP, Recurs compartit del Windows,SSH, WebDAV, Ubicació personalitzada, però 'PersonalCloud' no surt. Curiosament si vaig a Xarxa puc veure la unitat de Personal Cloud (ho pots veure a la imatge que he enviat abans) i si entro puc veure la carpeta que he creat i desar fitxers, però això vol dir que hauria de copiar les carpetes i fitxers manualment. 

Pel que he vist en el portàtil on tenim W10, PersonalCloud té una aplicació anomenada 'Seagate Dashboard' que t'has de baixar i et demana quines còpies vols fer i on les vols desar. Vaig intentar baixar l'aplicació, però a meitat del procés el wine s'aturava i no ho l'he pogut instal·lar. Així que com el sistema no detecta el PersonaCloud, no puc fer còpies de seguretat.

Em sembla que finalment serà millor utilitzar un disc dur extern normal i corrent. Gràcies pel teu temps.

No s

---

### Post by wgarcia on 2016-09-12
Si cliques sobre "Recurs compartit del Windows", què et surt?

---

### Post by annafur on 2016-09-13
Si clico 'Recurs compartit de windows' surt una carpeta anomenada 'workgroup', si l'obro veig el meu ordinador, el portàtil i la unitat de PersonalCloud. Obro el 'PersonalCloud' i veig la meva unitat al núvol(si entro veig els arxius que he copiat manualment), la del portàtil, una unitat anomenada 'NetBackup' i ina altra anomenada 'Public'.

He intentat fer còpia de seguretat (veure enllaç : [https://drive.google.com/a/xtec.cat/file/d/0B-cWXzp7KYMhMXdmQ05RX2hsTzQ/view?usp=sharing](https://drive.google.com/a/xtec.cat/file/d/0B-cWXzp7KYMhMXdmQ05RX2hsTzQ/view?usp=sharing)), però no funciona.

---

### Post by wgarcia on 2016-09-13
No es pot veure l'enllaç, demana permís. 

Exactament quin error et dóna?

---

### Post by annafur on 2016-09-13
Ubicació de l'emmagatzatge -> (he triat ) Recurs compartit del Windows
Servidor -> (he escrit) PersonalCloud
Carpeta -> surt per defecte la meva carpeta local : home/anna/deja-dup
Nom d'usuari -> (escric el nom de la meva carpeta a PersonalCloud)
Nom del domini -> worksgroup

Vaig a resum -> Fes la còpia de seguretat ara -> Connectat al servidor - contrasenya (poso contrasenya creada per compartir home a PersonaCloud -> Surt finestra amb el missatge : Ha fallat la còpia de seguretat. No s'ha pogut montar el recurs compartit de Windows: el fitxer o directori no existeix.

Em sembla que ja he trobat on fallava. He canviat el nom de la carpeta i he escrit només ''anna'' i sembla que l'ha trobada. M'ha demanat la contrasenya que he posat al núvol i s'ha obert una finestra amb el missatge s'està fent còpia de seguretat. 

Deixo que vagi fent, a veure si és cert.

Moltes gràcies per la teva ajuda i interès!! Espero no haver de tornar amb aquest problema!

---

### Post by wgarcia on 2016-09-13
En tot cas assegura't que ha funcionat intentant restaurar alguna cosa de la còpia de seguretat, no sigui cosa que quan hagis de restaurar t'adonis que no ho estava fent bé.

Si s'arregla recorda't de marcar el fil com "Solved", sisplau, ho pots fer editant el primer missatge i escollint "Solved" a prefix.

---

### Post by annafur on 2016-09-13
Moltes gràcies. Continua sense funcionar. Tanco el fil. Moltes gràcies.

---

### Post by wgarcia on 2016-09-14
Llástima, deu ser un problema de permisos per escriure al disc. Si vols continuar investigant-ho podem continuar, en aquest cas no convé posar-li "Solved" al fil perquè en realitat no està resolt.

---

### Post by wgarcia on 2016-10-05
Potser una alternativa al Seagate Cloud: Netxgate Cloud que funciona amb l'Ubuntu

[https://goo.gl/J0sIYx](https://goo.gl/J0sIYx)

---


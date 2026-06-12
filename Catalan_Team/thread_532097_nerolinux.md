---
title: "nerolinux"
date: 2007-08-22
forum: Catalan Team
---

### Post by muleta on 2007-08-22
Mireu quina troballa: [http://www.nero.com/esp/nerolinux](http://www.nero.com/esp/nerolinux).

El gran cremador de video té una versió per a Linux!!.

Fins ara no havia trobat cap programa que em permetés codificar i grabar películes desde Linux, només dades.

Però.. .:(  no es deixa instal·lar. Mireu què em diu en la captura. Us asseguro que no tenia cap altra aplicació en funcionament fins que he engegat el navegador. Fins i tot he reiniciat, per si s'havia quedat alguna cosa a mitges. :confused:

Què puc fer?.

---

### Post by lluisanunez on 2007-08-22
Clarament, algun procés s'ha quedat engegat. Mira de fer:
```
sudo apt-get clean
```

De totes maneres, hi han programes a linux iguals o millors. Per exemple, K3B

---

### Post by muleta on 2007-08-22
Gràcies per la informació sobre K3D. Estic patejant el google per ampliar-la i descobreixo que, a part de no estar preparat per a Ubunto (cosa que ensenyen com resoldre), el pitjor és que no passa de ser un programa com tots els que havia trobat fins ara: grabador de CD i de DVD de dades.

Enlloc no diu que tingui tots els codecs necessaris per cremar películes de qualsevol format ni que pugui realitzar les múltiples funcions que brinda el Nero.

Seguiré la teva altra indicació i provaré el Nero. Jaus ho explicaré.

---

### Post by muleta on 2007-08-22
Com que m'he compromés a explicar-ho, us dic que els meus intents d'instal·lar nerolinux han esdevingut un fracàs total.

Hauré de seguir el consell de Papapep i instal·lar un doble navegador, però m'esperaré a veure si algú ha viscut experiències semblants i n'obtinc més informació.

També he fet de tot per instal·lar el K3B, com introduïr un munt de programes, fitxers que hi manquen, etc. i tampoc no me'n he sortit.

Però encara no em deixo acoquinar ](*,) per les resistències de Linux, m'hi vull capbussar més a fons i assegurar-me bé de que no té possibilitats semblants a les que m'oferia el Win :evil: , abans de marxar.

Veig que és difícil trobar i activar controladors, executar algunes aplicacions que em resulten imprescindibles i que gairebé no hi ha programes per a les tasques que he de realitzar... però encara no vull admetre que Ubuntu  sigui un SO poc útil. Em queda molt per aprendre i per descobrir.

M'haureu d'aguantar una temporada més #-o perque us bombardejaré incansablment amb preguntes, queixes desesperades, cabrejos i lamentacions. [-o< Si, al final, no n'aprenc i us he de deixar, faré la meva crítica constructiva de tot plegat.

---

### Post by xoldy on 2007-08-22
Hola muleta bona nit, jo fa poc també que estic movent-me per Ubuntu, però ja no faig servir el güindous només que a la feina (on estic obligat).

Aquesta versió de Linux que estàs provant d'instal·lar penso que no és gratuïta. En van treure una fa un temps que si que ho era. El vaig instal·lar però no te res a veure amb el que porta per l'altre sistema. Només és el burning.

Com a nouvingut de Linux et puc dir que el que costa més és el canvi de mentalitat d'un sistema a l'altre. És més laboriós al principi perquè has d'anar trobant tot el programari "equivalent" al que coneixies, amb la limitació de temps que tenim tots.

En aquest forum jo estic aprenent molt, i a més pel que he vist és en el que més es contesta als dubtes. Ostres quin rotllo t'he fotut.

El k3b me l'he instal·lat avui llegint aquest fil. No en puc opinar encara, però te molt bona pinta. He fet servir el GnomeBaker i va molt bé.

Per Aplicacions+Afegeix/Elimina pots instal·lar fàcilment el programari. (Per anar entrant, és la manera més fàcil d'instal·lar paquets.

Endavant amb l'Ubuntu.
cada vegada més.

---

### Post by muleta on 2007-08-22
Hola Xoldy,

no, el nerolinux no és gratuït, és d'avaluació, tens raó. Això vol dir que, pasat un temps, t'has de buscar la vida.

Però si no té res a veure amb la meravellosa suite que coneixem, ja m'animo a deixar-ho córrer. Tot i que és el burning allò que no trobo.

No has tingut cap mena de dificultat per instal·lar el k3b?. Jo l'he agafat del block d'un noi argentí que prometia ajudar molt però anava anomenant la quantitat de fitxer que s'havien d'instal·lar prèviament per complementar els que falten a l'Ubuntu per ser Gnome. M'hi he perdut i el meu pc ha començat a fer el ximple. Quan em recuperi de l'ensurt i hagi llegit tot el tutorial de l'intèrpret de comandes d'en Papapep :-k , ho tornaré a provar.

És veritat que en aquest forum hi ha molta correcció i nivell.

Gràcies pels teus comentaris.

---

### Post by CarlesOriol on 2007-08-23
No has fet sudo apt-get install k3b ? N'hi ha prou amb això.

Per cert per fer dvds de video pots usar eines com dvdauthor mandvd o qdvdauthor.

El k3b a més te la opció de crearte cds/dvds em format emoviex. Un cd amb un mini sistema operatiu per veure pelis + la peli. Oi que això no ho havies vist mai? ;-)

També pots preparar els formats de video amb eines tipus kdenlive (tipus premiere) per despres passar-ho al k3b.

No pateixis que ho pots fer tot amb programari lliure. No val la pena de canviar per usar programes privatius ja que llavors no guanyes res.

---

### Post by muleta on 2007-08-23
Hola Carles,

a veure si, al final, m'agradarà Linux...

Però ho provo ara i em respon: 

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

Ho faig i em respon que hauria de ser superusuari, per fer aquesta mena de coses. I, de moment, ja en tinc ben bé prou amb mirar de ser usuaria d'estar per casa.

Hauria estat bé que s'instalés de la manera que em déies.

M'he passat la nit connectant a llocs on donaven instruccions i descarregaven fitxers necessaris mitjançant enllaços. Dec haver empastifat el disc de dalt a baix. Potser que busqui alguna eina per fer-ne una bona neteja.

Per cert, algú sap què és "l'Avahi"?. Em diu que es desconnecta perque no li agrada el domini de la meva xarxa.

---

### Post by lluisanunez on 2007-08-23
Hola,
ser superusuària és tan fàcil com prefixar amb "sudo" les teves comandes. O sigui:
```
sudo dpkg --configure -a
```
et demanarà el password i et farà la feina.
Prova-ho!
I, si vols un consell, pren-t'ho amb més calma. No executis tot el que vegis pel google, intenta treballar amb les aplicacions de la distribució, i fes-ho  amb una mentalitat oberta: al món de Windows estan de moda els programes que fan milers de coses, tipus suite. Al món del programari lliure, es porten molt més els programes que fan una sola cosa, però la fan molt bé. Això sovint vol dir que en comptes d'un sol programa en fas servir dos o tres, però faran exactament el que tu vulguis. No busquis els equivalents de W. exactes, sinó la manera linux de fer les coses.

---

### Post by muleta on 2007-08-23
Hola Lluïsa,

La única diferència és que he de sortir de la meva sessió i tornar a entrar com a root?. Després de que s'executi l'ordre dec haver de tornar a sortir per entrar amb el meu nom d'usuària...

Prenc nota dels teus consells. A mesura que vagi descobrint qualitats en el Linux, aniré canviant de mentalitat. Però és que vosaltres en sabeu molt i la majoria sou professionals de l'informàtica, JO NO.  :cry:

---

### Post by lluisanunez on 2007-08-23
No, no, això d'entrar en una sessió gràfica com a root no ho has de fer, podries fer molt de mal sense adonar-te'n.  Justament SUDO serveix perquè s'apliquin els drets de root ** només** a la comanda que estàs entrant. Equival a dir "fes, amb drets de superusuari, tal i tal cosa".
Aquest és un dels avantatges del terminal: poder precisar moltes coses en una sola línia. 
Sense canviar de sessió, obres un terminal, i entres les comandes, i només quan sigui necessari les prefixes amb SUDO.

Ah, i perquè no pensis que estàs sola entre informàtics: jo sóc bibliotecària :-)

---

### Post by papapep on 2007-08-23
> La única diferència és que he de sortir de la meva sessió i tornar a entrar com a root?.
No, com bé t'ha dit la Lluïsa, _només_ et cal afegir "sudo" davant la comanda que vols executar (sempre que li calguin permisos de superusuari, sinó no cal).

> Però és que vosaltres en sabeu molt i la majoria sou professionals de l'informàtica, JO NO. 

Això tampoc és cert :) 

Aquí hi ha, evidentment, llicenciats en informàtica, però també hi ha usuaris molt experts a base d'anys de suar tinta quan Linux no era tan amigable i simple com ara, usuaris que fa un temps que són a aquest món i se'n van sortint, i d'altres que fa dos dies que han començat i suen com desesperats (i tots els nivells intermitjos).
La única diferència que tenen tots respecte tu és que tu encara no saps gaires coses i la resta, en diferents nivells, si.

O sigui, que la dita "Al regne dels cecs el guenyo és el rei" és el que et passa a tu ;-)

---

### Post by muleta on 2007-08-23
Ah, sí, ara sí!.

S'ha posaat a llegir paquets del K3B  i, de sobte, m'ha obert una pantalleta blava demanant-me l'acceptació de condicions per a instal·lar JAVA  (una de les coses que havia estat intentant instal·lar infructuosament). Accepto, llegeixo i accepto... i RES, no es mou.

M'he quedat amb l'acceptació pendent en pantalla. Què faig?.

---


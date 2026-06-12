---
title: "UbuntuStudio 14.04.3 i Windows 7 instal·lats, s'obre només W7"
date: 2015-12-01
forum: Catalan Team
---

### Post by shan2 on 2015-12-01
Hola!


Per primera vegada instal·lo Ubuntu! Perdoneu si he fet alguna barbaritat, però no me'n surto ni trobo informació que m'ajudi.
Acabo d'instal·lar Windows 7 64 bits de nou en un disc SSD i he intentat instal·lar UbuntuStudio 14.04.3 en un altre disc físic. El procediment ha sigut el següent, després de consultar informació diversa:
- He baixat la ISO i l'he gravada en un DVD tot comprovant si hi havia errors.
- He obert Ubuntu des del DVD i GParted.
- He formatejat a ext4 la partició del disc dur on vull instal·lar Ubuntu. És un disc diferent del disc on hi ha W7.
- He reiniciat W7 per comprovar que tot estava bé.
- He reiniciat des del DVD i he triat instal·lar.
- He triat català, no connectar-me (tinc wifi), no actualitzar ni baixar programes de terceres parts, destriat els paquets de generació d'àudio i vídeo.
- En les opcions finals d'instal·lació he triat "Alguna altra cosa" per fer les particions a mida, si triava mantenir W7 m'instal·lava Ubuntu al mateix disc que W7 i no vull això, de moment. En qualsevol cas això últim ho he provat i funciona, en arrencar l'ordinador sortia la finestra d'Ubuntu per triar W7 o Ubuntu. Però ara per ara prefereixo reservar l'SSD per Windows.
- He fet les particions tal i com les podeu veure al fitxer adjunt. Val a dir que no he sabut trobat informació clara sobre si havia de crear la partició pel boot i a on, o bé no crear-la i confiar que tot anés bé triant el disc corresponent a "dispositiu on instal·lar el carregador". Això últim, en tot cas, ho he fet, triant la partició creada pel boot (el boot és el carregador, oi? :confused:)


[ATTACH=CONFIG]265863[/ATTACH]


He seguit amb el procés d'instal·lació sense més i tot ha anat bé, en principi. Però quan reinicio l'ordinador s'inicia W7, només. Si reinicio des del DVD i me'n vaig a instal·lar detecta que Ubuntu està instal·lat.


A veure si em podeu donar un cop de mà. M'agradaria poder triar entre els dos SO. Per demanar, seria la bomba que sortís l'opció de triar durant uns pocs segons i que, si no faig res, s'iniciés W7. Espero, en un futur proper, fer-ho a l'inrevés!

Us deixo amb una imatge dels discos durs, tal i com es veuen des de W7, i amb la info del sistema, per si de cas. Salut i gràcies!

[ATTACH=CONFIG]265864[/ATTACH]

Sistema operativo       Microsoft Windows 7 Home Premium
Versión                      6.1.7601 Service Pack 1 Compilación 7601
Descripción adicional del sistema operativo     No disponible
Fabricante del sistema operativo    Microsoft Corporation
Nombre del sistema    SHAN-PC-01
Fabricante del sistema    Gigabyte Technology Co., Ltd.
Modelo del sistema    P35-DS3L
Tipo de sistema    PC basado en x64
Procesador    Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz, 2400 Mhz, 4 procesadores principales, 4 procesadores lógicos
Versión y fecha de BIOS    Award Software International, Inc. F9, 19/06/2009
Versión de SMBIOS    2.4
Directorio de Windows    C:\Windows
Directorio del sistema    C:\Windows\system32
Dispositivo de arranque    \Device\HarddiskVolume1
Configuración regional    España
Capa de abstracción de hardware    Versión = "6.1.7601.17514"
Nombre de usuario    SHAN-PC-01\SHAN
Zona horaria    Hora estándar romance
Memoria física instalada (RAM)    8,00 GB
Memoria física total    8,00 GB
Memoria física disponible    5,27 GB
Memoria virtual total    16,0 GB
Memoria virtual disponible    12,5 GB
Espacio de archivo de paginación    8,00 GB
Archivo de paginación    C:\pagefile.sys

---

### Post by wgarcia on 2015-12-01
Perquè arrenqui l'ubuntu en arrencar l'ordinador, un programa que es diu "grub" (que és el que dóna el menú que vas veure quan vas instal·lar Ubuntu al disc on tens el Windows) ha d'estar instal·lat al disc des d'on arrenca l'ordinador. Entenc que aquest dispositiu és el /dev/sda. Però ara mateix segons expliques ha quedat instal·lat al /dev/sdb, i per tant quan inicies des del dic principal, Ubuntu no es veu. 

Entenc que la captura de pantalla que mostres del gparted és arrencant des del DVD, oi? perquè ara mateix no pots arrencar l'Ubuntu des del segon disc, i per tant no pots accedir a la instal·lació que has fet de l'Ubuntu.

Tampoc entenc del tot el que es veu al gparted. Es veu una partició lògica /dev/sdb2, i dins d'ella una /dev/sdb6 amb 18.63 Gigues, una /dev/sdb7 amb 190 Megues (una partició petita), una altra /dev/sdb8  amb 37.91 Gigues. Aquestes tres estan formatejades amb el format de Linux, ext4. Després hi ha una altra /dev/sdb5 amb 127.71 Gigues i format usat per Windows, ntfs. Està tot molt desordenat i s'hauria de saber què són aquestes diferents particions. En tot cas sembla com si a la instal·lació d'Ubuntu li haguessis donat massa poc espai , 18 + 37 gigues. Has separat el /home del /root? Si no saps de què parlo segurament no ho has fet (és una opció que es pot fer per tenir separades les dades d'usuari dels fitxers del sistema, per si reinstal·les no necessites recuperar-les). 

Un altre problema que veig és que si tens 8 gigues de RAM el swap hauria de tenir uns 16 gigues, sempre és convenient posar el doble del RAM que tens (el swap és un espai de Linux on el sistema pot escriure si exhaureix la memòria RAM, per seguir treballant).

---

### Post by shan2 on 2015-12-02
Em sembla que ja ho entenc. Aleshores crec que hauria de:

- eliminar la partició dev/sdb7, que és la que havia creat pel boot
- tornar a instal·lar Ubuntu sense crear una partició pel boot
- quan em pregunti [COLOR=#000000]"dispositiu on instal·lar el carregador" li dic a dev/sda1, que és el que té l'etiqueta W7, es pot veure en aquesta imatge:

[/COLOR][ATTACH=CONFIG]265884[/ATTACH][COLOR=#000000]

També és possible que en comptes de resinstal·lar es pugui reparar, però no tinc ni idea.

Respecte les particions, he seguit les recomanacions de molts fòrums i tutorials. He fet particions ext4 pel swap (1.86 GiB, sdb1), root (18.63 GiB, sdb6) i home (37.91 GiB, sdb8). sdb7 és per boot, que no l'havia de crear, i sdb5 (ntfs) és un espai que reservo per Windows per altres coses.

Pel que fa al swap he llegit que amb 8 Gb de RAM n'hi havia prou amb reservar-li 2 Gb. Però era una recomanació general. No sé si per UbuntuStudio, que necessitarà molta RAM (crec que faré servir sovint el GIMP i el Raw Therapee), caldria més espai pel swap.

Bé, ja em direu què en penseu de tot plegat, si ara vaig pel bon camí.

Gràcies!

[/COLOR]

---

### Post by wgarcia on 2015-12-02
Separar la partició /root de /home com deia va bé, però no és una cosa que algú que s'inicia en Linux fa habitualment, mostra que tens futur a Linux si ja ho has sabut fer. 

Per a la instal·lació de l'arrencada, estic d'acord, a /dev/sda. Es podria recuperar la teva instal·lació actual, però potser com tens tot a un disc extern millor refer-la ara que ja tens més informació.

Quan a la mida del swap, la pàgina que ho explica és:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

El paràgraf rellevant diu:

Per a sistemes més moderns (més de 1GB), el vostre espai de swap hauria de ser com mínim mínim igual a la mida de la vostra memòria física (RAM) "si useu hibernació", en cas contrari necessiteu un mínim de arrel quadrada del RAM arrodonida com a mínim i un màxim del doble de la mida del RAM. El únic inconvenient de tenir més swap del que fareu servir en realitat és l'espai de disc que li reservareu.

---

### Post by shan2 on 2015-12-03
Moltes gràcies, ja funciona tot plegat!

---

### Post by wgarcia on 2015-12-03
Solem marcar els fils amb [Solved] per deixar per futures consultes, ho pots fer editant la teva primera intervenció i escollint aquesta opció a un desplegable que es veu a dalt de l'àrea per entrar el text.

---


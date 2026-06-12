---
title: "Ubuntu 18.04 no reconeix partició amb Windows 10"
date: 2018-11-03
forum: Catalan Team
---

### Post by albeitar on 2018-11-03
Bones,

M'inicio en aquest fòrum dels ubuntaires amb la següent consulta que us plantejo tot seguit.

Intento instal·lar Ubuntu 18.04 en el portàtil Lenovo Ideapad 100-15IBD ([https://www.notebookcheck.net/Lenovo-IdeaPad-100-15IBD-Notebook-Review.158803.0.html](https://www.notebookcheck.net/Lenovo-IdeaPad-100-15IBD-Notebook-Review.158803.0.html)) i no me'n surto.

Vull fer una instal·lació en què Ubuntu convisqui amb Windows en el mateix disc dur (instal·lació dual) però l'instal·lador d'Ubuntu del pendrive que he creat no detecta el Windows 10.

L'instal·lador, en el pas de Tipus d'instal·lació, em diu 'Aquest ordinador no duu cap sistema operatiu que s'hagi detectat. Què voleu fer?'

El disc dur és d'un TB i amb l'administrador de discos de Windows he alliberat espai en la C. Així que queden disponibles mes de 460 GB. L'instal·lador d'Ubuntu detecta les particions del disc però no em dóna l'opció de fer la instal·lació dual.

Les particions detectades per Ubuntu són les següents:
sda1 (FAT32, 277 MB; es la partició sistema EFI)
sda2 (unknow, 16 MB)
sda3 (ntfs, 487 GB; es la /C: on està Windows 10 i l'arrencada)
espai lliure (466 GB; espai alliberat de C; per tal d'instal·lar Ubuntu)
sda4 (ntfs, 27 GB; es la /D: on el recovery del Lenovo)
sda5 (ntfs, 1GB)
sda6 (ntfs, 17,7 GB)
sda7 (ntfs, 1 GB)

No he intentat una instal·lació en l'espai lliure que queda (creant-ne una nova participació) perquè no domino gaire la creació de particions i no em refio que Grub em permeti després arrencar la partició del Windows 10.

A mes, tinc por de carregar-me la BIOS. He llegit que en alguns Lenovo Ubuntu 17.10 corrompia la BIOS. 
[https://m.genbeta.com/linux/si-querias-instalar-ubuntu-en-tu-portatil-lenovo-mejor-no-lo-hagas-te-puede-danar-la-bios](https://m.genbeta.com/linux/si-querias-instalar-ubuntu-en-tu-portatil-lenovo-mejor-no-lo-hagas-te-puede-danar-la-bios)

Desconec si la 18.04 ha subsanat la incidència detectada amb la 17.10.

Aixi que, teniu alguna idea de com fer una instal·lació dual? Què em recomaneu que faci?

Moltes gràcies.

---

### Post by wgarcia on 2018-11-05
He vist que ho has marcat amb "Solved". Ja està resolt?

---

### Post by albeitar on 2018-11-09
No, no está resolt. 

L'usb amb Ubuntu 18.04 s'ha creat en mode GPT per a UEFI atès que Windows 10 està instal·lat en la màquina d'aquesta manera.

No m'atreveixo a fer la instal·lació dual predeterminada que em proposa l'instal·lador: no em reconeix Windows 10 i em diu si vull instal·lar Ubuntu amb 'Windows boot manager' que es troba instal·lat en la participació UEFI que ve de fàbrica amb el portàtil.

De moment, no  em refio de fer una instal·lació manual perquè no sé on he d'instal·lar grub. No vull cagar-la...

---

### Post by wgarcia on 2018-11-11
Crec que és segur fer la instal·lació que proposa l'instal·lador. Fes un disc de recuperació del Windows per si l'has de recuperar després de la instal·lació, però jo crec que funcionarà correctament.

---

### Post by albeitar on 2018-11-11
Així ho faré després de fer-me un disc de recuperació per al Windows 10.

Ja us diré com m'ha anat.

Moltes gràcies per la vostra paciència i col·laboració.

---


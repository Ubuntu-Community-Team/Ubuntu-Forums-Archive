---
title: "Problemes alhora d'instal·lar Xubuntu en portàtil Acer P256-M"
date: 2021-11-11
forum: Catalan Team
---

### Post by astarothvg on 2021-11-11
[FONT=Ubuntu]Hola a tothom, escric per demanar ajut en un tema que m'ha passat el qual trobo força estrany.[/FONT]
[FONT=Ubuntu]
La cosa va començar quan vaig decidir canviar el vell disc dur de 2.5  per un ssd, un cop fet el canvi vaig baixar-me la imatge del Lubuntu 21.10 per passar-la a usb i seguidament instal·lar.[/FONT]
 [FONT=Ubuntu]El portàtil és un Acer model TMP256-M-35X amb el processador intel i3, només te una connexió de disc dur però vaig canviar el lector de DVD per un adaptador i ara hi ha 2 discs durs, un amb uindous i l'altre que és en el que vull instal·lar linux.[/FONT]
 [FONT=Ubuntu]
La distro live va arrencar bé, després de provar que tot el hardware fos compatible vaig procedir a la instal·lació i un cop fet, reinici i bé, el grub detecta el uin i la màquina va fluida i tot sembla correcte.[/FONT]
 
 [FONT=Ubuntu]Al cap d'uns dies vaig baixar-me la imatge del Xubuntu, la vaig provar a virtualbox en el pc de escriptori i la veritat és que em va agradar moltíssim, més que el lubuntu així dons com que encara no havia començat a afegir programari al so del portàtil vaig pensar, la provarem.[/FONT]
 
 [FONT=Ubuntu]Un cop cremada la imatge al pendrive torno a fer tota la litúrgia i quan arriba el moment de triar el disc on instal·lar es glaça, cancel·lo la instal·lació obro gparted i veig que els discs si que els veu, no entenc res de que està passant.
[/FONT]
 [FONT=Ubuntu]Començo a buscar per la web a veure si trobo amb una solució i el que em trobo és que diuen que la bios d'aquests portàtils és una mica xunga a l'hora de instal·lar qualsevol cosa fins i tot el uindous 10!, al fòrum d'acer hi trobo una possible solució hi diu: [/FONT] 
 [FONT=Ubuntu][FONT=Ubuntu][SIZE=2]"[/SIZE][/FONT][FONT=Ubuntu][SIZE=2]Acceda a la BIOS, vaya a la pestaña MAIN, presione CTRL + S y cambie el modo sata a AHCI. Debe crear una contraseña en SETSUPERVISORPASSWORD y deshabilitar SECUREBOOT.[/SIZE][/FONT][FONT=Ubuntu][SIZE=2]"[/SIZE][/FONT][/FONT]
       [FONT=Ubuntu]un cop fet això torno a provar i ... res, altre cop el mateix.[/FONT]
 
 [FONT=Ubuntu]He repassat els passos que fa la instal·lació i he detectat que el pas de triar on instal·lar se'l salta, després d'això he provat de tot, canviar els discs de lloc, alhora de crear l'usb fer-ho en gpt en ves de mbr, particionar el disc dur en gpt també i res m'ha donat resultat.[/FONT]
 
 [FONT=Ubuntu]I ara ve la pregunta del milió, per què Lubuntu si i Xubuntu no?. [/FONT] 
 
 [FONT=Ubuntu]Un altre cosa que m'ha cridat l'atenció és que quan carrega el sistema el plymouth (l'animació) en el cas del Lubuntu hi apareix el logotip d'Acer i en Xubuntu no, no se potser alguns portàtils de la marca venien amb Lubuntu pre-instal·lat i per això no dona problemes alhora de fer-ho de manera gràfica, o el Lubuntu porta controladors que Xubuntu no.[/FONT]

 [FONT=Ubuntu]M'agradaria poder fer la instal·lació de manera  gràfica, recordo que algun cop havia provat d'instal·lar en mode terminal i a demès de ser força complicat si t'equivoques en un pas adéu, tot  s'envà al carall.[/FONT]

 [FONT=Ubuntu]Per acabar 2 coses, la primera perdoneu pel rotllo he intentat explicar-me de la manera més precisa possible i la segona, si m'estic equivocant de secció on plantejar el meu dubte si us plau digueu-me on adreçar-me i esborraré el post.

Salut a tots!
[/FONT]

---

### Post by wgarcia on 2021-11-12
El missatge és perfectament apropiat.

Has provat de tornar a instal·lar el Lubuntu? Sí que pot ser que l'instal·lador del Lubuntu porti alguna configuració gràfica que no porti el Xubuntu, i això fa que no doni problemes. Dic tornar a instal·lar el Lubuntu per assegurar-se que sí que ho instal·la bé.

Un cop instal·lat el Lubuntu, penso que et pots instal·lar el paquet xubuntu-desktop i et deixaria els dos escriptoris per arrencar. Considerant que són dels escriptoris més o menys lleugers, no seria massa problema l'espai que ocupa el Lubuntu si no el fas servir.

Fins i tot pots instal·lar l'Ubuntu normal i després instal·lar xubuntu-desktop, però en aquest cas sí que potser estaràs malbaratant espai. En aquesta pàgina en anglès explica com instal·lar xubuntu-desktop sobre l'ubuntu normal:

[https://itsfoss.com/install-xfce-desktop-xubuntu/](https://itsfoss.com/install-xfce-desktop-xubuntu/)

---

### Post by astarothvg on 2021-11-16
Hola wgarcia d'entrada gràcies pel interès,
dons si vaig tornar a instal·lar Lubuntu i sense cap problema alhora de escollir disc, sembla com si fos un bug en el instal·lador tant del Xubuntu com d'Ubuntu, si també em vaig baixar la imatge d'ubuntu i ho vaig provar sense resultat.

Bé us informo que a la fi ho he _SOLUCIONAT_  no volia haver de fer una instal·lació mínima per por de que fos massa complicada però res d'això, vaig baixar-me el [mini.iso]("https://askubuntu.com/questions/1233746/download-ubuntu-minimal-iso-20-04lts") i la instal·lació segueix sent gràfica només que no pots provar l'escriptori però el procés és força intuïtiu. 

Puntualitzar que l'usb el vaig haver de crear sota uindous amb el programa rufus ja que primer ho vaig fer amb l'eina de linux i ni el veia.

Les opcions a tindre en compte alhora de fer l'arrencador son:
Esquema de partició: GPT   Sistema de destí: UEFI (no CSM)
Fat 32 i deixar la mida del clúster per defecte.

Un cop fet això vaig comprovar que engegava sense problema i tot va anar rodat, una vegada instal·lat xubuntu i abans de instal·lar res més vaig obrir la configuració de repositoris i li vaig dir que volia pujar a una versió més nova i així vaig actualitzar a 21.04 i un cop fet a 21.10, de moment cap problema tot funciona correctament.

Salutacions i gràcies.

---

### Post by wgarcia on 2021-11-17
Perfecte. Si tens un moment, marca el missatge amb el "Solved" perquè quedi de referència per  a qui pugui trobar-se amb el mateix.

---


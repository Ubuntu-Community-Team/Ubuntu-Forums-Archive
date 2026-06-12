---
title: "Reinstalar ubuntu 8.10     AJUDA PER FAVOR"
date: 2009-03-01
forum: Catalan Team
---

### Post by juanal on 2009-03-01
hola a tots, vaig instalar el ubuntu 8.10 al meu ordinador portatil asus M50CVseries i tot en funcionava correctament menys el sò, vaig averiguar que la tarjeta de so del portatil es ua realteck ALC663 i que pe a ferla funcionar existien uns drivers de la paguina web de realteck pera que funcionara els vaiginstalar pero ara el sistema operatiu no marranca pose el nom dusuari i la contraseny i es que da aturat, nomix no el fons de pantalla ni res, e pensat en tornar a instalar el ubuntu pero?
tinc que formatejar el ordinador??? tinc tambe instalat el vista per cuestions de garantia i tal, pero puc reintalar ubuntu sese afectar a vista damunt del mateix ubunu? puc formatejar soles la part del ubuntu?? algu sap si per a instalar els drivers de realteck avans tinc que fer algo per a que en funcione be i no se me penje el sistema operatiu? gracies

---

### Post by sianeu on 2009-03-04
Comença a instal·lar com el primer cop. Quant et demani les particions li dius que vols fer-ho manual. A la següent pantalla senyales la partició del actual linux (serà la ext3) i li dones al botó editar: a la nova finestra que sortirà indiques el sistema de fitxers ext3 i el punt de muntatge /. I ja està, tornarà a instal·lar-lo al mateix lloc.

Peró perdut per perdut, per que no intentes desinstal·lar el driver que has instal·lat (entrant en mode consola, la segona opció del menú del grub). Després podria ser que el problema fos que abans d'instal·ar el nou driver hagessis de desinstal·lar el que hi tens per defecte.

Salut

---

### Post by juanal on 2009-03-04
> **sianeu said:**
> Comença a instal·lar com el primer cop. Quant et demani les particions li dius que vols fer-ho manual. A la següent pantalla senyales la partició del actual linux (serà la ext3) i li dones al botó editar: a la nova finestra que sortirà indiques el sistema de fitxers ext3 i el punt de muntatge /. I ja està, tornarà a instal·lar-lo al mateix lloc.

Peró perdut per perdut, per que no intentes desinstal·lar el driver que has instal·lat (entrant en mode consola, la segona opció del menú del grub). Després podria ser que el problema fos que abans d'instal·ar el nou driver hagessis de desinstal·lar el que hi tens per defecte.

Salut

Merci, vaig instalar altra vegada el ubuntu i el que vaig fer va ser instalar els ultims paquets alsa a la paguina alsa, al fer aÇo nomes se me sentia en OSS aixi que vaig ficar els seguents comandos:

kill pulseaudio

sudo alsa force-reload

i per ultim
 alsamixer -Dhw
i mntava els parametres i al canviar a alsa ja en funcionava tot els sorolls del sistema, el que pasa es que cada vegada que reinicie el ordinador tinc que repetir estos ultims pasos, magradaria saber com puc guardar la ultima configuració. merci

---

### Post by sianeu on 2009-03-05
Crec que has de modificar el fitxer de configuració, però no en se prou per dir-te cóm.

El que sí t'aconsello es que obris un nou fil per aquest tema, que ja no te res a veure amb la reinstal·lació, si no vols bronques del INMENS (pppp) :D:D

---

### Post by juanal on 2009-03-06
ja esta ja en funciona tot com deu anar, era més facil nomes tenia que guardar la configuracio actual abans de apagar el ordinador  merci per la ajuda

---

### Post by Haliotis on 2009-03-24
hola, sento allargar aquest fil amb el tema secundari. Peo és molt simple, i potser obro un altre fil ja resolt.
A mi també em passa axiò que haig de retocar els volums de l'alsa cada vegada que inicio ubuntu. I dius que simplement es tracta de guardar al configuració abansd e tancar l'ordinador... però com es fa això?
merci :D

Max

---


---
title: "Actualitzacio Feisty: sistema fotut"
date: 2007-03-30
forum: Catalan Team
---

### Post by sianeu on 2007-03-30
L'ultima actualització del Feisty m'ha deixat sense poder entrar al sistema. Desprès d'escriure la contrasenya intenta entrar però no pot i em torna al login, en un bucle. 

Desprès, tant si entro en sessió de cónsola a prova de fallades, com a recovery mode des del grub, no em deixa reinstal·lar el driver de Nvidia, que fins ara havia estat la meva solució. Diu: "sh: no pot obrir NVIDIA-.................run"

He pensat que potser s'havia fet malbé el fitxer, així que he creat una carpeta i he copiat a dins una copia del fitxer que tenia a una altre partició. He entrat a la carpeta i l'he executat, amb el mateix resultat.

Havia borrat tots els image-kernels anteriors menys el primer. He intentat entrar i m'ha donat error de X recomenant reinstal·lar el driver de Nvidia. Això es el que sempre em passava en les actualitzacions del kernel, i he pensat que anava bé. Però no, també ha donat el mateix error: sh no pot obrir el fitxer.

No es greu per que ho tenia tot salvat. Puc tornar a reinstal·lar el sistema. Però si  hi ha algú que pugui oferir-me una possible solució, voldria intentar-ho.

Si ningú diu res provaré a sobreescriure el xorg.conf, del que en tinc una copia. No ho tinc clar, per que sé que es un dels fitxers actualitzat junt amb d'altres associats a ell i penso que canviar-lo només a ell pot embolicar el tema encara més. A part que el fet de no poder reinstal·lar el driver de Nvidia sembla senyalar a un altre banda.

No sé, els savis direu.....

Salut

---

### Post by orestesmas on 2007-03-31
El driver de NVidia s'instal·la contra el kernel que estiguis corrent en aquest moment. ¿Podria ser que haguéssis esborrat el nucli que tenia el driver instal·lat?

De tota manera, això no té res a veure amb el fet que no puguis executar el fitxer. Jo provaria de baixar un nou fitxer de la web de NVidia, a veure si llavors funciona.

No en treuràs res de sobreescriure el xorg.conf, si no tens el driver de nvidia instal·lat. Si de cas, prova de carregar el driver lliure, com a mínim et funcionaran les X: edita el xorg.conf i a la secció "Device", allí on posa

        Driver          "nvidia"

posa-li

        Driver          "nv"

salva i reinicia les X (sudo /etc/init.d/gdm restart) o bé tot el sistema.

No tindràs acceleració 3D, però la major part de vegades no es fa servir per a res.

---

### Post by sianeu on 2007-03-31
Ja ho he solucionat. La veritat es que no se bé què ha passat.

He entrat a terminal a prova de fallades des de la pantalla de login. He actualitzat per si alguna novetat desfeia el problema.
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

He reiniciat i tot igual. He repetit el procés per que algun paquet no havia baixat. Tampoc ho ha fet, així que he sortit de X

sudo /etc/init.d/gdm stop
ctrl+alt+f1

He provat de reinstar Nvidia i com sempre: sh:no pot obrir el fitxer. Provo de substituir xorg.conf per la copia de seguretat i em diu que no tinc permisos :mad: .

No se cóm cambiar a root des de terminal (com es fa?) y començo a provar per provar.

sudo sh (no se que es sh (que es?)

Entra sh i començo a provar el mateix a veure que passa. Res, no recordo bé però tampoc podia fer gaire res.

exit

Torno a ser l'usuari. Estava a punt de reiniciar, però abans provo una última vegada de reinstalar el driver de Nvidia. I ara va i funciona, aquest cop sh l'ha pogut obrir !!

Ja torno a ser a Ubuntu i el sistema m'avisa que tinc més actualitzacions. Però jo, de moment, com si res.........

Salut

---

### Post by RainCT on 2007-03-31
Hola,

M'alegro de que ja et funcioni :).

Sobre com estar com a root a la terminal, simplement inicia sessió amb el teu usuari (que ha de ser administrador, clar) i després escriu "sudo -s" (et demanarà la contrasenya, i llestos).

---


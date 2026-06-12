---
title: "Unity or not Unity?"
date: 2011-05-05
forum: Catalan Team
---

### Post by rosa d'abril on 2011-05-05
Jo també m'he baixat l'11.04 i ja tira. L'Unity tampoc no m'acaba de convèncer però intentaré acostumar-m'hi una mica abans de tornar al Gnome. Ara, això sí, hi ha manera d'aconseguir que els botons de tancar, minimitzar i restaurar apareguin a la dreta de la barra de tasques superior? He aconseguit fer-ho amb les finestres que vaig obrint però no amb aquests. 
Per altra banda, hi ha manera de deixar fix a la barra superior el menu Fixter-Edita-Visualitza, etc., que s'autoculta en separar-ne el punter?
Gràcies

---

### Post by wgarcia on 2011-05-05
Quant als botons de maximitzar, minimitzar, tancar, suposo que per disseny han d'estar a l'esquerra perquè quan es maximitza la finestra queden al quadre superior i se superposarien als indicadors de la dreta si estan a la dreta. 

Quant al menú global, em sembla que no es pot configurar perquè no s'autoamagui, però es pot cancel·lar el menú global. No ho he provat però, però he vist aquesta instrucció:

sudo su
echo "export UBUNTU_MENUPROXY=" > /etc/X11/Xsession.d/81ubuntumenuproxy

que s'ha de donar des d'una terminal. Compte amb el "sudo su" que l'usuari queda com a superusuari i pot modificar qualsevol part del sistema deixant-lo inservible, en quan acabis el millor és entrar 

exit

per sortir d'aquesta sessió de superusuari.

---

### Post by rosa d'abril on 2011-05-06
Moltes gràcies però no vull cancel·lar-lo sinó més aviat al contrari: que es quedi fix.
De tota manera, aprofito per llençar una nova pregunta: aquesta barra tan boniqueta que apareix a la banda esquerra de l'escriptori, hi ha manera de posar-la en horitzontal abaix de tot?
Novament, gràcies

---

### Post by wgarcia on 2011-05-06
De moment la barra de tasques de l'esquerra, el llançador d'Unity, no es pot moure. Diuen que per a la 10.10 serà tot molt més configurable.

---

### Post by rosa d'abril on 2011-05-07
Vaja, gràcies per la informació. Em sorprèn aquesta falta de flexibilitat però què hi farem? Sempre puc tornar a l'escriptori antic.

---

### Post by wgarcia on 2011-05-07
La falta de flexibilitat es deu a què de moment han apostat per assegurar que tot funcioni més o menys bé i cada nova prestació i configuració pot introduir problemes addicionals, al final ha estat un cicle curt de desenvolupament (6 mesos), segurament per a la 10.10 hi haurà més configuracions disponibles.

---

### Post by quitus on 2011-05-08
Només comentar que en cas de tenir unity amb acceleració 3D hi ha un editor especial per unity en el editor de la configuració del compiz. No es que hi hagi moltes opcions, però es pot modificar la mida de les icones del llançador, hi ha opcions d'ocultació i alguna cosa més.

salut

---

### Post by akyra on 2011-05-09
Hola a tothom,

És cert que pel moment l'Unity no té gaires configuracions, i pot ser en un principi costa d'acostumar-si, però en general m'agrada molt, trobo que és molt net, i no tinc problemes amb la barra de notificacions del gnome.
Com a problemes trobo que hi h apoques aplicacions que ho soportin, no es poden esborrar els documents recents, i poques posibilitats de configuració.

Jo pel moment seguiré utilitzant-ho, a mi m'agrada.

---

### Post by tanreb20 on 2011-05-09
Ei!

A mi m'encanta de moment, el trobo molt práctic per tenir les coses ordenadetes, a l'estiu Docks...

L'unic que em falla es que falta trballar més el tema notificacions i area de notificacions...

Aplicacions com ara l'Amsn has de fer mans i manigues per que es mantinguin obertes i les puguis minimitzar ala "safata de sistema"

---


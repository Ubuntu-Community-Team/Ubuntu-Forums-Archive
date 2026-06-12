---
title: "escriptori privat - lubuntu 10.10"
date: 2010-12-12
forum: Catalan Team
---

### Post by yae7 on 2010-12-12
Hola:

sóc novell en el món ubuntu, bé en linux en general.:P

He instal.lat lubuntu 10.10, però vaig triar durant la instal.lació que l'escriptori de l'usuari per defecte fós privat, però no m'és necessari. i preguntareu: "per què ho vas seleccionar?". Doncs no ho sé....com vinc de Windows doncs em pensava que era una cosa similar.

Resumint: Com puc fer per a què ja no sigui privat?

Gràcies.

Salutacions

---

### Post by wgarcia on 2010-12-12
Suposo que tens alguna raó clara per haver instal·lat "lubuntu". És un sabor excel·lent d'ubuntu,  però potser no el més indicat per a un que comença amb linux, més que res perquè no és un sabor que faci servir massa gent i és més difícil obtenir ajuda, tot i que a part d'això pot ser perfectament una bona elecció. 

Quant a la teva pregunta, has d'obrir una terminal, cosa que penso que en Lubuntu (no tinc cap instal·lació a prop) es fa clicant als menús, escollint "Accessoris" i aquí escollint "LXTerminal". Suposo que no tens cap dada important encara desada al teu espai, perquè s'hauria de fer una còpia de seguretat primer si fos el cas (per exemple copiant les dades a una memòria USB). Bé, en aquest cas has d'entrar les següents instruccions a la terminal, tot prement "Intro" al final de cadascuna:

ecryptfs-umount-private  

chmod 700 ~/Private  

rm -rf ~/Private ~/.Private ~/.ecryptfs  

sudo apt-get remove ecryptfs-utils libecryptfs0 

Quan premis intro en aquesta última instrucció, et demanarà la clau i li has de donar la teva clau d'usuari. 

Un cop fet això surt de la teva sessió i torna a entrar i ja no hi hauria de fer servir l'escriptori privat.

---

### Post by yae7 on 2010-12-12
Hola:

gràcies per respondre.

Doncs he triat lubuntu perquè necessitava un distro lleugera per a un ordinador una mica antic. N'he provat varies, i fins fa poc estava utilitzant Puppy linux 5.1. el puppy Funciona molt bé i es molt lleugera, però m'agrada més aquesta distro. Triar per triar...:P Es molt més fàcil la instal.lació del programari i les seves dependències.

Doncs vaig a provar aquests passos que m'has descrit, i ja us comento.

salutacions

---

### Post by yae7 on 2010-12-12
bé, al final he tornat a instal.lar des de cero el lubuntu, ja que no m'acabava de funcionar correctament l'escriptori.

salutacions

---


---
title: "Pantallasso i no arrencada de l'Ubuntu"
date: 2012-11-26
forum: Catalan Team
---

### Post by amirrocat on 2012-11-26
Bon dia. Sóc nou al fòrum i a Ubuntu, pràcticament (tot i que ja fa més o menys un any que vaig alliberar-me dels jous de Güindous), així que em presento. Sóc l'amirrocat, un plaer ésser per aquí.

Bé, vaig instal·lar-me fa qüestió de dues setmanes l'Ubuntu 12.10 perquè el 12.04 fotia errades com no deixar-me obrir l'Skype o el Centre de programari, cosa que semblava mig solucionada (ja que el Centre de programari encara no el podia obrir). Malauradament, però, se m'afegiren un parell de problemes: primer em sortia un pantallasso que deia que hi havia un error al kernel, si no m'erro, tot i que després de prémer F perquè em solucionés els problemes (tot i que semblava que no els solucionava, val a dir) Ubuntu arrencava. Ara, però, el pantallasso que surt és aquest de la imatge, i Ubuntu no arrenca. 

[IMG]http://postimage.org/image/ba0wf341z/[/IMG]

Espero que pugueu ajudar-me a solucionar el problema tenint en compte que no vull perdre cap dada de les que tinc desades a l'ordinador. 

Moltes gràcies!

---

### Post by wgarcia on 2012-11-26
No has adjuntat la imatge, o no la sé veure.

---

### Post by amirrocat on 2012-11-26
A la icona, però t'adjunto l'URL i ja està. A veure si pots ajudar-me! :)

[http://postimage.org/image/ba0wf341z/]("http://postimage.org/image/ba0wf341z/")

---

### Post by wgarcia on 2012-11-26
Jo primer, abans de remugar res, arrencaria el sistema amb un CD o USB autònom, i intentaria fer una còpia de seguretat de totes les dades, si no les tens. 

Simplement aconsegueix-te un CD d'instal·lació d'Ubuntu, o un USB arrencable. arrenca'l en mode prova, obre un "navegador de fitxers", i munta el disc on tens les dades des de les opcions de discos que veus a l'esquerra. Si es veu més d'un muntal's tot i mira després quin és el que conté les teves dades. 

Si et diu que són sols de lectura fes "Alt-F2" i entra "gksudo nautilus" per navegar com a super-usuari.

Un cop trobades les dades copia-les a una memòria USB per tenir-les guardades. 

Un cop fet això es podrà mirar perquè et surt el problema que dius, i què fer. Tens entrada per la pantalla inicial on surten els sistemes operatius que tens instal·lat (Grub)? Si és així mira si tens una entrada que diu "versions anteriors" a veure si hi ha algun nucli (kernel) més antic que es pugui provar.

---

### Post by wgarcia on 2012-11-26
Mirant una mica el problema que reporta, segons he pogut llegir el missatge que reps és perquè no s'ha generat un fitxer clau per a l'arrencada que es diu initramfs. Sembla que la següent llista d'instruccions ho arregla. Prova-ho després d'assegurar-te que tens còpia de seguretat de les dades.

Un altre cop la clau és arrencar el sistema amb un CD o USB autònom (Live CD o USB). Un cop estàs en el sistema de prova, obre una terminal, on s'han d'entrar:

Primer has d'identificar la partició on està instal·lat l'Ubuntu:

```
sudo fdisk -l
```

Mira les particions que et mostra a veure si pots identificar el que conté el teu sistema (posarà alguna cosa com a Linux). Suposant que és /dev/sda2:

```

sudo mount /dev/sda2 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt 
```

I ara es repara la instal·lació:

```

update-initramfs -u -k 3.5.0-18-generic
update-grub2

```

Després reiniciar i creuar els dits.

---

### Post by amirrocat on 2012-11-26
Sóc un pringaillo en informàtica, així que no tinc massa idea de com fer gaire res del que dius. 

A veure, tinc un USB amb l'Ubuntu 10.10 em sembla i no sé quina de les opcions que em dóna he de triar. 

De totes maneres, deixa'm dir-te que la pantalla del GRUB amb les opcions: "Ubuntu", "Opcions avançades de l'Ubuntu", "Memory test (memtest86+)" i "Memory test (memtest86+, serial console 115200)"; ja m'apareixen. 

Si li dono a l'opció "Ubuntu", perquè arrengui el sistema, després d'estona "pensant" em dóna l'error 0xb8770 en <<hdo>> i després surt el pantallasso que et dic.

---

### Post by wgarcia on 2012-11-26
Si tens l'USB amb el 10.10, ja és prou. Mira d'arrencar l'ordinador amb l'USB posat a veure si arrenca l'Ubuntu de prova, si ho fa un cop que estiguis a l'escriptori de prova, busca "terminal" als menús, i ves entrant una a una les instruccions del missatge (prement INTRO després de cada una). 

Si no arrenca la sessió de prova d'Ubuntu des de l'USB hauràs de entrar en el menú de configuració de l'ordinador i mirar una configuració que diu ordre d'arrencada (o BOOT ORDER en anglès). Un cop aquí has de canviar l'ordre perquè el primer de la llista sigui "USB boot" o alguna cosa així. Un cop que tornis a arrencar l'ordinador amb l'USB posat t'hauria d'iniciar la versió de prova de l'Ubuntu.

---

### Post by amirrocat on 2012-11-27
> **wgarcia said:**
> Si tens l'USB amb el 10.10, ja és prou. Mira d'arrencar l'ordinador amb l'USB posat a veure si arrenca l'Ubuntu de prova, si ho fa un cop que estiguis a l'escriptori de prova, busca "terminal" als menús, i ves entrant una a una les instruccions del missatge (prement INTRO després de cada una). 

Si no arrenca la sessió de prova d'Ubuntu des de l'USB hauràs de entrar en el menú de configuració de l'ordinador i mirar una configuració que diu ordre d'arrencada (o BOOT ORDER en anglès). Un cop aquí has de canviar l'ordre perquè el primer de la llista sigui "USB boot" o alguna cosa així. Un cop que tornis a arrencar l'ordinador amb l'USB posat t'hauria d'iniciar la versió de prova de l'Ubuntu.

El problema és accedir als arxius que tinc desats a l'ordinador. No sé com des de l'USB Boot, un cop estic a l'Ubuntu "de prova" (que suposo que deus voler dir que és en el qual surt l'instal·lador), accedir a aquests arxius...

---

### Post by wgarcia on 2012-11-27
Per accedir als arxius, simplement des de la sessió de prova obre un "navegador de fitxers", i a la barra de la dreta veuràs els volums (particions). Clica sobre el que vulguis obrir i es muntarà. Un cop muntat podràs navegar a la teva carpeta d'inici i copiar els teus fitxers.

---

### Post by amirrocat on 2012-11-27
He fet tot el que m'has dit i tot ha fallat, malauradament... Quan puguis em dius el que puc fer. 

Merci altre cop.

[http://postimage.org/image/85xzzqd9h/](http://postimage.org/image/85xzzqd9h/)

---

### Post by wgarcia on 2012-11-28
Suposo que la pantalla que mostres és el que obtens quan inicies l'ordinador des de l'arrencada USB. 

Dóna primer la següent instrucció:

```
sudo fdisk -l
```

i mostra el resultat, potser /dev/sda és el dispositiu que està assignant el sistema al disc USB.

---

### Post by amirrocat on 2012-11-28
Solucionat! Finalment he hagut d'introduir el comando update-initramfs -u -t -v perquè se solucionés i fer-ho des de root. 

En qualsevol cas, arreglat.

Gràcies altre cop, anem llegint-nos! :)

---

### Post by wgarcia on 2012-11-28
M'alegro, sisplau si pots posa-li "Solved" clicant sobre "Thread tools" al fil així queda constància per si a algú li passa el mateix.

---


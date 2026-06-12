---
title: "escaneig al iniciar??"
date: 2007-10-08
forum: Catalan Team
---

### Post by pablinsfc on 2007-10-08
Bones!!

Us escric perquè més d'una vegada m'ha sortit el següent missatge i no sé si em falta activar alguna opció o és normal que cada X temps, al iniciar-se doni aquest missatge (tant al pc de sobretaula com al portàtil):

[...]
* Loading manual drivers... 	[OK]
* Activating swap...		[OK]
* Checking root file system...
fsck 1.40-WIP (14-Nov-2006)
/dev/sda1: Superblock last mount time is in de future. FIXED
/dev/sda1 has gone "x" /*el nombre no el recordo*/ without being checked, check forced.
/dev/sda1: |===================================================  -89.4%

Tinc la sensacio que s'haura de fer el "check" més sovint i no ho tinc activat, però tampoc ho sé del cert...

Gràcies per endavant.

Pau.

---

### Post by papapep on 2007-10-08
Sinó recordo malament, la verificació s'efectua cada 30 arrencades o cada 30 dies, el que arribi abans.

---

### Post by pablinsfc on 2007-10-08
Llavors entenc que és normal, rutinari. El desconeixement em feia pensar que em deixava alguna cosa. Suposo que al estar acostumat a les finestres que només escaneja quan passa algo "dolent"...

També suposo que m'hauria d'acostumar a que el finestres fa les coses una mica a l'inrevés, no??

jajajaja

Merci papapep!

Salut!

---

### Post by Ferri on 2007-10-09
Pots ajustar cada quan vols que faci la comprovació amb tune2fs. Per exemple:```
sudo tune2fs -c 20 -C 15 /sda3
```
et farà que la partició sda3 es comprovi cada 20 cops que es munti i li poses el recompte de cops que s'ha muntat a 15 (és a dir, el primer cop et farà la comprovació d'aquí a 5 vegades que es munti).

---


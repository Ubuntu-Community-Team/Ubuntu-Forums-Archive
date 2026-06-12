---
title: "veure espai restant disc dur"
date: 2009-05-31
forum: Catalan Team
---

### Post by neo_76 on 2009-05-31
Hola de nou,
  segueixo cultivant-me amb això del Lnux. Ara m'agradaria saber si puc veure les unitat de dic dur, quanta memòria em queda. En el PC hi tinc dos unitats una de 8Gb i l'altra de 30Gb. Com puc saber on guardo les coses, etc...

---

### Post by papapep on 2009-05-31
neo_76: un parell de conceptes per parlar el mateix llenguatge i no confondre'ns:

Memòria és la RAM, i algun altre xip que fan servir els ordinadors. A l'emmagatzematge del disc dur en diem "espai", no memòria.

Quan dius "unitats", vols dir "particions"?

Per saber l'espai lliure de les particions, fes:

```
df -h
```

i veuràs una cosa semblant a això:

```
papapep@awacs:~$ df -h
S. fitxers            Mida En ús Lliure %Ús Muntat a
/dev/sda1              19G  3,1G   15G  18% /
tmpfs                 750M     0  750M   0% /lib/init/rw
varrun                750M  100K  750M   1% /var/run
varlock               750M     0  750M   0% /var/lock
udev                  750M  172K  750M   1% /dev
tmpfs                 750M   84K  750M   1% /dev/shm
lrm                   750M  2,4M  748M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda2              36G   24G  9,4G  72% /home
/dev/sdc1              78G   51G   24G  69% /media/disk-1
/dev/sdc2              53G  180M   50G   1% /media/disk-2
/dev/sdc4             330G  315G  1,9G 100% /media/disk-3

```

observa que, en el meu cas, el disc dur intern (sda) té dues particions (de fet en té tres, però aquí no es veu sda3, la swap):
 
- sda1 que és el directori arrel (/) de l'estructura de directoris.
- sda2 que és el directori (/home) i tots els seus subdirectoris.

El teu cas serà semblant, tot i que no idèntic.

També pots veure les particions i l'espai ocupat i lliure d'un disc dur extern USB que tinc, que comencen per sdc.

---

### Post by neo_76 on 2009-05-31
no, amb unitats vull dir unitat de disc dur físiques.
Amb del "df -h" no veig el disk dur de 8Gb.

---

### Post by papapep on 2009-05-31
Intern? extern? USB? SATA? 

Quan executes ordres cal que ens enganxis aquí el resultat, per veure el mateix que tu veus. Si no, estem venuts...

---

### Post by RainCT on 2009-06-01
Sistema -> Administració -> Monitor del sistema, pestanya «Sistemes de fitxers».

---

### Post by papapep on 2009-06-01
I si no el té muntat, li sortirà per aquí?? :P

---


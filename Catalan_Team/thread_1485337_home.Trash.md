---
title: "home/.Trash"
date: 2010-05-16
forum: Catalan Team
---

### Post by jinglada on 2010-05-16
Tinc el disc molt ple i tot d'una m'ha sortit un avís que només em quedaven 2 Gb i que si volia engegar l'Analitzador. Li he dit que si i llavors m'ha mostrat dins del home/ el directori home/joan i el directori home/.Trash de 14 Gb amb 2 subdirectoris home/.Trash/files i home/.Trash/info. El contingut del directori files és 454683 elements, de mida total 13,1 GB i l'espai lliure 6,2 GB (suma més que la mida del directori .Trash). El contingut del directori info és 126 elements, de mida total 14,3 KB i l'espai lliure 6,2 GB. 

La paperera diu que és a la ubicació trash:/// (no sé on és això dins del Sistema de fitxers)

Els fitxers de home/.Trash/files els vaig esborrar en dues dates, uns el 21-3-09 i la resta el 5-8-09 segons els elements de home/.Trash/info

Puc eliminar el directori home/.Trash/ movent-lo a la paperera o el deixo i esborro només el contingut? Si es pot eliminar el .Trash ho hauré de fer des del Terminal oi? perquè amb el nautilus no el veig.

joan@joan-laptop:/home$ ls -la
total 48
drwxr-xr-x   5 root root  4096 2009-03-21 09:35 .
drwxrwxrwx  23 root root  4096 2010-05-16 11:12 ..
drwxr-xr-x 118 joan joan 20480 2010-05-16 23:51 joan
drwx------   2 root root 16384 2009-03-16 01:33 lost+found
drwxr-----   4 joan joan  4096 2009-03-21 09:35 .Trash-0
joan@joan-laptop:/home$ cd .Trash-0
[email]joan@joan-laptop:/home/.Trash[/email]-0$ ls -la
total 24
drwxr-----  4 joan joan  4096 2009-03-21 09:35 .
drwxr-xr-x  5 root root  4096 2009-03-21 09:35 ..
drwxr----- 13 joan root  4096 2009-08-05 16:44 files
drwxr-----  2 joan root 12288 2009-08-05 16:44 info

Gràcies a la bestreta.

---

### Post by wgarcia on 2010-05-17
El Trash des de hardy està a 

/home/usuari/.local/share/Trash

per tant

/home/usuari/.Trash sembla ser un remanent d'instal·lacions anteriors i el pots esborrar junt amb tot els seu contingut, i la teva paperera continuarà funcionant correctament.

---

### Post by jinglada on 2010-05-17
Gràcies wgarcia.

> **wgarcia said:**
> El Trash des de hardy està a 

/home/usuari/.local/share/Trash

Verificat, tinc la paperera actual a /home/joan/.local/share/Trash

> **wgarcia said:**
> per tant

/home/usuari/.Trash sembla ser un remanent d'instal·lacions anteriors i el pots esborrar junt amb tot els seu contingut, i la teva paperera continuarà funcionant correctament.

De fet no és /home/usuari/.Trash sinó /home/.Trash-0 com pots veure en "joan@joan-laptop:/home$ ls -la" que adjunto a l'anterior missatge (lapsus, no vaig posar "-0" després de .Trash). Tanmateix eliminaré el directori i a veure si recupero espai.

En relació a la versió de l'Ubuntu he de dir que aquest ordinador el tinc des de mitjans de març 2009 i per tant vaig instal·lar l'Intrepid. Total que no entenc com es deuria crear aquest directori /home/.Trash-0 i que hi anés a parar tanta brossa... (?)

---

### Post by jinglada on 2010-05-20
He buidat el directori /home/.Trash-0 però aquest no es deixa eliminar.

[email]joan@joan-laptop:/home/.Trash[/email]-0$ ls -la
total 8
drwxr----- 2 joan joan 4096 2010-05-20 20:32 .
drwxr-xr-x 5 root root 4096 2009-03-21 09:35 ..
[email]joan@joan-laptop:/home/.Trash[/email]-0$ cd ..
joan@joan-laptop:/home$ ls -la
total 48
drwxr-xr-x   5 root root  4096 2009-03-21 09:35 .
drwxrwxrwx  23 root root  4096 2010-05-20 11:05 ..
drwxr-xr-x 118 joan joan 20480 2010-05-20 20:28 joan
drwx------   2 root root 16384 2009-03-16 01:33 lost+found
drwxr-----   2 joan joan  4096 2010-05-20 20:32 .Trash-0
joan@joan-laptop:/home$ rm .Trash-0
rm: no s’ha pogut eliminar «.Trash-0»: Permission denied
joan@joan-laptop:/home$ sudo rm .Trash-0
[sudo] password for joan: 
rm: no s’ha pogut eliminar «.Trash-0»: Is a directory

Què he de fer?

---

### Post by oriolsbd on 2010-05-20
Per esborrar un directori (buit), l'ordre correcta és "rmdir", i no "rm". :-)

És a dir:
```
rmdir .Trash-0
```

Salut!

---

### Post by jinglada on 2010-05-20
> **oriolsbd said:**
> Per esborrar un directori (buit), l'ordre correcta és "rmdir", i no "rm". :-)

És a dir:
```
rmdir .Trash-0
```

Salut!

Quin "fall":( És que no es pot còrrer...:guitar:

Gràcies! :popcorn:

---


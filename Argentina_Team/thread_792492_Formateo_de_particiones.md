---
title: "Formateo de particiones"
date: 2008-05-13
forum: Argentina Team
---

### Post by ramiro_md on 2008-05-13
Hola amigos del foro, les comento que a la hora de instalar ubuntu cree 3 particiones:
1) /: 10gb destinada a alojar el sistema operativo (ext3)
2) /home: 20gb para datos (ext3)"/sda8"
3) swap: de 512mb
lo que necesito es formatear las particiones que cree al instalar linux, así poder crear una swap de 2gb y una ext3 de 10gb para el operativo. Y el resto del espacio asignarlo al disco d (nfts "/sda5") que es donde guardo todos mis archivos.

Dejo adjunto una captura de pantalla de mis particiones.

Desde ya muchas gracias

---

### Post by faktorqm on 2008-05-13
No veo por que tendrias que formatear algo, asi y todo lo que tenes que es hacer, es borrar las ultimas 3 particiones, y comenzar a particionar como vos queres del final para adelante digamos, y lo que te quede libre se lo das a la particion de windows.

Otra cosa que veo es que tenes demasiado ocupado en el "/", instalaste 15000 juegos no? o sea, si es asi todo bien, pero si no tenes un ""problema"" en algun lado. 

Salu2!!

---

### Post by ramiro_md on 2008-05-15
Siempre la respuesta del hermano pincha =)...no, la verdad es que instale mucha *** en ubuntu..y quería formatearlo y volverlo a instalar....y de paso arreglar lo de las particiones. Cuando quiero borrar la swap desde partitionmagic me tira error al igual que cuando quiero hacerlo en la "/"..si me podrían dar alguna pista :(

---

### Post by ramiro_md on 2008-05-15
URGENTE necesito ayuda....inexplicablemente el espacio libre en mi "/" se vio reducido a solo 300 mb....necesito que me digan como formatear la *** unidad y cargar de nuevo ubuntu.

---

### Post by uidb4056 on 2008-05-15
Para cambiar/formatear las particiones tienes que arrancar con el Live CD de instalación y arrancar desde el menu Sistema-Administador el editor de particiones (GParted). Desde un sistema operativo instaldo solo se pueden modificar las particiones que no están montadas.

---

### Post by faktorqm on 2008-05-16
Hola! che, yo no te lo quise decir para que no armarte lio pero si tenes back-up de esos 20 gb te recomendaria borres todas las particiones menos la que tiene el windows, o sea la primera, es decir, la extendida entera.

te quedaria (las 4 particiones son primarias, olvidate de las extendidas):

particion 1: DEJALA COMO ESTÁ, montala como "/media/windows" (por ejemplo)
particion 2: ext3, montada como "/home", 116gb.
particion 3: ext3, montada como "/", de 10gb.
particion 4: swap, no se monta, 2 gb

Despues al windows le pones el driver ext3 y usas esa particion como alguna letra, por ejemplo "f:" y listo el pollo.

Fijate, o sea, este es mi consejo, capaz no te gusta, o no queres, pero esto anda joshita :P Salu2!!

---


---
title: "[SOLVED] Consulta sobre GRUB"
date: 2008-05-02
forum: Argentina Team
---

### Post by vk-cdg on 2008-05-02
Buenas, tengo una consulta, va mas que nada necesito que alguien me heche un poco de luz...

La situación es la siguiente. En mi desktop tengo 2 discos:

1) sata 160GB (2 particiones: NTFS con Windows y FAT para cosas varias)
2) sata 250GB (3 particiones: ext3 para el /, ext3 para el /home y swap).

El problema es que el disco de 160 (donde está Windows) está palmando, muchas veces no lo escucho arrancar, o cuando arranca, queda haciendo unos ruidos raros. Por suerte está en garantía, así que lo voy a llevar a que lo revisen/cambien.

La consulta es... 

¿el GRUB, donde está alojado fisicamente? 
¿de donde lo lee?
¿que pasa si saco el disco 1 (de 160gb)?
¿levantará linux sin ese disco (por el GRUB digo)?

Gracias mil!

---

### Post by Mauro22 on 2008-05-02
Generalmente el grub se instala en el principio del disco donde se instala linux. Otra opcion es el MBR pero es una "opcion avanzada"


Proba desenchufando el de 160 y arrancando la PC.


De ultima si no arranca, metes el live cd y configuras el GRUB de nuevo.

---

### Post by vk-cdg on 2008-05-02
Mauro, siempre con una respuesta a mano!!! jajajaja.

Cuando llego a casa lo pruebo. 
Ahora... como lo configuro desde el liveCD?

---

### Post by Mauro22 on 2008-05-02
Yo siempre hice asi:

metes el livecd, abris la consola y pones:

sudo grub

y te aparece asi:

grub>

ya ahi pones 

root (hdX,Y)
setup (hdX)
quit 
donde X es el disco e Y la particion.

---

### Post by vk-cdg on 2008-05-03
En mi caso el grub estaba instalado en el disco 1 (el de 160GB) donde estaba Windows en una partición y Fat32 en la otra. 
Digo estaba porque anoche el disco decidió fallecer por lo que al encender la PC, no leía el grub por lo tanto me quedé sin Windows ni linux. 

Aproveché e instalé Hardy (desde ahí estoy) pero en el disco de 250. Cuando me entreguen el disco de recambio (de 160) e instale Windows, voy a tener que "mover" el GRUB y ahí les pediré ayuda nuevamente.

---


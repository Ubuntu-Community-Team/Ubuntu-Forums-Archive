---
title: "Instalacion Mal Hecha"
date: 2007-11-02
forum: Argentina Team
---

### Post by dj_isaco on 2007-11-02
hola a todos los molesto porque el otro dia estaba viendo que tengo un munton de particiones, eso me pasa por no prestar atencion a la guia, bueno les comento lo que tengo y lo que quiero hacer yo tengo dos HD de 160 c/u uno (sata) con win y en el otro (ata) esta My Ubuntu, pero hasta aqui no hay problema, pero resulta que cuando instale feisty selecione la 2º HD por completo,y andaba bien pero cuando quise actulizarlo no entendia nada, asi q intente hacer una instalacion limpia de gutsy y me daba un error en las particiones asi despues de varios intentos lo pude instalar dejando el modo automatico y me quedo asi:
---------------------------------------------------------------------------------------------------
----------------------sist de arch----------punto month--------------tamañ                                                               
---------------------------------------------------------------------------------------------------   
  /dev/hdb1       |       -----ext3 ----------------- /media/disk- 1 ---------- 145.41 gib                                        
  /dev/hdb3       |  desconocido ---------- /media/disk ------------- 2.04 gib                   
  /dev/hdb2       |     extended ------------------------------------------------ 1.60 gib
     /dev/hdb6 |     linux-swap ---------------------------------------------- 164.67 mib
        /dev/hdb5 |   linux-swap  ---------------------------------------------- 1.44 gib

el sata tiene dos part. una de 30 gb y la otra 130 gb
a mi me gustaria foramatear el ata y dejarlo una sola part. y al sata de 30 utilizarlo para SO y al 130 dejarlo como esta ntfs ya que hay tengo musica y peliculas (esta casi lleno), y serian muchos dvd para bajarlos.
como podria hacer para utilizar el ata de 160 como home el de 30 para sistema y swap. Esto es posible?, muy complicado? o imposible es una preguntita mas o menos asi que no tengo apuro.
Gracias a todos y espero sus repuestas.

---

### Post by Mafber on 2007-11-03
Hola Dj_isaco!!!
Veo que tenés un poco de lío en las particiones (unidades). Como concejo te diría que vuelvas a bootiar desde el cd-live y empieces de cero. Y cuando llegue el momento redefiní las particiones (no te preocupes que es fácil) borralas a todas y empeza de cero. 
Si no estas muy seguro de cómo hacerlo, lo que podes hacer es desde windows usar el “partition magic” formatea ese hd y crea las unidades con los tamaños que quieras.
Lo que haría es crear 3 unidades:
2 en ext3 (“/” y “home”) y 1 para swap (de máximo de 512 mb)
Suerte!!! :)
No dudes en consultar

---

### Post by sajnox on 2007-11-03
Consejo parecido al de mafber, pero te cambiaria el win por el live cd de ubuntu y usar el gparted, lo tenes en sistema/administracion/editor de particiones

Saludos

---

### Post by dj_isaco on 2007-11-04
gracias por las respuestas ya acomodo los datos y borro todo

---


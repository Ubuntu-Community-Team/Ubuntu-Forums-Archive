---
title: "Ubuntu anda en Colinux!"
date: 2007-06-07
forum: Argentina Team
---

### Post by juako on 2007-06-07
Me compré un disco de 500G y lo junté con otro de 300G que tenía usando LVM, ahora tengo un hermoso disco virtual de 800G XFS para empacharme de videos y musica. Como necesito acceder a estos datos desde windows levanté la partición de Ubuntu en CoLinux, pero igual me enfrenté con el problema de que el mismo no trae por defecto el driver para LVM, así que...

Tras romperme el o***e logré compilar un kernel 2.6.17.14 con los patches de colinux **Y **los patches de Edgy (el ultimo patch estable de edgy para esa linea de kernels: no pude usar los patches de feisty porque son para 2.6.20+). El GCC es 4.1 (el de feisty), y desistí de compilar un colinux con la misma versión porque era un quilombo negro así que al final encontré los binarios de los demonios colinux, FLTK, etc. compilados con GCC 4.1. (CoLinux no deja arrancar el guest kernel sin no está compilado con la misma versión de GCC que el demonio y el driver).

Estoy bastante débil por las horas pasadas frente a la computadora y he perdido alrededor de 105.000 neuronas pero soy feliz! ahora con sambita levanto mis datos en Guinda Operating System, es más! es mi "carpeta Mis Documentos" :guitar:

Siguen los pasos de instalar ESD, X y otras cosas y de migrar ubuntu a loopbacks en el área de datos, perfeccionar el dual boot, etc pero ya va tomando forma.

**Necesito ayuda en lo siguiente:**

Alguien me puede decir como puedo generar una serie de diffs comparando el árbol que tengo parchado contra el arbol 2.6.17.14 sin parchar? así lo tengo guardadito y puedo distribuirlo para el que necesite un kernel de estas características.

Muchas gracias! Aguante Ubuntu! ):P

---

### Post by lavaramano on 2007-06-07
mira que loco / interesante eso.
igual a mi nunca me funco bien el colinux.. supongo que era porque tneia una maquina de ****** :mrgreen:

---

### Post by clasificado on 2007-06-09
¡Muy groso lo tuyo!

No tengo idea de que herramienta puede hacer un patch de un directorio completo, porque el diff gnu solo puede hacerlo archivo por archivo, y nunca trabajé con diffs fuera de svn.

Pero a mi me serviria bastante que cumplas tu cometido, asi que si veo algo por ahi lo postearé.

Sino de ultima tirate los sources completos.

Clasificado

---

### Post by ariel on 2007-06-10
Si el objetivo es nomas acceder desde Windows a particiones linux EXT3, la opcion que yo uso desde hace mucho es:

[http://ext2fsd.sourceforge.net/index.htm](http://ext2fsd.sourceforge.net/index.htm)

Anda muy bien. No estoy seguro si soporta LVM / stripped disks etc, pero en una de esas si.

---

### Post by juako on 2007-06-14
lavaramano: el colinux creo que anda igual con maquinas chongas! no se cual tenés pero la mas chica que probé era un PIII con 256 megas, pero para que ande X mejor un poco mas

clasificado: gracias! al final todavía no lo seguí desarrollando :D, es que nunca había usado ubuntu y estoy totalmente ********** instalando cosas y jugando con el ubuntu desde hace una semana! pero lo voy a terminar todo, aunque cada vez tiene menos goyete usar Guinda OS, excepto tal vez por progs como propellerheads Reason 3 (aunque quiero ver si anda bien bajo Wine)
per bueno cuando lo termine voy a postear los resultados en este thread...en cuanto a los patches, encontré un programa gtk que genera las diferencias entre dos directorios...hoy a la noche posteo el tgz y una pequeña guía si puedo

ariel: si yo lo usé y esta bueno, pero el volumen lógico está en XFS..igual EXISTE un driver que tiene XFS/ETX2/EXT3, hechos por transmeta, pero no me dió muy buen resultado.

---


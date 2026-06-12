---
title: "No puedo Iniciar, Espacio Insuficiente"
date: 2008-05-11
forum: Argentina Team
---

### Post by Legumbre on 2008-05-11
HOla, disculpen las molestias; soy nuevo en esto de linux, y lo instale en una particion nueva. El problema surge que esa particion se "lleno" y ahora no me deja iniciar ubuntu, alegando que no tiene espacio para poder iniciar.
Alguien seria tan amable de ayudarme?
Desde ya, muchas gracias

---

### Post by faktorqm on 2008-05-11
Entra con un live cd y anda hasta la carpeta "/var/cache/apt/archives" con el explorador de archivos y si existen archivos ahi borralos todos. Hay uno que no lo vas a poder borrar que se llama .lock.
Si no te deja borrar los archivos por algun motivo, abri una consola, escribi "sudo nautilus", y repeti el proceso. Suerte y salu2!

---

### Post by Legumbre on 2008-05-12
Gracias por responder.
Lamentablemente, lo intente, pero aparentemente no era ese el problema.
Quizas pueda guiarte diciendote el error q tiene:

"GDM no pudo escribir en su archivo de autorizacion. Esto puede significar que no tiene espacio en disco o que su directorio personal no se puede abrir para escrituro (...)"

Desde ya, reitero, muchas gracias por responder

---

### Post by WanderingKnight on 2008-05-12
Lo que faltó mencionar es que para borrar los archivos desde un live cd, tenés que montar el disco primero:

```
sudo su
mkdir carpeta
mount /dev/_d_* carpeta
```

En el primer _ de /dev/_d_* tenés que poner el código asignado a la partición. Si es un disco IDE, empieza con h, si es un disco SATA, empieza con s. En el segundo _, tenés que poner a, b, c y así dependiendo de qué número de disco es (el primer disco conectado es a, el segundo disco es b, y así), y finalmente, el * indica el número de partición.

Entonces, suponiendo que tengas un solo disco SATA y en la segunda partición está el root, el código será el siguiente:

```
mount /dev/sda2 carpeta
```

Y una vez que lo tengas montado, hacé:

```
rm -rf carpeta/var/cache/apt/archives/*
```

Lamentablemente, es un poco complicado para un novato solucionar lo que pediste, pero es posible.

---

### Post by faktorqm on 2008-05-12
Se me pasó ese detalle. Si no tambien podes ir al nautilus y montarlas "a mano" haciendo doble click cuando vas a lugares -> carpeta personal. A la izquierda de la pantalla te aparecen las particiones para montarlas "a mano". Luego la seleccionas y listo. Lo que no recuerdo es si lo hace en modo ro o en rw (read-only (solo lectura) o read-write (lectura y escritura)).
WK: te recuerdo que el kernel toma los discos IDE como /dev/sdX donde X es a, b, c o d en algunos casos, dependiendo (al menos en mis experiencias) del mother. Algunos modelos son h, y el mismo cd de ubuntu en otros es con s. 

Comparto la opinion de que es medio complicado para un novato, pero es ponerle onda y listo :D Salu2!

---


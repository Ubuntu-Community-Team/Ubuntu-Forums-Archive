---
title: "como instalar actioncube?"
date: 2007-02-22
forum: Argentina Team
---

### Post by zspikes on 2007-02-22
buenas gente! aqui zspikes rompiendo las pelotas de nuevo jeje.
Pasa q me baje el actioncube de la [pagina oficial]("http://action.cubers.net/"), el archivo es un tar.bz2, y no se como se intala. Googlee un toque y encontre una pequeña guia pero no me resulto. Alguien sabe como se hace?

Ya q estamos, tb baje el "ubuntu games" y a travez del mismo instale el vdrift y no andubo, asiq corri un "sudo aptitude purge vdrift", pero los accesos directos no se borraron, como los saco? no quiero q ande quedando basura x ahi, gracias!!!

---

### Post by spg76 on 2007-02-22
Según dicen en [este thread]("http://www.ubuntuforums.org/showthread.php?t=355178&highlight=actioncube"), para instalarlo hay que "...correr el archivo actioncube.sh". Calculo que tendrás que darle permiso de ejecución (Clic Derecho > Propiedades > Permisos > Tildar la casilla de Ejecución)
Espero que te sirva.

---

### Post by zspikes on 2007-02-23
lo lei, pero no funciona.

```
gerardo@gerardo-desktop:~$ cd /home/gerardo/Desktop/ActionCube
gerardo@gerardo-desktop:~/Desktop/ActionCube$ sh actioncube.sh
.//bin_unix/linux_client: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory

```

parece q faltan esas librerias, pero no tengo idea de donde las saco y como se instalan

---

### Post by spg76 on 2007-02-23
Podes instalarlas desde Synaptic. Creo que se llaman libsdl-image1.2.
Sino podes probar en la terminal:
```
sudo apt-get install libsdl-image1.2
```

---

### Post by zspikes on 2007-02-23
ahi andubo, muchisimas gracias maestro!!! pense q ya habia intentado eso, pero quiza tipee algo mal. En fin, acabo de jugarlo un toke y tengo una descompostura tremenda jaja, hace banda q no jugaba un juego en primera persona :S

Ya q estamos, para no andar abriendo temas, como puedo conseguir el tux racer? estoy a full con los jueguitos jaja.

gracias y saludos!

---

### Post by spg76 on 2007-02-23
Que bueno que te funciono.
En cuanto al Tux Racer, creo que hay una versión más nueva en los repositorios que se llama Planet Penguin Racer, y la instalas facilmente:

```
sudo apt-get install planetpenguin-racer
```

Saludos.

---

### Post by zspikes on 2007-02-23
disculpa la ignorancia, q repositorios? donde lo consigo? estube googleando un toke y no encontre nada

gracias!

PD: esto me sale cdo ejecuto el comando

```
gerardo@gerardo-desktop:~$ sudo apt-get install planetpenguin-racer
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo información de estado... Hecho
E: No se pudo encontrar el paquete planetpenguin-racer
gerardo@gerardo-desktop:~$ 

```

---

### Post by spg76 on 2007-02-23
> **zspikes said:**
> disculpa la ignorancia, q repositorios? donde lo consigo? estube googleando un toke y no encontre nada

Los repositorios son los servidores desde los cuales se instalan, agregan y/o actualizan programas y librerias. Cuando abris Synaptic, el listado que aparece proviene de la lista de arrchivos que están disponibles en los servidores que tenes como repositorios. Podes verlos en Synaptic en Configuración > Repositorios. De paso te podes fijar si tenes activada la opción que dice "Software libre mantenido por la comunidad (universe)". Si no está tildada debe ser por eso que no podes instalar Planet Penguin Racer. Activala,  presiona el botón recargar y busca un paquete que se llame planetpenguin-racer.
Cualquier duda, avisa.

---

### Post by zspikes on 2007-02-23
sos un genio, ahi encontre todo y estoy instalando. Te lo agradezo de corazon, soy nuevo por aca y me sorprendio la buena onda de la comunidad :D

nuevamente, gracias!!!!

---

### Post by sdm_cacto on 2007-02-23
Che y q onda esta bueno el juego??? tirame un puntaje del 1 al 7,3 zspikes siendo 1 zspike Basura apestosa y 7,3 zspikes el mejor game

---

### Post by zspikes on 2007-02-23
ahi lo estube probando y la verdad q me envicie mucho jaja. No esta EXCELENTE q digamos, pero tengamos en cuenta q es freeware, tiene como protagonista a tux y muchas otras cosas jaja.

Le pongo un 6,44444444... zspikes

---


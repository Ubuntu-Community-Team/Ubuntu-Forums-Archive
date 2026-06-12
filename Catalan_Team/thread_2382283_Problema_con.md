---
title: "Problema con"
date: 2018-01-11
forum: Catalan Team
---

### Post by erislandy on 2018-01-11
Hola amigos, soy nuevo con Ubuntu, lo estoy utilizando pues debo de instalar un módulo nuevo a un programa que estoy utilizando que se llama gnuradio, al seguir la secuencia de comando para instalar el modulo tengo problema al ejecutar el comando **cmake ..**, aqui les pongo una parte de lo que me devuelve el comando que es donde yo creo que tengo problemas, ya que el resto del codigo esta bien

- Build type not specified: defaulting to release.
-- Found PkgConfig: /usr/bin/pkg-config (found version "0.29.1")
-- Checking for module 'uhd'
-- Found uhd, version 003.008.004-0-g93011c14
-- Found UHD: /usr/local/lib/libuhd.so
-- UHD library found.
-- Looking for pthread.h
-- Looking for pthread.h - found
-- Looking for pthread_create
-- Looking for pthread_create - not found
-- Looking for pthread_create in pthreads
-- Looking for pthread_create in pthreads - not found
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Found Threads: TRUE

Desde mi visión  creo que tengo problemas con el paquete **pthread**, pero segun busque por internet para instalar el mismo debo de ejecutar el comando **sudo apt-get install libpthread-stusb0-dev**, al hacerle ya este paquete se había instalado automaticamente. Tambien tengo duda si la primera linea del codigo arriba estaría bien. Saludos y agradecería cualquier sugerencia

---

### Post by slickymaster on 2018-01-11
Hello erislandy, welcome to the forums.

We have many users from many different countries, and English is the common language of these forums so please write your posts in English. You are permitted to use another language in a [LoCo Forum]("https://ubuntuforums.org/forumdisplay.php?f=183"), if it is in common use in that Loco Forum and understood by the Loco Forum staff.

---

### Post by leunam12 on 2018-01-11
¿Por qué estás instalando de esa manera? Según la página web de gnuradio lo que tienes que hacer es sudo apt install gnuradio.

Why are you installing from source? according to their website all you have to do is ```
sudo apt install gnuradio
```

---

### Post by slickymaster on 2018-01-11
Thread moved to **Catalan Team** for a better fit

Movido a **Catalan Team** para un mejor ajuste

---


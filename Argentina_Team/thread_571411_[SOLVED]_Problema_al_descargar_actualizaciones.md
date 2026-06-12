---
title: "[SOLVED] Problema al descargar actualizaciones"
date: 2007-10-09
forum: Argentina Team
---

### Post by vk-cdg on 2007-10-09
Buenas, abro este post porque tengo un problema que, según las indicaciones que da el mismo Ubuntu, no puedo solucionar.

Estoy intentando descargar algunas actualizaciones que me aparecen como pendientes pero al hacerlo me aparece un error de que hay algo corrupto. Me ofrece hacer un

```
apt-get install -f
```

Al hacerlo me aparece el siguiente error.

```

apalac@vikingo:~$ sudo apt-get install -f
Password:
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo información de estado... Hecho
Corrigiendo dependencias... Listo
Se instalarán los siguientes paquetes extras:
  compiz-gnome
Se actualizarán los siguientes paquetes:
  compiz-gnome
1 actualizados, 0 se instalarán, 0 para eliminar y 28 no actualizados.
1 no instalados del todo o eliminados.
Se necesita descargar 0B/271kB de archivos.
Se utilizarán 1229kB de espacio de disco adicional después de desempaquetar.
¿Desea continuar [S/n]? s
(Leyendo la base de datos ...  
142619 ficheros y directorios instalados actualmente.)
Preparando para reemplazar compiz-gnome 1:0.3.6-1ubuntu13 (usando .../compiz-gnome_1%3a0.5.5~git20070921+3v1ubuntu0_i386.deb) ...
Desempaquetando el reemplazo de compiz-gnome ...
dpkg: error al procesar /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20070921+3v1ubuntu0_i386.deb (--unpack):
 intentando sobreescribir `/usr/lib/compiz/libgconf.so', que está también en el paquete compiz-plugins
dpkg-deb: el subproceso paste fue terminado por la señal (Tubería rota)
Se encontraron errores al procesar:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20070921+3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
apalac@vikingo:~$ 


```

Adjunto también el screenshot del error.

Se agradece de antemano todo cable o ayuda que puedan darme.

---

### Post by Mauro22 on 2007-10-09
Tendrias que entrar a synaptic y arrelgar los paquetes rotos.

o puedes ejecutar sudo apt-get update, para ver si los repositorios estan OK; o alguno esta dando error


Salu2

---

### Post by vk-cdg on 2007-10-09
Muchas gracias!!!

Al final eran los paquetes del compiz-fusion que había querido instalar sin éxito.
Esperaré a tener Gusti en la PC de casa, ya que acá (en el trabajo) con 32mb de ram no puedo hacer mucho.

---

### Post by Mauro22 on 2007-10-09
:guitar: :popcorn:

[SOVLED]

---


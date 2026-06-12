---
title: "emulador de windows 98"
date: 2008-01-13
forum: Argentina Team
---

### Post by sebaxxxtian on 2008-01-13
hola es mi primer post

ayer instale el 7.10 y anda muy gneial, mejor q otras distros q habia probado anteriormente

el tema es q las aplicaciones q uso para trabajar solo corren para windows (tengo instalado en otro disco rigido un w98)

q emulador para w98se me recomiendany donde puedo encontrar informacion sobre su instalacion?

gracias

---

### Post by santiagoward2000 on 2008-01-13
> **sebaxxxtian said:**
> hola es mi primer post

ayer instale el 7.10 y anda muy gneial, mejor q otras distros q habia probado anteriormente

el tema es q las aplicaciones q uso para trabajar solo corren para windows (tengo instalado en otro disco rigido un w98)

q emulador para w98se me recomiendany donde puedo encontrar informacion sobre su instalacion?

gracias

Hola!
Como emulador de Windows yo uso WINE, que tiene la para elegir en la configuración qué versión de Windows querés usar. Podés leer algo más en: [www.winehq.org/]("www.winehq.org/")
O podés instalarlo desde los repositorios de Ubuntu y probarlo. Buscalo en Synaptic, en Add/Remove Applications o abrir una terminal y tipear:
```
sudo apt-get install wine
```
Saludos!

---

### Post by brunovecchi on 2008-01-13
> **sebaxxxtian said:**
> hola es mi primer post

ayer instale el 7.10 y anda muy gneial, mejor q otras distros q habia probado anteriormente

el tema es q las aplicaciones q uso para trabajar solo corren para windows (tengo instalado en otro disco rigido un w98)

q emulador para w98se me recomiendany donde puedo encontrar informacion sobre su instalacion?

gracias

¿Qué aplicación usás para trabajar? Porque hay muchísimas probabilidades de que haya alguna para Linux que te sirva para hacer lo mismo.

---

### Post by sebaxxxtian on 2008-01-13
> **brunovecchi said:**
> ¿Qué aplicación usás para trabajar? Porque hay muchísimas probabilidades de que haya alguna para Linux que te sirva para hacer lo mismo.


trabajo en investigacion de mercado y utilizo survey system 9.0 y spss 14.2.


voy a probar el wine

gracias!

---

### Post by santiagoward2000 on 2008-01-13
> **sebaxxxtian said:**
> trabajo en investigacion de mercado y utilizo survey system 9.0 y spss 14.2.


voy a probar el wine

gracias!

De nada! Contanos si andan!

---

### Post by valucha on 2008-01-13
[COLOR="DarkOrchid"]http://ubuntuforums.org/showthread.php?t=33052 fijate si eso te ayuda... [/COLOR]

---

### Post by sebaxxxtian on 2008-01-14
> **valucha said:**
> [COLOR="DarkOrchid"]http://ubuntuforums.org/showthread.php?t=33052 fijate si eso te ayuda... [/COLOR]


gracias por ese thread. al parecer hay algunos problemas con spss y wine, pero es cuestion de probar. tambien hablaban de R, con el q quiero empezar a experimentar.

cualquier cosa chiflo de vuetla por ayuda.

---

### Post by ojvulluz on 2008-01-18
hola!! yo virtualizaria un w98, con virtualbox, o vmware, que es propietario, pero se "consigue" y anda muy bien.

saludos desde Mendoza.

ojvulluz

---

### Post by sebaxxxtian on 2008-01-22
> **ojvulluz said:**
> hola!! yo virtualizaria un w98, con virtualbox, o vmware, que es propietario, pero se "consigue" y anda muy bien.

saludos desde Mendoza.

ojvulluz

hola,

instale wine pero la verdad no se como hacer correr los softs q necesito.

virtualbox o vmware son mas amigables q wine?

---

### Post by sajnox on 2008-01-22
Virtualbox y Wine son cosas totalmente distintas.

Wine: Es una aplicacion para que los programas hechos para windows funcionen en entorno Linux. Las aplicaciones corren sobre Linux

Virtualbox: Es un programa que crea una computadora virtual en la cual instalas uno o varios SO. Es decir tu maquina arranca con Linux y sobre eso inicias un windows con el consiguiente uso de recursos, pero si. De esta manera logras que ande cualquier soft para windows, salvo juegos y algunas cuestiones graficas muy pesadas.

Espero haber sido lo suficientemente claro (cosa que dudo)

---

### Post by tzulberti on 2008-01-23
> **sebaxxxtian said:**
> 

instale wine pero la verdad no se como hacer correr los softs q necesito.



Primero deberias de configurar el wine usando WineCfg. Eso te va a crear una carpeta .wine en tu home. Ahi adentro hay una carpeta llamada "c:" (o algo similar) y dentro de la misma estan las carpetas de windows necesarias. 

Para correr un programa con wine, tenes que abrir una consola, ir hasta donde este el exe y usar: "wine programa.exe".

---

### Post by sebaxxxtian on 2008-01-23
> **tzulberti said:**
> Primero deberias de configurar el wine usando WineCfg. Eso te va a crear una carpeta .wine en tu home. Ahi adentro hay una carpeta llamada "c:" (o algo similar) y dentro de la misma estan las carpetas de windows necesarias. 

Para correr un programa con wine, tenes que abrir una consola, ir hasta donde este el exe y usar: "wine programa.exe".

y para correr un instalador?

---

### Post by sajnox on 2008-01-23
Para correr un instalador es lo mismo, navegas hasta la carpeta y ahi escribis

wine archivo.exe

Si mal no recuerdo tambien podes hacer click derecho en el archivo y ejecutar con wine

Saludos

---

### Post by sebaxxxtian on 2008-01-23
mil gracias a todos, ahora entendi como funciona wine.

instale survey system 9.0 y ahora estoy probando si corre o no.

---

### Post by niko_3100 on 2008-01-23
No hay forma de instalar dentro de wine el driver de video de windows? Para poder correr juegitos medios truchelis pero que piden el driver??

---

### Post by sebaxxxtian on 2008-01-23
al final instale el survey system y me tiro un mensaje de error que dice q no encuentra un componenete o que es invalido. les mande un mail a los desarrolladores del soft para ver como lo arreglo, pero seguro q es porque no esta corriendo en windows.

---

### Post by tzulberti on 2008-01-23
Postea aca el error. Generalmente, si el mensaje es que no se encuentra algun dll o algo similar, se lo puede bajar de internet y tirar en la carpeta  correspondiente a la instalacion del wine.

---

### Post by sebaxxxtian on 2008-01-23
el mensaje de error es 

run-time error 339

component draglistz.ocx or one of its dependencies are not correctly registered. a file is missing or invalid.

---

### Post by sebaxxxtian on 2008-01-24
instale y reinstale y no hay caso: el wine no me arranca el survey system.

pregunta. puede una aplicacion no correr bajo wine, pero si bajo qemu?

---

### Post by tzulberti on 2008-01-24
La verdad es que del error no tengo ni idea.
Sobre el qemu. El mismo es un emulador como Virtual Box o VmWare. Es decir, tenes que emular todo un windows.

---

### Post by sebaxxxtian on 2008-01-24
voy a probar con qemu, a ver que pasa.

gracias

---

### Post by sebaxxxtian on 2008-01-24
instale qemu y a duras penas pude correr una version de xp (el xp fenix,. si no lo conocen, es un xp reducido armado para pcs de bajo o medio rendimiento). el programa q deseaba correr funciona, pero la ventana del qemu no se puede maximizar y me es imposible trabajar.


despues encotnre en los repositorios el vmware, pero el sistema me dice q mi computadora no soporta el vmware.

conclusion: tendre q trabajar en otra maquina, por ahroa, hasta q de con una solucion.

:(

---

### Post by sajnox on 2008-01-24
Probaste virtual box??

Hasta tiene repositorios para Ubuntu y sinceramente es muy facil de usar

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---


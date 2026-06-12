---
title: "Drivers Nvidia"
date: 2008-04-22
forum: Argentina Team
---

### Post by AzureSky07 on 2008-04-22
Hola a todos,tal como prometi aca estoy jodiendolos otra vez. En este caso es un tema algo recurrente por lo que estuve viendo pero la verdad no hice mas que marearme leyendo los demas asi que pregunto directamente. Tengo una Gforce 6200 en mi maquina y me baje los drivers de la pagina de linux: NVIDIA-Linux-x86-169.12-pkg1.run el tema que despues de dar muchas vueltas para saber como hacia para ejecutarlo desde la consola ( porque me pedia que sea un usuario root ) me encuentro que me tira errores que, disculpen, no recuerdo cuales eran pero hacia muchas menciones al kernel.
Si alguien podria decirme que driver tengo que instalar o que hacer se lo agradeceria mucho.

Saludos AzureSky

---

### Post by Hernán-Amaya on 2008-04-22
probaste instalando envy? a mucha gente le sirvió proba y contanos

---

### Post by sajnox on 2008-04-22
Envy lo podes encontrar en la pagina de su creador

[www.albertomilone.com.ar](www.albertomilone.com.ar)

Es un script que descarga y configura el driver de nvidia o ati

---

### Post by AzureSky07 on 2008-04-22
Lo probare, pero no se si me funcione ya que no tengo internet en mi casa y ahora estoy haciendo esto desde mi trabajo.

---

### Post by sajnox on 2008-04-22
Sin internet en tu casa seguro que no te funciona debido a que por mas que puedas instalarlo no tenes conexcion para descargar el driver. 

Seguramente si te bajas el driver y lo pones en la carpeta que usa envy podes llegar a hacerlo.

---

### Post by MeduZa on 2008-04-23
> **AzureSky07 said:**
> Hola a todos,tal como prometi aca estoy jodiendolos otra vez. En este caso es un tema algo recurrente por lo que estuve viendo pero la verdad no hice mas que marearme leyendo los demas asi que pregunto directamente. Tengo una Gforce 6200 en mi maquina y me baje los drivers de la pagina de linux: NVIDIA-Linux-x86-169.12-pkg1.run el tema que despues de dar muchas vueltas para saber como hacia para ejecutarlo desde la consola ( porque me pedia que sea un usuario root ) me encuentro que me tira errores que, disculpen, no recuerdo cuales eran pero hacia muchas menciones al kernel.
Si alguien podria decirme que driver tengo que instalar o que hacer se lo agradeceria mucho.

Saludos AzureSky

para instalarlo tenes que hacer asi:

1 buteas ubuntu en modo texto (2da opcion del menu de arranque)
2 pones el password cuand otermine de cargar todo
3 cd /home/[tu user]/donde hayas puesto el archivo NVIDIA-Linux-x86-169.12-pkg1.run
4 sh NVIDIA-Linux-x86-169.12-pkg1.run
5 seguis los pasos (si no sabes ingles mm el primero es no)

consejos:
1 guarda el archivo en /home/[tu user] para hacer mas facil
2 cuando te pregunta si queres ver si hay un kernel precompilado decile que no
3 tenes que tener instalado el build-essential sino no te anda.
4 cuando termina de instalar reinicias y tenes que configurar el xorg.conf

Suerte

---

### Post by faktorqm on 2008-04-23
Aca tenes algo grosso tambien pero es para KDE, ojo! 
[http://www.funkblogjob.com.ar/?p=512](http://www.funkblogjob.com.ar/?p=512)

---


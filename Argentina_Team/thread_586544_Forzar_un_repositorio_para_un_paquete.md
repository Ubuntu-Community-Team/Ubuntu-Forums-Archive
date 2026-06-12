---
title: "Forzar un repositorio para un paquete"
date: 2007-10-22
forum: Argentina Team
---

### Post by newtonfn on 2007-10-22
Holas,

Hoy instalé la versión 7.10 y me puse a instalar los programas que necesito, para ello agregué varios repositorios extra-oficiales.
Puntualmente agregué primero download.skype.com y luego al ver que no podía escuchar los malditos archivos wma agregué tambien los repositorios de medibuntu.
El problema es que medibuntu también tiene en el repositorio a Skype y apt concidera que la versión de skype de medibuntu es más moderna (realmente es la misma)

La pregunta es: ¿Como hago para que synaptic ignore medibuntu como fuente de Skype así sigue buscando actualizaciones exclusivamente del repositorio de Skype?
Intenté usar el menú "Package :: Force Version", pero parece no tener efecto. Al hacer un reload de los paquetes me vuelve a saltar el mensajito de que la versión de Medibuntu es más moderna.

¿Alguna sugerencia?
Desde ya muchas gracias

---

### Post by Mauro22 on 2007-10-22
Podes comentar (#) el repositorio de medibuntu en la lista de sources ????


Si podes hacer eso, haces en la consola:

```
sudo apt-get update
```



Y listo, ese repositorio no lo va a tener en cuenta!



No se si es lo que estas buscando!??

Salu2

---

### Post by newtonfn on 2007-10-22
Eso me desactivaría el repositorio de medibuntu, que lo quiero dejar porque hay algunos paquetes que saco de ahí (especificamente el w32codecs)

Gracias igualmente ! 
Saludos

---

### Post by faktorqm on 2007-10-22
cuando se trata de codecs, yo nunca pude igualar la sabiduria del automatix. es malo para muchas cosas, pero los codecs y el plug in para el navegador te lo instala de una. salu2!

---

### Post by clasificado on 2007-10-23
> 
Use pinning to limit the backports repository

You may want to keep your system as close to the normal repositories as possible, and only use the backports when you have to. APT has a mechanism called pinning that will allow you to do this. Assuming you are using Ubuntu 7.04 (Feisty Fawn), save the following text in /etc/apt/preferences (note: this file might not already exist):

```

Package: * 
Pin: release a=feisty-backports
Pin-Priority: 400 

```

This code will set the priority for the 'feisty-backports' archive to 400, which is lower than the default (500), so that apt-get will not automatically upgrade to packages in the backports repository. The line release a=feisty-backports selects packages that belong to the 'Archive' (or 'Suite') called 'feisty-backports'. If you are not using Ubuntu 7.04, look in /var/lib/apt/lists/*_Release to find the values to use in this line.

If you actually want to install packages from the backports, you will have to use the -t (target) option to apt-get. To upgrade a single package e.g. amarok, do this:

```

sudo apt-get install -t feisty-backports amarok

```

(Using -t is equivalent to setting a Pin-Priority of 990, so the priority for feisty-backports packages now beats that for the feisty, and the new version of amarok, with its dependencies, will be installed).

You can also choose a version number of a program to force apt-get to upgrade. You should note that because of the pinning, any dependencies that are required cannot be automatically upgraded in this case. However, if you use 'aptitude' instead of apt-get, its superior dependency handling will usually be able to offer the correct solution e.g.:

```

sudo aptitude install strigi-daemon=0.5.5-2build1~feisty1

```

To see what is available in backports for upgrading, do:

```

sudo apt-get upgrade -u -t feisty-backports

```


salió de acá 
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Me da fiaca traducirlo :P

Clasificado

---

### Post by newtonfn on 2007-10-24
Muchas Gracias Clasificado !

Creo que esto es justamente lo que estaba buscando ! En cuanto este nuevamente en mi box lo probaré. Si el notification-manager se da cuenta de esto y me hace desaparecer el molesto recordatorio de que tengo updates que no quiero me sentiré feliz :)

Saludos,
Fernando

---

### Post by newtonfn on 2007-10-26
Luego de unos cuantos días sin internet logré probar esto y salio a la perfección ! (aunque debi adaptar un poco el precedimiento)

Al final mi archivo /etc/apt/preferences quedó de la siguiente manera

```

Package: * 
Pin: release l=Medibuntu
Pin-Priority: 400

```

No pude usar el a= porque eso especifica por archive, y no se cual es el archivo de Medibuntu.. pero usé el l= que es para especificar por label. (el label lo descubrí revisando el archivo  /var/lib/apt/lists/packages.medibuntu.org_dists_gutsy_Release

Saludos

---


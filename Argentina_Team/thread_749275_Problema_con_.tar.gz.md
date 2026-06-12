---
title: "Problema con .tar.gz"
date: 2008-04-08
forum: Argentina Team
---

### Post by ramiro_md on 2008-04-08
Hola gente del foro, otra vez yo y mi problemas...jejeje...resulta que he bajado un paquete .tar.gz y cuando le doy ./configure en la consola me dice que el comando no existe :confused:

[I]daeron@daeron-lnx:~$ sudo ./configure nuoveXT-1.6.tar.gz
[sudo] password for daeron:
sudo: ./configure: command not found
daeron@daeron-lnx:~$ 
[/I]

si estoy haciendo algo mal por favor digamnee ! desde ya muchas gracias =)

---

### Post by faktorqm on 2008-04-08
Efectivamente estas haciendo algo mal :D

Los archivos de tipo tar.gz son archivos comprimidos, como un .rar, un .zip, .ace, .7z, etc. Primero lo tenes que descomprimir (click derecho -> extraer aqui) (te diria como hacerlo por consola pero estoy apurado, perdon) despues vas a la carpeta y recien ahi haces ./configure.
Lo que no estoy seguro es si necesitas el sudo. Capaz que si, pero no me acuerdo. Intenta usar menos el sudo, recorda que corres las cosas con permisos de "root" (pongo entre comillass por que no es dle todo asi pero bueno) y si ejecutas un script maligno t pueden romper la pc. Salu2!!

---

### Post by oktubrer on 2008-04-08
Para hacerlo por consola, probá
```
tar xvfz nombre_de_archivo.tar.gz
```

Podés obviar la opción "v" que es de "verbose" y te va mostrando en la salida el listado de archivos que va inflando.

---

### Post by ramiro_md on 2008-04-08
Efectivamente faktorqm tenia que descomprimirlo xD gracias.

---

### Post by guisheca on 2008-04-09
Ramiro, eso que tenés entre manos no es un pack de iconos?? deverías de dar detalles al respecto.
Si lo que queres es instalar un nuevo tema de iconos, lo que tenes que hacer es ir a Sistema>Preferencias>Apariencia y simplemente arrastrar el archivo comprimido (ojo, **comprimido** es decir no lo vayas a descomprimir) hasta dicha ventana y listo, ya estará instalado el nuevo pack de iconos que estarán disponibles desde Personalizar>íconos.
Espero no haber metido la pata, pero creo que eso es lo que intentás hacer,
Un saludo

---

### Post by ramiro_md on 2008-04-09
tal cual guisheca..pero al descomprimirlo vi los iconos y no me conformaron mucho x eso no pregunte còmo se instalaban xD igual gracias x la atención =) un abrazo.

---

### Post by guisheca on 2008-04-09
De nada che.

---


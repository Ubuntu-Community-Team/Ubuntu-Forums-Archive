---
title: "msttcorefonts"
date: 2007-11-02
forum: Argentina Team
---

### Post by jorgito on 2007-11-02
Hola a todos!

Me esta pasando lo siguiente: cada vez que se hace una actualizacion salta un problema con los msttcorefonts, asi que intente reconfigurar, reinstalar y remover el paquete, pero siempre con el mismo resultado:

E: msttcorefonts: subprocess pre-removal script returned error exit status 1

En los detalles  siempre lo mismo tambien:

```

jorge@jorge-laptop:~$ sudo apt-get purge msttcorefonts
[sudo] password for jorge:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  msttcorefonts*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 193kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 131105 files and directories currently installed.)
Removing msttcorefonts ...
W: /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Andale_Mono.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Webdings.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Black.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Impact.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Italic.ttf: not registered.
dpkg: error processing msttcorefonts (--purge):
 subprocess pre-removal script returned error exit status 1

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
jorge@jorge-laptop:~$ 



```


Alguien tendra una idea de que es lo que pasa?
La parte interesante parece ser la de el error parseando el proxy.
Aparentemente el proxy esta ok, pero quien sabe???

Bueno, gracias por adelantado y saludos!

---

### Post by rojojuan on 2007-11-02
Las había instalado en la 7.04 y todo bien. Cuando actualicé a Gusty las aceptó y anda todo bien.
Para instalarlas lo había hecho desde Synaptic. 
Si probás desde Synaptic, podría andar?

---

### Post by jorgito on 2007-11-03
No, rojojuan.

Desde Synaptic o  desde consola (haciendo purge, inclusive) es siempre lo mismo. Tambien es lo mismo con cada actualizacion automatica.

Ya se vera.....

Gracias!

---

### Post by meryovi on 2007-11-03
Hola jorgito,

Tengo el mismo problema...

¿Lograste solucionarlo? Porque la verdad me es muy incomodo estar recibiendo ese error siempre...

Muchas gracias!!

---

### Post by Mauro22 on 2007-11-04
Esutve buscando, y encontre esto:

> **Nick Fedchik said:**
> Peoples!!!!
It's not an .exe problem (actually it's self-extracted CAB)
It's not a DNS problem.

The problem is in wget here: (see the /var/lib/dpkg/info/msttcorefonts.postinst file)

```
if ! wget --continue --tries=1 --dns-timeout=10 --connect-timeout=5 --read-timeout=300 $QUIET_ARG --directory-prefix . --no-directories --no-background $URLROOT$ff ; then
```I guess than it's a kind of changes in new wget that unable to work with lots of pre-defined params.
Hope than msttcorefonts package maintainer solve the problem ASAP.
I solve it by change that big line by short 
```
wget $URLROOT$ff
```

```
Por si no saben ingles, o les cuesta entederlo:
abrir el archivo /var/lib/dpkg/info/msttcorefonts.postinst

y cambiar esto:

if ! wget --continue --tries=1 --dns-timeout=10 --connect-timeout=5 --read-timeout=300 $QUIET_ARG --directory-prefix . --no-directories --no-background $URLROOT$ff

por esto:

wget $URLROOT$ff

```A un par dice que se le arrelgo el problema. probalo y conta!

---

### Post by jorgito on 2007-11-05
Gracias, pero no hay caso.
Sigue haciendo exactactamente lo mismo.

saludos!!

---

### Post by meryovi on 2007-11-05
Bueno, a mí me funcionó. :)

Gracias!

---

### Post by jorgito on 2007-11-05
Yo tuve que borrar del archivo la linea que hacia referencia al proxy.
Recien ahi funciono.
Al actualizar se ve que volvio a crear o descargar el archivo modificado,  por lo que no puedo mostrar aca lo que hice.

Saludos  y gracias!

---


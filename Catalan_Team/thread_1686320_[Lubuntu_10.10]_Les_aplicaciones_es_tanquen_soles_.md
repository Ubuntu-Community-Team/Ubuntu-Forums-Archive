---
title: "[Lubuntu 10.10] Les aplicaciones es tanquen soles / Problema amb paquet"
date: 2011-02-12
forum: Catalan Team
---

### Post by yae7 on 2011-02-12
Hola:

estic utilitzant lubuntu 10.10

desde fa uns dies, quan començo a treballar amb alguna aplicació (ja sigui amb el chromium, abiword, etc.) aquestes es tanquen. Com puc saber a què es deu? Per exemple, hi ha algun log com el visor de sucesos en windows? 

No sé si té a veure, possiblement són 2 problemes diferents o no,... però en el synaptic tinc un paquet trencat "**gksu**" (versió 2.0.2-2). Quan l'intento reinstal.lar, em sorgeix error (adjunto captura de pantalla)

---

### Post by wgarcia on 2011-02-12
Penso que el tancament de les aplicacions no pot estar relacionat amb el tema del paquet trencat. 

Per veure perquè es tanquen les aplicacions pot provar d'iniciar alguna des de la terminal i veure si imprimeix algun missatge en tancar-se. El que vull dir és: 1) obre una terminal, 2) entra per exemple "abiword" i enter i ves treballant fins que es tanqui a veure quin missatge et dóna. 

En quant al paquet trencat, prova de córrer des d'una terminal la instrucció següent:

sudo apt-get install -f 

A veure si s'acaba d'instal·lar bé aquest paquet.

---

### Post by yae7 on 2011-02-12
Hola:

ok gràcies per respondre. Probaré lo de obrir el programes desde la terminal.

Respecte a lo de reinstal.lar em surt aquest missatge:

**sorry, try again**:confused:

---

### Post by wgarcia on 2011-02-12
És estrany el missatge que et surt, has entrat sense errors 

sudo apt-get install -f 

a una terminal i després la tecla intro?

Si això no funcionés també pots provar de reinstal·lar el paquet "libcomerr2":

sudo apt-get install --reinstall libcomerr2

---

### Post by yae7 on 2011-02-12
ok, ara si m'agafa la instrucció, i em retorna lo següent:

**sudo apt-get install -f **
[COLOR="Green"]Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Corrigiendo dependencias... Listo
El siguiente paquete se instaló automáticamente y no es necesario:
  libgksu2-0
Utilice «apt-get autoremove» para eliminarlos.
Se instalarán los siguientes paquetes extras:
  libgksu2-0
Se instalarán los siguientes paquetes NUEVOS:
  libgksu2-0
0 actualizados, 1 se instalarán, 0 para eliminar y 1 no actualizados.
2 no instalados del todo o eliminados.
Se necesita descargar 0B/58,2kB de archivos.
Se utilizarán 242kB de espacio de disco adicional después de esta operación.
¿Desea continuar [S/n]? s
dpkg: error en el análisis, en archivo «/var/lib/dpkg/available» línea cercana 12523 paquete «libcomerr2»:
 nueva línea dentro del nombre del campo `
E: Sub-process /usr/bin/dpkg returned an error code (2)[/COLOR]


**sudo apt-get install --reinstall libcomerr2**
[COLOR="green"]Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Tal vez quiera ejecutar 'apt-get -f install' para corregirlo:
Los siguientes paquetes tienen dependencias incumplidas:
 gksu : Depende: libgksu2-0 (>= 2.0.8 ) pero no va a instalarse
E: Dependencias incumplidas. Intente 'apt-get -f install' sin paquetes (o especifique una solución).[/COLOR]


He obert el fitxer i en la zona de la linea 12523:


> Package: libcomerr2
Priority: required
Section: libs
Installed-Size: 104
Origin: Ubuntu
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Architecture: i386
Source: e2fsprogs
Version: 1.41.12-1ubuntu2
Replaces: e2fsprogs (<< 1.34-1)
Provides: libcomerr-kth-compat
Depends: libc6 (>= 2.4)
Filename: pool/main/e/e2fsprogs/libcomerr2_1.41.12-1ubuntu2_i386.deb
Size: 51268
MD5sum: 8ea114349afe7305ddcb039da238ae58
Description: common error description library
 libcomerr is an attempt to present a common error-handling mechanism to
 manipulate the most common form of error code in a fashion that does not
 have the problems identified with mechanisms commonly in use.
p&#65533;^\
$&#65533;: Theodore Y. 

---

### Post by wgarcia on 2011-02-13
Després del reinstall has tornat a fer 

sudo apt-get install -f 

?

---


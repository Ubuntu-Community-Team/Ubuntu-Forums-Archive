---
title: "probremas al intentar instalar wine en ubuntu 8.04."
date: 2008-05-09
forum: Argentina Team
---

### Post by abraxasdne on 2008-05-09
bueno ante de todo soy nuevo en los sistemas linux y con muchas ganas de aprender ^^. 
bueno al intentar instalar el wine con los siguientes comando en consola 

sudo wget [http://wine.budgetdedicated.com/apt/sou](http://wine.budgetdedicated.com/apt/sou) ... hardy.list -O /etc/apt/sources.list.d/winehq.list 

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add - 
sudo apt-get update 
sudo apt-get install wine 

lo ke dio como resultado el siguiente error: 

"Error :Opening the cache(E:type'<!DOCTYPE' is not known on line 1 in sources list/etc/apt/sources.list.d/winehq.list, E:The list of sources could not be read.)" 

error que me impide abrir algunos tipos de aplicaciones, como el gestor de actualizaciones y el gestor de paquetes synaptic. 

bueno espero que puedan ayudarme . 

saludos ^^.

---

### Post by Mister X on 2008-05-09
Lo que estas haciendo es agregar un repositorio para descargar wine, y el archivo donde indica el repositorio esta malformado.
Tenes dos posibles soluciones:
- Eliminar el archivo winehq.list y entonces descargar wine desde los repositorios oficiales

-Corregir el archivo winehq.list y que tenga un formato correcto, si queres postea el contenido para ver cual es el error.

---

### Post by sartrejp on 2008-05-09
Te recomiendo instalarlo desde synaptic, yo no tuve problemas y me funcionan hasta los programas del escaner.
Suerte

---


---
title: "update ubuntu"
date: 2007-07-11
forum: Argentina Team
---

### Post by Miriknell on 2007-07-11
cuando hago un sudo apt-get update me dice...
Leyendo lista de paquetes... Hecho
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 2D6CFB44DD800CD9
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas



obvio q no se soluciona... q puede ser?

gracias

---

### Post by Mauro22 on 2007-07-11
Eso pasa porque agregaste la direccion del repositorio pero no agregaste la clave publica para su verificacion. 


Te acuerdas que instalaste ultimamente??


Salu2

---

### Post by Timbis on 2007-07-11
abre la lista de repositorios (" Sudo gedit /etc/apt/sources.list "), has una copia del mismo y borra la linea que contiene "http://download.tuxfamily.org feisty Release" que es de un programa que instalaste, guarda la lista y dale a " sudo apt-get update". 
Espero que te ayude.

---

### Post by DeadSuperHero on 2007-07-11
I cant speak this language but im glad i got that update command :D thanks lol.

---


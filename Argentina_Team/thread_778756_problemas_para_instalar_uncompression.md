---
title: "problemas para instalar uncompression"
date: 2008-05-02
forum: Argentina Team
---

### Post by rodrigo_johnson on 2008-05-02
Hola:

Que bueno encontrarlos.

Quiero instalar uno de los tres programas disponibles para descomprimir .rar y me aparece este cartel:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Que puedo hacer?

Muchas gracias

---

### Post by Mauro22 on 2008-05-02
> **rodrigo_johnson said:**
> 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


Ahi te lo dice:
Pone sudo dpkg --configure -a en una consola y listo!

---

### Post by rodrigo_johnson on 2008-05-02
Hola:

Hice lo que me dijiste.

Hizo sus cuentas. Pero ahora ciando quiero instalar el programa y hago clik en la lista de programas, se queda pensando y no para de pensar.

Ya reinicie, apague y lo mismo.

Trate de hacer de nuevo lo que me habias dicho en la terminal y ahora dice:

la operación solicitada precisa privilegios de superusuario

Muchas gracias

---

### Post by srmantis on 2008-05-02
instalar programas comprimir/descomprimir:

sudo apt-get install rar unrar p7zip-full

el comando sudo es para que tengas privilegios de superusuario y puedas instalar.
unrar:para descomprimir
7zip: programa free para comprimir y descomprimir varios formatos (zip, etc)

---

### Post by rodrigo_johnson on 2008-05-03
Muchas Gracias:

lo hago y mira lo que pone:

rodrigo@rodrigo-desktop:~$ sudo apt-get install rar unrar p7zip-full
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
rodrigo@rodrigo-desktop:~$ dpkg --configure -a
dpkg: la operación solicitada precisa privilegios de superusuario
rodrigo@rodrigo-desktop:~$ sudo dpkg --configure -a
rodrigo@rodrigo-desktop:~$ sudo dpkg --configure -a
rodrigo@rodrigo-desktop:~$

---

### Post by rodrigo_johnson on 2008-05-03
hola de nuevo:

Trate denuevo desde añadir y quitar programas y pareciera que lo hizo.

ahora estoy bajando un .rar y vere que hace.

Srmantis y Mauro22 Muchisimas gracias

---


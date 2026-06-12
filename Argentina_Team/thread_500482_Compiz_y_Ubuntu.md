---
title: "Compiz y Ubuntu"
date: 2007-07-13
forum: Argentina Team
---

### Post by Miriknell on 2007-07-13
Buenas gente!!!!!
Miren, quise instalar compiz en ubuntu siguiendo los pasos estos:

En kubuntu 7.04 feisty basta con hacer lo siguiente:

**   1. Eliminar, si procede, las anteriores versiones de compiz y/o beryl que tengamos instaladas.**

sudo apt-get remove beryl compiz-core desktop-effects

**   2. Añadir los siguientes repositorios de paquetes en nuestro sources.list (/etc/apt/sources.list)**

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
[B]
   3. Ejecutar lo siguiente en un terminal para añadir la clave gnupg correspondiente a los anteriores repositorios[/B]

KEY=81836EBF; gpg –keyserver subkeys.pgp.net –recv 81836EBF && gpg –export –armor 81836EBF | sudo apt-key add -

  ** 4. Actualizar la base de datos de paquetes de nuestro sistema con los nuevos repositorios añadidos**

sudo apt-get update

**   5. Instalar los siguientes paquetes:**

sudo apt-get install compiz-kde compizconfig-settings-manager libcompizconfig-backend-kconfig emerald emerald-themes compiz-fusion-*

Y ya. Para hacerlo funcionar manualmente basta con ejecutar el siguiente comando (ALt+F2):

compiz --replace -c emerald &

:popcorn:


Cuando agrego los repositorios me tira lo siguiente
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 2D6CFB44DD800CD9

Agrego la key pero me sigue diciendo lo mismo.......
Entonces los update no andan...... alguien sabe porq....???

Gracias, saludos

---

### Post by jpmorelli on 2007-07-14
Cuidado porque a veces las llaves no se instalan bien, hacelo paso a paso o fijate en la administración de los repositorios donde se listan las llaves instaladas si realmente está ahí, a mi ya me pasó un par de veces.
Suerte !

---

### Post by Miriknell on 2007-07-14
> **jmorelli said:**
> Cuidado porque a veces las llaves no se instalan bien, hacelo paso a paso o fijate en la administración de los repositorios donde se listan las llaves instaladas si realmente está ahí, a mi ya me pasó un par de veces.
Suerte !

hola, y como se instalan las Key "paso a paso"? y donde se listan las Key.

Gracias!!!!!

---

### Post by Al_maverick on 2007-07-14
Proba este paso primero, a ver que te dice

gpg &#8211;keyserver subkeys.pgp.net &#8211;recv 81836EBF

---

### Post by Miriknell on 2007-07-15
> **Al_maverick said:**
> Proba este paso primero, a ver que te dice

gpg –keyserver subkeys.pgp.net –recv 81836EBF

Hago un 
 gpg –keyserver subkeys.pgp.net –recv 81836EBF
me dice
uso: gpg [opciones] [nombre_fichero]

Luego de esto, hago un update y me dice
[B]W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 2D6CFB44DD800CD9
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas[/B]


no anda :(

---

### Post by Al_maverick on 2007-07-16
> **Miriknell said:**
> Hago un 
 gpg –keyserver subkeys.pgp.net –recv 81836EBF
me dice
uso: gpg [opciones] [nombre_fichero]

Luego de esto, hago un update y me dice
[B]W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 2D6CFB44DD800CD9
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas[/B]


no anda :(

El tema es que o el tutorial esta mal o copiaste mal los comandos. Pusiste otro simbolo en lugar de los guiones, por eso no lo reconocía.

Proba este:
```
KEY=81836EBF; gpg --keyserver subkeys.pgp.net --recv 81836EBF && gpg --export --armor 81836EBF | sudo apt-key add -
```

---


---
title: "Hola mundo!"
date: 2007-09-25
forum: Argentina Team
---

### Post by fajro on 2007-09-25
Hola gente

Mi primer mensaje en el foro! :KS

Recién ayer firme el CC.. no entendía esto de las llaves pgp (sigo sin entenderlo :-P )

:biggrin:

---

### Post by kowal on 2007-09-25
Bienvenido a bordo, señor.

---

### Post by leo_rockway on 2007-09-25
Hola, bienvenido.

Lo de las claves gpg es mas facil de lo que parece (a mi tb se me complico entenderlo al comienzo).

Basicamente tenes una clave publica y una privada. La clave publica la distribuis para que todo el mundo la tenga y sepa que esa es tu clave publica. Si una persona quiere mandarte un mensaje cifrado utiliza tu clave publica para codificar ese mensaje. La unica forma de decodificar un mensaje cifrado con tu clave publica es usar tu clave privada (que solo vos conoces).

Tb se puede usar para codificar archivos.

---

### Post by faktorqm on 2007-09-26
aaahhhhh asi que ese era el objetivo, mira vos! yo hice todo el proceso siguiendo el tuto que aparece en algun lugar tipo newbie style. jijijijij gracias, salu2!

---

### Post by leo_rockway on 2007-09-26
> **faktorqm said:**
> aaahhhhh asi que ese era el objetivo, mira vos! yo hice todo el proceso siguiendo el tuto que aparece en algun lugar tipo newbie style. jijijijij gracias, salu2!

yo hice mas o menos lo mismo, solo que instale el kgpg para hacer todo el proceso (es mas o menos lo mismo, solo que mas foolproof)

despues me meti en la wikipedia para entender como funcionaban las pgps (aunque yo ya habia tenido un acercamiento cuando todavia estaba en win, asi que algo mas o menos entendia)

---

### Post by Hei Ku on 2007-09-26
El uso más extendido a nivel de usuario es el de firmar los mensajes de mail. Y como nota adicional, Kubuntu Gutsy va a traer configurado el agent de pgp, para firmar automaticamente, (y encriptar, si se quiere) los mensajes de correo. Algo que hoy es un poco engorroso de hacer, pero que es esencial para una comunicación segura.

---

### Post by fajro on 2007-09-26
Y
o ya me instale la extensión FireGPG para Firefox, puedo firmar y cifrar mails pero...

¿Ahora como hago para que los demás puedan descifrar mis mails?

Tengo que pasarles algún código o algo así, ¿no?

---

### Post by Hei Ku on 2007-09-26
Si los encriptas, lo tenes que hacer con la clave publica del destinatario, asi solo esa persona puede verlo. Si lo firmas, lo haces con tu clave privada, y una persona puede comprobar tu firma teniendo tu clave publica (que deberia estar publicada en un servidor publico, no?)

---


---
title: "Permisos en KNetworkManager"
date: 2008-05-05
forum: Argentina Team
---

### Post by armb on 2008-05-05
Hola amigos!
  Tengo el siguiente inconveniente:
En mi notebook HP NX6325, con Kubuntu. para poder conectarme wifi,
 - habilite hardware con driver propietario
 - configure KnetworkManager para iniciar en mi wifi

al iniciar SIEMPRE me pregunta la clave de kwallet para ingresar a la wifi, sino, no me conecta.(ya que le puse clave WEP a la wifi)
Hay alguna forma de hacer esto automaticamente?, ya probe varias opciones en kwallet y KNetworkManager y sigue el problema.
Una mas, tambien me pide clave para poder ver mi disco HD C, con W$ que comparto para usar archivos, donde se cambia eso?.

saludos y gracias por la ayuda.

---

### Post by clasificado on 2008-05-06
> **armb said:**
> Hay alguna forma de hacer esto automaticamente?

¿KWallet no tiene una opción de recordar?

Fijate entre las opciones sinó. A mi me pasaba con mis conexiones FTP, y lo recuerdo solucionado algo como así

clasificado

---

### Post by armb on 2008-05-07
> **clasificado said:**
> ¿KWallet no tiene una opción de recordar?

clasificado

Dentro de kwallet no encuentro ninguna opcion en este sentido
Tambien este tema me sucede con kopete.
sigo buscando...:)

---

### Post by Hei Ku on 2008-05-07
KWallet esta justamente como opcion de seguridad. Te da la posibilidad de juntar todas las claves en un lugar, para solo acordarse de una. Pero justamente te fuerza a meter esa clave al menos una vez. Si lo que quieren es saltearse la clave deberian usar otra cosa, no KWallet.

---

### Post by armb on 2008-05-07
> **Hei Ku said:**
> KWallet esta justamente como opcion de seguridad. Te da la posibilidad de juntar todas las claves en un lugar, para solo acordarse de una. Pero justamente te fuerza a meter esa clave al menos una vez. Si lo que quieren es saltearse la clave deberian usar otra cosa, no KWallet.

exacto
ahora me cayo la ficha, el primer programa que utiliza kwallet, la abre y me pide la clave, en este caso es knetworkmanger, si lo salto, por ejemplo guardando la clave sin codificar, es kopete o el proximo programa que utiliza kwallet, me preguntara por la clave.
El tema es que en kubuntu 7 modifique esto y me dejo de andar la wifi por no se que lio se hizo knetworkmanager y kwallet.

gracias por el aporte
por ahora usare kwallet para las demas pero la de internet no
de esa manera entra automaticamente a la wifi.

salu2

---


---
title: "[SOLVED] inconveniente al querer instalar win teniendo ubuntu"
date: 2008-04-19
forum: Argentina Team
---

### Post by guisheca on 2008-04-19
Que tal muchachos, ya se que es raro el titulo, pero es así. Espero no ofender a nadie, a mi particularmente me molesta cuando se hacen consultas de este tipo.
Resullta que tengo particionado mi disco de 250gb de la siguiente manera:

[IMG]http://i29.tinypic.com/148kl5j.png[/IMG]

En sda1 tengo ubuntu, en sda5 tengo el home, en sda6 tengo una partición ntfs vacía y en sda3 tengo una partición ext3 para probar distros.

El asunto es que quiero instalar winxp en la partición ntfs, para poder jugar call of duty 4 y pes6 que son un vicio, pero al ejecutar el instalador me dice que todo bien con esa partición, pero el mbr está en un lugar que win no reconoce. Claro, está en sda1.

Antes sda6 y sda3 eran una sola partición, en donde estaba winxp, lo que pasa es que yo instalé primero que nada el winxp y después ubuntu. El winxp estaba para jueguis y para mi hermana, pero a mi hermana ahora le compraron una laptop, así que quise redimensionar la partición, ya que solo la uso para juegos, y dejar espacio para otras distros. Pero como ya les digo, winxp me dice que no puede instalar el mbr porque no reconoce la partición.

Alguien podría darme algún dato de como hacer lo que necesito, sin tener que hacer todas las particiones de vuelta?
Gracias.

---

### Post by sajnox on 2008-04-20
Si mal no recuerdo Windows no puede ser instalado en particiones logicas, seguramente por eso no te reconoce la particion.

Tendrias que pasar los datos de la particion sda3 a la sda6, formatear la particion 3 en ntfs y ahi instalar, ya que tampoco podes agregaer mas particiones primarias al disco

---

### Post by facundocorradini on 2008-04-20
A propósito, COD 4 funciona a la perfección a través de Wine.

---

### Post by Mauro22 on 2008-04-20
> **sajnox said:**
> Si mal no recuerdo Windows no puede ser instalado en particiones logicas, seguramente por eso no te reconoce la particion.

Tendrias que pasar los datos de la particion sda3 a la sda6, formatear la particion 3 en ntfs y ahi instalar, ya que tampoco podes agregaer mas particiones primarias al disco


Exacto, windows es caprichoso y solo se instalara en particiones primarias.


:lolflag:

---

### Post by guisheca on 2008-04-21
Muchas gracias a todos por sus ayudas.
Sajnox: Hice lo que me dijiste, e instalé wintendo en sda3 y todo de lujo, ahora disfruto del querido ubuntu (hardy RC) fedora 8 y wintendo.
facundocorradini: Todavía no probé pero seguro que le meto mano al wine y trato de instalar el call of duty 4 ahí.
Muchas gracias comunidad!!!

---


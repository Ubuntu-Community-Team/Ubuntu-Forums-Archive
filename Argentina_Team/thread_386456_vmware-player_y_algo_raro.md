---
title: "vmware-player y algo raro"
date: 2007-03-17
forum: Argentina Team
---

### Post by jajajavi on 2007-03-17
hace unos días que cada vez que actualizo ubuntu me aparece este diálogo. vmware-player aparece pero no puedo marcarlo para instalar/actualizar.  abajo parece que detecta algún conflicto con libdbus... ¿alguien sabe qué es esto? tengo el vmware-player instalado pero aún no lo usé. esto es ubuntu edgy (amd64) kernel 2.6.17-11-generic. en realidad no me molesta pero me gustaría saber de qué se trata. muchas gracias!
[IMG]http://ubuntuforums.org/g/images/225407/1_Pantallazo.jpg[/IMG]

---

### Post by strugart on 2007-03-17
Estuve checkeando varias cosas y descubri que lo que te pasa es que no tenes instalada una dependencia (ahora si me preguntas porque no te la instala sola lo unico que te puedo decir es que podes tener corruptos algunos bits de synaptic que seguro se corrigen en la nueva version). Instalala por synaptic (si podes si no hace apt get con lo que te pide, libdbus).
Cualquier problema postea que vemos.

Strugart

---

### Post by jpmorelli on 2007-03-18
A mi me parece que el paquete en sus comentarios solo está avisando que el motivo de ese upgrade es una incompatibilidad con la librería libdbus .
Si mal no recuerdo el tema de que te quede en modo "grisado" el paquete a instalar está en que si bien Ubuntu ve que en sus repositorios hay una versión más nueva para instalar, vos no lo tenés totalmente activado y hasta me juego a que lo tenés activado pero no tenés instalada la llave clave que vendría a ser algo así como el certificado instalado en tu máquina que se asegura de que el paquete que se está instalando fué hecho por la persona que dice y que no es ningún paquete trucho que perjudique a tu sistema y que simplemente el dueño de esa clave "se hace cargo" de lo que te está mandando... se entendió ? Me refiero a las claves.

---


---
title: "2da pregunta: ¿cómo reutilizar un  disco con sectores corruptos?"
date: 2007-06-04
forum: Argentina Team
---

### Post by marianom on 2007-06-04
El tema es que tengo dos discos (uno de 80gb y otro de 160gb) que me han dado siempre errores (soy ignorante en temas de hardware así que la voy a explicar como yo la entiendo: instalo programas y todo anda bien pero algunos de esos programas se instalan en algún especial del disco y, si bien funcionan, dan fallas de segmentación y similares en forma constante). Es como si algunos sectores de ambos disco no funcionan pero pese a ello, puedo grabar sobre ello y causando errores al intentar utilizar la información.
Reemplacé ambos discos pero ahora los tengo tirados y me dan lástima, la cuestión es que me sobre también una PC (que no tiene disco) y estoy pensando en armar un servidor con todo eso.
La duda es: ¿puedo utilizar esos discos y de alguna manera correr alguna especie de proceso que identifique y clausure los sectores que me han estado dando problemas?
Tener en cuenta que instalaría un SO nuevo para usar esos discos, por lo cual esa información de sectores prohibidos debe quedar permanente.

Gracias por cualquier sugerencia que me puedan hacer,

---

### Post by guillermolisi on 2007-06-05
Hola Mariano

Hasta donde se, cuando el SO (Unix seguro por lo que supongo que Linux tambien) formatea una particion marca las pistas defectuosas y las mapea contra otras "de reserva" sanas. De hecho te pide que reserves un area del disco destinada a guardar este mapa y te pregunta que capacidad le queres dar (medida en cantidad de bad tracks). Con este mecanismo podes utilizar el disco con cierta confianza.

Digo con cierta confianza porque en realidad hay que ver cual es la causa real de las bad tracks. Puede ser la logica del disco, puede ser un problema de degradacion de la superficie magnetica, puede ser que el disco este rayado o con marcas por aterrizaje de los cabezales, etc.

Para no correr riegos los probaria intensamente antes de ponerlos en produccion. SI la cantidad de bad tracks se mantiene y son siempre las mismas, pareceria que el asunto esta estabilizado. Si la cantidad y la ubicacion varian de prueba en prueba, los descartaria.

Estoy suponiendo que no es problema de controladora.

Saludos

---

### Post by jayflower on 2007-06-05
Hola Marianom, si sabés en qué cilindro del disco están los sectores, podés particionar el disco y dejar esas particiones inactivas. Si no son las areas donde está sector de arranque.

---

### Post by marianom on 2007-06-05
Estimados Guillermo/Florencia,
gracias por sus aportes. Les cuento que en otro lado también me sugirieron que tenga en cuenta los comandos badblocks y mke2fs -c para que se guarde registro de los bloques defectuosos.

Espero que los sectores, como ustedes bien comentan, sean fijos porque si no será cuesta arriba poder utilizar esos discos.

Un saludo.

---


---
title: "Habilitar aplicaciones al root"
date: 2007-07-09
forum: Argentina Team
---

### Post by ideafix on 2007-07-09
hola gente, queria saber porque cuando entro como root en ubuntu 6.06 tengo menos aplicaciones disponibles que cuando entro con el usuario creado en la instalacion, y como hago para que root tenga las aplicaciones disponibles. Desde ya gracias!!!!

---

### Post by Al_maverick on 2007-07-09
es por como se crearon los menus, pero en realidad podes correr las mismas aplicaciones. 

**La pregunta seria por que queres correr aplicaciones como root? **Eso es algo que deberias hacer **solamente** en situaciones muy particulares, y como regla general, por el tipo de uso del root, no deberias permitir que tenga acceso a una sesion grafica. Ni hablar de usarlo para navegar por internet, o abrir un .pps
El default de ubuntu es que el root no este habilitado, y es una buena medida de seguridad, con varias razones.
En lo posible deberias utilizar sudo, que habilita la posibilidad de correr comandos como root con un tiempo muy limitado.
Mas alla de esta advertencia general, que es lo que quieres hacer que necesitas login como root?

---

### Post by ideafix on 2007-07-09
pues tienes razon con el tema seguridad. Lo que pasa es que la unica manera de acceder al disco NTFS es como root (como el otro usuario lo veo, pero no puedo leerlo), y queria ver unos videos, me pidio bajar unos paquetes, y ahi vi que no habia synaptic ni nada de eso. En realidad veras que es flojera de no salir, volver a entrar como root, descubrir que falta algo, salir... En fin, estoy viendo en hacer upgrade a otra version que soporte ntfs-config para que no haya tanto drama. Gracias por la respuesta

---

### Post by Al_maverick on 2007-07-09
Tres o cuatro threads por debajo de esta, está la misma consulta. Muchos tenemos particiones ntfs y no necesitamos entrar como root.

Fijate aqui: [http://ubuntuforums.org/showthread.php?t=496917](http://ubuntuforums.org/showthread.php?t=496917)

---


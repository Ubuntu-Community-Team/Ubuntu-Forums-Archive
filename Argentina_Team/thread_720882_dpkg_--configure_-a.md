---
title: "dpkg --configure -a"
date: 2008-03-10
forum: Argentina Team
---

### Post by fedescha on 2008-03-10
Tengo un pequeño problema. Cuando quiero instalar un paquete (Gdeb), luego de pedirme la clave me aparece un cartelito con el siguiente mensaje:  Solo se permite la ejecucion simultanea de una unica herramienta de gestion de softwere. Cierre cualquier otra aplicacion como "gestor de actualizaciones", "aptitude" o "synaptic".

No tengo nada mas abierto. Arrastrando una vieja costumbre reinicie la maquina y sigue la misma historia. Cuando hago $ sudo aptitude install <nombre> me da el siguiente mensaje: dpkg was interrupted, you must manually run "dpkg --configure -a". Cuando corro ese instruccion copiandola tal cual me dice que tengo que ser root. Que yo sepa soy root, pues soy el unico usuario.
Que puedo estar haciendo mal? Si no soy root, como puedo serlo? Hago mal ejecutando la instruccion tal cual la escribo?
Gracias de antemano, saludos,

---

### Post by Mauro22 on 2008-03-10
Vos no sos root, sos un usuario "limitado"

Para correr ese comando con** privilegios** de root, ponele antes "sudo"

sudo dpkg --configure -a

sudo, viene de superuser do o superusuario haz.

---

### Post by Apokalyptica79 on 2008-03-11
Hola  fedescha, en todo caso logueate como root y tratá de correrlo de esa manera a ver si te sigue tirando algún error.
Suerte y éxitos.

---

### Post by sajnox on 2008-03-11
> **Apokalyptica79 said:**
> Hola  fedescha, en todo caso logueate como root y tratá de correrlo de esa manera a ver si te sigue tirando algún error.
Suerte y éxitos.

No te podes loguear como root en ubuntu salvo que lo habilites especialmente, y no se lo recomendaria a un usuario nuevo.

Por algo Ubuntu esta hecho asi.

---

### Post by dondionisio on 2008-03-11
Dos detayecito más, importantes pa' un principiante:
- Cada vez que "sude", el terminal le va a pedir que ponga la clave de aceso (es la mesma que ha usao pa' intalar el Linu)
- Pa' que sea efetiva la orden **sudo dpgk -- configure -a** no se olvide que tiene que estar la máquina conetada a Interné (porque tiene que bajar y atualizar paquetes)

Dionisio Rearte
Desperto Informático Crioyo
[www.ciberrancho.com.ar](www.ciberrancho.com.ar)

---


---
title: "OT: Patch TightVNC sin password"
date: 2008-02-25
forum: Argentina Team
---

### Post by jclevien on 2008-02-25
Hola,

Perdón por el OT, estuve haciendo los deberes pero no encontré información ni en las man, ni en el sitio de TightVNC.

Lo que necesito es simplemente esto: ¿como arranco un servidor TightVNC en un Ubuntu pero SIN que pida clave? El mismo me fuerza a escribir una clave, pero no encontré un parámetro de línea de comandos para que ni se fije si hay clave.

La otra sería aplicar un patch, pero ni idea si existe algo para esto (debería haber una opción, me parece ilógico anular una opción como pedir password).


Gracias.


Juan

---

### Post by jclevien on 2008-02-25
Listo, me contesto yo solo.

Al que le interese:

Para lograr esto, estuve viendo que no hay un parámetro en TightVNC para ignorar el password, por lo que decidí patchear el fuente de esta forma:

(versión 1.3dev7 bajada de SourceForge):

1. En el archivo auth.c ( vnc_unixsrv/Xvnc/programs/Xserver/hw/vnc/auth.c), buscar la línea 55 y cambiar:

securityType = rfbSecTypeVncAuth;

por

securityType = rfbSecTypeNone;

2. Compilar normalmente (primero xmkmf, make World en la raíz del fuente, y luego configure, make en el directorio Xvnc.)

3. En la raíz del fuente, correr el vncinstall para instalar los binarios.


Nota: el truco funciona siempre y cuando haya un fichero passwd creado.


Saludos.



Juan

---


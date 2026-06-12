---
title: "[SOLVED] Actualización de Wine"
date: 2007-11-11
forum: Argentina Team
---

### Post by Vero1 on 2007-11-11
Hola a todos,

Desde ayer recibo aviso de una actualización para Wine, pero cuando le doy el ok para la descarga me sale este aviso:

W: Falló al obtener [http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.48~winehq0~ubuntu~7.10-1_i386.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.48~winehq0~ubuntu~7.10-1_i386.deb)
  404 Not Found

Qué puedo hacer?

Gracias y saludos:)

---

### Post by Can+~ on 2007-11-11
Los servidores que usan en wine no son muy solidos para toda la carga que reciben, una vez tuve que pedir un update 5 veces hasta que me lo mandó.

:KS

---

### Post by Vero1 on 2007-11-11
Hola,

Gracias por tu respuesta. Seguiré probando en los días siguientes.

:)

---

### Post by facundocorradini on 2007-11-11
De hecho, en su mismo website dicen que tiran el aviso antes y luego hacen el paquete en el repositorio (no estoy seguro de para que), así que a quieren les pase esto solo deberán esperar unos días y luego darle actualizar.

slds

---

### Post by Vero1 on 2007-11-11
facundo,

el error hace mención a 404, lo cual indica que esta página no es encontrada por el Servidor.

De todas formas gracias y esperaré unos días.

saludos

---

### Post by clasificado on 2007-11-12
Podes bajarte directamente el deb. No sera tan comodo pero bue

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Clasificado

---

### Post by Vero1 on 2007-11-12
Gracias clasificado. Ya lo hice.
Ahora, cómo puedo comprobar si se ha agregado?

Y cómo puedo eliminar el aviso?

---

### Post by clasificado on 2007-11-12
Por la comprobación, ejecutate 
```
wine --version
```

Por la actualizacion, se me ocurre que podes ir con el synaptic, buscar el paquete WINE, y darle a la opcion de menu "Bloquear version"

Clasificado

---

### Post by Vero1 on 2007-11-12
clasificado, me dice:

Wine 0.9.46.

Ahora, si está ok, cómo hago para que deje de avisarme sobre esta actualización?

gracias

---

### Post by facundocorradini on 2007-11-12
Hola

Hoy se habilitó la descarga desde el repositorio de wine. Yo lo acabo de actualizar desde ahí.

---

### Post by Vero1 on 2007-11-12
Hola facundo,

Gracias.

Ahora, una vez descargado, se integra solo a Wine o hay que hacer algo?

---

### Post by Vero1 on 2007-11-12
despreocupate ya que lo instalé con sudo apt-get install wine(me dije voy a probar:).

Confirmé la versión.

Muchas gracias a vos.

saludos

p.d.
desapareció el aviso de actualización por suerte.

---


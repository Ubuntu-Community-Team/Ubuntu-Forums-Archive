---
title: "Volver al kernel de Feisty"
date: 2007-12-14
forum: Argentina Team
---

### Post by loopeando on 2007-12-14
Tengo una duda.

¿Se puede instalar el kernel que viene por default en Feisty en Gutsy?

El tema es que yo tengo una laptop con una placa de sonido HDA Intel, que sufre de problemas de jack sense, y ya me canse de no poder poner musica fuerte en los auriculares sin que los que estan alrededor mio se quejen por la distorsion de los parlantes internos.

En conclusion, si es posible, ¿como instalo el kernel de Feisty en Gutsy?

Gracias!

---

### Post by marianom on 2007-12-14
No me parece buena idea, el kernel no es un programa más. Para eso, reinstala Feisty, te vas a ahorrar algunos dolores de cabeza.
Igual si lo queres hacer, bajate el kernel de [este lugar]("http://packages.ubuntu.com/"). Fijate las dependencias ya que lo que correcto es reemplazar todo. Además del linux image (el common y el de corresponda a tu arquitectura) bajate el restricted modules y nvidia kernel common (es lo que me acuerdo ahora).
Mi sugerencia es que practiques un poco antes: instala el ubuntu server en un virtualizador (a mi me gusta qemu) y proba hacerlo ahi: no trae naa, solo linea de comandos pero esencialmente lo que tenes que hacer es bajarte los paquetes y luego dpkg -i nombre. Si te falta algo, el instalador te va a avisar. Si te sale bien en el virtualizado y reinicia sin kernel panic, con red y todo de lujo dale nomás con tu cambio.

---

### Post by clasificado on 2007-12-17
Yo secundo al muchacho: Instalate fiesty y usá los Backports para actualizar lo que quieras a lo mas nuevito.

Clasificado

---


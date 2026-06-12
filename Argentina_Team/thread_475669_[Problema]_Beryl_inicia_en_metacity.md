---
title: "[Problema] Beryl inicia en metacity"
date: 2007-06-16
forum: Argentina Team
---

### Post by dj termitu on 2007-06-16
Buenas gente, tengo un amigo que tiene un problema que no se lo pude solucionar :@
Él tiene la distribución ubuntu, con beryl (placa nvidia) + screenlets
Le pasa lo siguiente:
hasta hace muy poco le iniciaba todo bien, los screenlets normalmente
Pero ahora lo que sucede es que se inician los screenlets con un fondo negro y lo que tiene que hacer es "Kill Daemon" luego pasar el gestor de ventanas de metacity a beryl (si, se inicia en metacity!) y luego abrir denuevo los screenlets.

Alguien sabe como solucionar este problema? qué es lo que está causando esto?

PD: sacó "screenlets-tray" del inicio (o sea que ya no se inicia automaticamente) y esto se solucionó. Pero él no lo quiere inciar todos los días manualmente.
Hay alguna forma de que "screenlets-tray" se inicie por ejemplo 5 segundos después que beryl?

---

### Post by spg76 on 2007-06-16
Screenlets está en una etapa de desarrollo muy temprana (va por la versión 0.0.7) y por lo tanto le falta un tiempo para que sea totalmente estable.
Además, según mi experiencia, screentlets-tray causa algunos problemas extras.
Para cambiar el orden de inicio de screenlets anda a "Sistema > Preferencias > Sesiones", y en donde dice "Sesión actual", hay una columna que dice "Orden".
Otra forma que podría funcionar es poner en el inicio "screenletsd" en lugar de "screenlets-tray".

---

### Post by undiaperfecto on 2007-06-18
igualmente no le hace falta hacer kill o stop daemons, pasando de metacity a beryl se acomodan solas.
el tema de que te cargue metacity en lugar de beryl ya desconozco,

---


---
title: "Problemas con NVIDIA"
date: 2007-10-12
forum: Argentina Team
---

### Post by pablo0469 on 2007-10-12
Hola, gente, anoche instale una GeForce 5200, Feisty me la pesco, le habilite el controlador "glx-nvidia", y desde entonces no pude entrar mas porque me salta que esta "deshabilitado el servidor grafico". Busque soluciones pero ninguna me ha dado resultado. Desde ya muchas gracias a todos.

---

### Post by Mauro22 on 2007-10-12
Si te deja entrar al modo grafico con la consola bajate el "nvidia-glx-new"

No me acuerdo si es asi o glx-nvidia-new

Tampoco se si estan en los repos de Fesity, pero con probar no perdes nada!

---

### Post by pablo0469 on 2007-10-12
No me deja entrar al modo grafico. Una de las cosas que intente fue justo reinstalar glx-nvidia, ya que el "new" es el propietario si mal no recuerdo y no esta en los repositorios oficiales. Voy a intentar de nuevo modificando el orden de arranque de BIOS, aunque ya lo hice sin fortuna. Gracias por la pronta respuesta.

---

### Post by Mauro22 on 2007-10-12
entra en modo texto, y edita el xorg.con en la carpeta /etc/X11, busca donde dice "nv" o "nvidia" y ponele "vesa" y reinicia


Ahi tiene q entrar seguro

---


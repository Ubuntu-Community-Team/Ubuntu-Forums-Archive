---
title: "[Ubuntu 19.04] - Servicio o script al inicio"
date: 2019-07-25
forum: Argentina Team
---

### Post by gonzaloleon on 2019-07-25
Hola, buenas y santas!
Hace unos días me pasé a Ubuntu 19.04 y estoy intentando restablecer lo que tenía en otra distro.
Puntualmente estoy con un inconveniente intentando ejecutar un script (.sh) que arranca "svnserve -d -r <repo>" al inicio, creado y con permisos en /etc/init.d/ y luego aplicado con update-rc.d <script> defaults y sin resultados (el comando update-rc.d no devuelve error, por lo menos a la vista).
Lo intenté también creado un servicio "svnserve.service y tampoco.
Alguien podrá, amablemente, ayudarme con éste inconveniente por favor.
Muchas gracias!

---

### Post by aromo2 on 2019-07-25
Tienes que crear un servicio en systemd (diferente de sysV). Para darte una idea, tienes que crear svnserve.service en /etc/systemd/system, luego ejecutar ```
systemctl daemon-reload
``` para que tome los cambios. Solo entonces podras habilitar el servicio ```
systemctl enable svnserve
``` e iniciarlo ```
systemctl start svnserve
```

---

### Post by gonzaloleon on 2019-07-25
> **aromo2 said:**
> Tienes que crear un servicio en systemd (diferente de sysV). Para darte una idea, tienes que crear svnserve.service en /etc/systemd/system, luego ejecutar ```
systemctl daemon-reload
``` para que tome los cambios. Solo entonces podras habilitar el servicio ```
systemctl enable svnserve
``` e iniciarlo ```
systemctl start svnserve
```

Muchas gracias por la respuesta.

Me pasa lo siguiente:
```
Synchronizing state of svnserve.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable svnserve
update-rc.d: error: svnserve Default-Start contains no runlevels, aborting. 
```

---


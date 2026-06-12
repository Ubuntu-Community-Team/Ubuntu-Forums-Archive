---
title: "Acceso directo internet"
date: 2007-06-03
forum: Argentina Team
---

### Post by Apipote on 2007-06-03
Me pasa algo muy desagradable. Cuando configuro el pppoeconf, para conectarme a internet, al reiniciar tengo que repetir el proceso de pppoeconf.
Tiene que haber alguna manera de automatizarlo o poner un acceso directo en el escritorio, o alguna aplicacion que me conecte facilmente.

Tambien, querria un visor para pps, ya que instalar oppenoffice en mi xubuntu para eso seria demasiado.

Les ruego me ayuden.
Gracias.

---

### Post by spg76 on 2007-06-03
Podes probar lo siguiente, una vez que configuraste la conexión con pppoeconf, tipea:

```
sudo chattr +i /etc/resolv.conf
```

Este hace que el archivo que tiene los datos de la conexión, resolv.conf, no pueda ser modificado, salvo por ciertos procesos o por el usuario root.

---

### Post by elrengo79 on 2007-06-03
si tu problema es que no sabes como conectarte, simplemente tenes que abrir una consola y poner:
pon dsl-provider
Tambien podes configurar con el pppoeconf que se conecte automaticamente cuando inicia la pc.

---

### Post by Apipote on 2007-06-03
Che, parece que funciona............
Buenísimo!!!!!
Y con el pps viewer, ( uso amd x64 ) alguna sugerencia?

---


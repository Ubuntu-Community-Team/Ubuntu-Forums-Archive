---
title: "problema actualizando un paquete (compiz-core)"
date: 2007-10-16
forum: Argentina Team
---

### Post by JoACoV on 2007-10-16
Hola acudo a ustedes que son unos capos para plantearles este problema:

ubuntu me dice que tengo una actualización pendiente, concretamente el paquete compiz-core:
```

compiz-core (versión1:0.5.2+git20070918-0ubuntu5~ppa1) será actualizado a la versión 1:0.5.2+git20070918-0ubuntu5~ppa1
```

pero parece que esta teniendo una falla al hacerlo y se queda "trancado" (a pesar de que la ventana dice qeu se ha actualizado con exito). si cierro la ventana, el gestor de actualizaciones sigue diciendo que tengo una actualizacion (la misma) pendiente

les dejo lo que me tira la consola en el attach

---

### Post by por100pre1 on 2007-10-16
Prueba cerrando el gestor de actualizaciones y prueba esto:

```
sudo aptitude update && sudo aptitude upgrade
```

```
sudo dpkg-reconfigure compiz-core
```

---

### Post by toXor on 2007-10-16
Me parece que es un problema con los repositorios. Saca los repositorios que usaste para instalar Compiz del sources.list y te va a dejar de tirar el update.

---


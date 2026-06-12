---
title: "musica en varios usuarios"
date: 2007-10-26
forum: Argentina Team
---

### Post by dj_isaco on 2007-10-26
hola a todo les queria hacer uns pregunta sobre como puedo reproducir la musica de un usuario en otro, ya q toda la musica q tengo en mi compu esta en mi secion y cuando entro por la de mis hermas no puedo ver nada.
intente compartirla pero me faltan unos paquetes y me da la obcion de samba y tengo entendido q sirve para compartir entre redes,o tambien entre usuarios se los agradecere si me guian por donde seguir

---

### Post by Hernán-Amaya on 2007-10-26
create un grupo, y uní a ese grupo a tus hermanas y a vos claro esta, después en  le cambias los permisos a la carpeta donde tenés la musica para que la puedan ver los que pertenecen al grupo que creaste con anterioridad. 

espero haber sido claro, y si no pregunta de nuevo que fue lo que no entendiste

suerte!!

---

### Post by sajnox on 2007-10-26
Te agrego un consejo, los permisos los podes cambiar con la consola o desde nautilus (para hacerlo con nautilus tenes que ejecutarlo con permisos de root)

```
 $ sudo nautilus
```

---

### Post by dj_isaco on 2007-10-28
gracias por las soluciones, me sirvieron.:)

---

### Post by MeduZa on 2007-10-28
> **sajnox said:**
> Te agrego un consejo, los permisos los podes cambiar con la consola o desde nautilus (para hacerlo con nautilus tenes que ejecutarlo con permisos de root)

```
 $ sudo nautilus
```

no te aconsejo esta forma, es mejor la de los grupos

---

### Post by sajnox on 2007-10-28
Si, pero para cambiar los grupos desde Nautilus, si el no es el dueño de los archivos necesita permisos de root (y siendo un usuario nuevo puede ser mas facil desde la forma grafica)

---

### Post by clasificado on 2007-10-29
> **sajnox said:**
> Te agrego un consejo, los permisos los podes cambiar con la consola o desde nautilus (para hacerlo con nautilus tenes que ejecutarlo con permisos de root)

```
 $ sudo nautilus
```

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

En esa pagina, recomiendan nunca usar sudo para herramientas que tengan entorno grafico

Siguiendo ese consejo, la instruccion seria
```
 $ gksudo nautilus
```

Clasificado

---


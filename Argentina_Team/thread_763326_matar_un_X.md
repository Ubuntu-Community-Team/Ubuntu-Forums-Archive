---
title: "matar un X"
date: 2008-04-22
forum: Argentina Team
---

### Post by MeduZa on 2008-04-22
Hola gente, tengo una duda y no consigo la respuesta (tampoco se muy bien como buscarla :( )
la cuestion es esta, yo setie mi ubuntu (8.04) para que habilite acceso a mi user a otros X, por ahi todo bien, entonces cuando cargo un juego lo cargo en otro X para que no se meta con mi desktop y ademas gane performance.
Eso lo hago con un archivo bash o directamente desde el laucher, la cuestion es que no se como matar el X una vez que termino de usar la aplicacion / juego

mi sh seria algo asi:

```
#!/bin/bash
X :3 -ac -br +kb  & # lanzo un X nuevo en la 3 por ejemplo
sleep 2 &  # espero 2 segundos para que todo este ok
DISPLAY=:3 ./aplicacion # lanzo mi aplicacion
```

hasta aca todo perfecto mi aplicacion se abre en la X 3 (control alt F10) pero si salgo del programa el X queda abierto y si lanzo otra aplicacion de la misma manera da un error, entonces lo que necesito saber son 2 posibles cosas:

como hago para que el X 3 muera cuando cierro la aplicacion, o como hago para no crearla de nuevo si ya esta creada?
la verdad no encuentro la respuesta :( me lei el help y probe algunos comandos pero nada, no se muere.
Gracias

---

### Post by faktorqm on 2008-04-23
Hola, no es tan simple como poner "ps -ax" en una consola y mirar el pid que se correponde con el 3 y cerrarlo?
Igual supongo que buscas una solucion mas profesional jajaja pero en un principio eso deberia funcionar.
No encontre nada che, tire "how to kill X session", "Xorg manual", "Xorg how to", salio cualquier cosa menos como cerrar. Despues me fijo mejor. Salu2!

---

### Post by MeduZa on 2008-04-23
> **faktorqm said:**
> Hola, no es tan simple como poner "ps -ax" en una consola y mirar el pid que se correponde con el 3 y cerrarlo?
Igual supongo que buscas una solucion mas profesional jajaja pero en un principio eso deberia funcionar.
No encontre nada che, tire "how to kill X session", "Xorg manual", "Xorg how to", salio cualquier cosa menos como cerrar. Despues me fijo mejor. Salu2!

si ahora la forma que lo hago es abrir el system monitor y buscar el xorg X:3 y matarlo pero la idea es algo automatico. voy a seguir buscando.

---

### Post by oktubrer on 2008-04-23
Probá con pkill que lo mata por el nombre del proceso, calculo que será siempre el mismo.

---

### Post by MeduZa on 2008-04-23
> **oktubrer said:**
> Probá con pkill que lo mata por el nombre del proceso, calculo que será siempre el mismo.

no me fije si es siempre el mismo, porque si le erro y mato al otro me quedo sin desktop XD

voy a probar, pero no se como automatizar eso, hagan de cuenta que tiene que ser en un BASH y no en la consola, sino que gracia tiene, lo sigo cerrando a mano desde el system monitor.

---

### Post by faktorqm on 2008-04-24
Hubieras dicho antes! Yo pense que lo querias cerrar tipo "con un boton" (aunque se puede :D)

```
 kill -9 $(ps aux | awk '$1 ~ /ACA_VA_TU_NOMBRE_DE_USUARIO/ {print $2}')
```

Proba eso, si queres primero proba

```
ps aux | awk '$1 ~ /ACA_VA_TU_NOMBRE_DE_USUARIO/ {print $2}'
```

y fijate si te devuelve bien el proceso, si te lo devuelve bien, ahi ya tenes el comando. Sino lo vemos. Salu2!

---

### Post by MeduZa on 2008-04-24
voy a probar tu solucion porque:

X :3 -ac -terminate #no hace nada
y

DISPLAY=:3 kill x # no deja nada vivo xD

---


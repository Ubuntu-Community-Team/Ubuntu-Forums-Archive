---
title: "desinstalar todo"
date: 2007-08-18
forum: Argentina Team
---

### Post by .NicK_LoVe on 2007-08-18
Hola gente!!! Alguien conoce una forma (si es que existe) de dejar el sistema como recien instalado???? Ya que estuve jugueteando mucho con las descargas y me quedo todo medio enquilombado. jeje
Aclaro q es la primera vez que instalo un linux y me pienso quedar para siempre!!!!:guitar:

---

### Post by rojojuan on 2007-08-18
Sistema-Administración-Synaptic-Roto. 
Te muestra los paquetes que quedaron rotos.

---

### Post by sajnox on 2007-08-18
recieninstalado = reinstalado = reinstala :)

Si queres evitar volver  bajar los paquetes que bajaste usa apton cd (hace un backup en un archivo .iso de lo paquets que bajaste)

$ sudo apt-get install aptoncd

Te lo agrega en sistema / Administracion / Aptoncd

Saludos,

---

### Post by por100pre1 on 2007-08-18
Bueno, una forma seria abrir el Gestor de paquetes Synaptic mirar bajo Archivo> Historico. Tambien puedes simplemente remover lo que no deseas y limpia culaquier paquete residual con este comando en terminal:

```
sudo apt-get autoremove
```

Espero que esto te sea util. :)

---

### Post by v1ncent on 2007-08-19
Por eso siempre es recomendable tener el directorio /home en otra partición, para no tener tus archivos personales junto a la particion en donde está realmente el sistema.

Si lo tuvieras de esa forma, entonces instalas ubuntu el la particion de sistema (formateando, obviamente) y designas la particion en donde esta tu /home, como /home del sistem (sin formatear).

---

### Post by clasificado on 2007-08-27
No hay un ayudante para eso, pero tampoco es herejia.

1) Encendes un Live CD
2) montás el disco rígido.
3) Haces percha todo menos el /home
4) Instalas de nuevo

Clasificado

---


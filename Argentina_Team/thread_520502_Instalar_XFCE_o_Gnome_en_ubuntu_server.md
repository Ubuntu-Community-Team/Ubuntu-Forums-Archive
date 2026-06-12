---
title: "Instalar XFCE o Gnome en ubuntu server"
date: 2007-08-08
forum: Argentina Team
---

### Post by aceki on 2007-08-08
Gente consulta como hago para instalar algun gestor de ventas (preferentemete los que puse arriba) en ubuntu server, me baje los paquetes de xubuntu-desktop y nda, tambien lo mismo con ubuntu-desktop, y nda, alguien me dice que paquetes hay que bajar desde ya muchas gracias.

---

### Post by por100pre1 on 2007-08-08
```
sudo /etc/init.d/gdm restart
```

Mira a ver si te resulta eso... :)

---

### Post by aceki on 2007-08-08
lo que quiero saber que paquetes nesecito, por que algo me falta, el servidor es un p3 650 (2 procesadores) 256 Mb de ram, placa de video 2 Mb, supongo que el XFCE deveria andar.

---

### Post by SLA_leandrin on 2007-08-08
Buscate todos los paquetes xfce4.

Abrí la consola y poné;

```
sudo apt-get install xfce4
```

y dale tab para que te salgan las opciones. Instalalas a todas, menos las dev si no te interesa.

Saludos.

---

### Post by faktorqm on 2007-08-09
Hola, cada vez que quieras instalar algo y no sepas como se llama el nombre del paquete, tenes que hacer:

```
aptitude search <nombre del paquete>
```

Entonces, si queres instalar xfce4 tendras que poner:

```
aptitude search xfce
```

entonces buscas por la cadena de caracteres. (EN LOS REPOSITORIOS, por supuesto) si el programa NO esta en los repositorios de ubuntu o la version es vieja (caso FUSE y FUSE-UTILS) lo tenes que instalar con otro tipo de cosas, como autoconf, auto install, o compilarlo directamente.

Si queres reinstalar un programa, tenes que escribir:

```
sudo apt-get install <nombre del paquete> --reinstall
```

entonces se fija si ya lo bajo, si lo tiene lo reinstala, sino lo vuelve a bajar. si la configuracion persiste por algun motivo tambien podes hacer antes de reinstalar:

```
sudo apt-get remove <nombre del paquete> --purge
```

Si queres compilar un programa y por algun motivo no podes hace esto:

```
sudo apt-get install build-essential
```

Espero que te haya servido. Salu2!!

---

### Post by lavaramano on 2007-08-11
si ya bajaste el xfce y el gnome, proba con startx
te deberia levantar las X, y si no es asi, te debe faltar el paquete xorg (pero no creo)

---

### Post by lugonesjoaquin on 2007-08-11
Necesitas:

x-window-system
xfce4 o gnome-core (Depende cual quieras instalar)
gdm o xdm (Gestor de login grafico, si quieres)

---


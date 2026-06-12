---
title: "Affinity no se ve bien en XFCE"
date: 2007-09-09
forum: Argentina Team
---

### Post by santiagoward2000 on 2007-09-09
Hola todos,
Hoy instalé Affinity, pero cuando quiero correrlo, se ve mal. Acá les dejo una imagen:
[[IMG]http://img505.imageshack.us/img505/2509/screenshot1jr8.th.png[/IMG]]("[URL=http://img505.imageshack.us/my.php?image=screenshot1jr8.png)"][[IMG]http://img505.imageshack.us/img505/2509/screenshot1jr8.th.png[/IMG]](http://img505.imageshack.us/my.php?image=screenshot1jr8.png)[/URL]

Cuando lo abro desde una Terminal, despues de revisar algunas carpetas, me manda estos errores:
(affinity:7382): GLib-CRITICAL **: g_dir_read_name: assertion `dir != NULL' failed

(affinity:7382): GLib-CRITICAL **: g_dir_close: assertion `dir != NULL' failed
Application Engine : Scanning /usr/share/applications
Application Engine : Scanning /usr/share/applications/screensavers
Application Engine : Scanning /usr/share/applications/kde
Desktop Search Engine : Tracker

(affinity:7382): Gtk-CRITICAL **: gtk_icon_theme_load_icon: assertion `error == NULL || *error == NULL' failed

(affinity:7382): Gtk-CRITICAL **: gtk_icon_theme_load_icon: assertion `error == NULL || *error == NULL' failed

(affinity:7382): Gtk-CRITICAL **: gtk_icon_theme_load_icon: assertion `error == NULL || *error == NULL' failed

(affinity:7382): GLib-CRITICAL **: g_string_free: assertion `string != NULL' failed

(affinity:7382): GLib-CRITICAL **: g_string_free: assertion `string != NULL' failed

Alguna idea?

---

### Post by faktorqm on 2007-09-11
hola, no tengo ni idea del problema, pero la barra de abajo con forma de repisa, como la lograS? es un efecto del beryl, o un programa? o un screenlet? salu2!

---

### Post by marianom on 2007-09-11
> **faktorqm said:**
> hola, no tengo ni idea del problema, pero la barra de abajo con forma de repisa, como la lograS? es un efecto del beryl, o un programa? o un screenlet? salu2!

Eso es [AWN]("https://launchpad.net/awn"). Fijate en el foro, hay varios posts al respecto.

---

### Post by faktorqm on 2007-09-12
gracias marianom!! :D

---

### Post by santiagoward2000 on 2007-09-12
Hola Gente,
En realidad no es AWN, es Kiba-Dock.

---

### Post by marianom on 2007-09-12
> **santiagoward2000 said:**
> Hola Gente,
En realidad no es AWN, es Kiba-Dock.

Gracias por la corrección en ese caso.

---

### Post by santiagoward2000 on 2007-09-12
De nada Mariano. Igual, es medio complicado saber cuál es a simple vista.

---

### Post by santiagoward2000 on 2007-09-12
Creo que ya está solucionado el tema de la barrita :lolflag:
Ahora, ¿alguien sabe cuál es el problema con Affinity?

---

### Post by santiagoward2000 on 2007-09-18
Alguien? Alguna idea??

---

### Post by Patriciologico on 2007-09-19
Usas los iconos por defecto del sistema u otros instalados por tu parte?

---

### Post by santiagoward2000 on 2007-09-19
> **Patriciologico said:**
> Usas los iconos por defecto del sistema u otros instalados por tu parte?

No, uso los íconos Nuvola que venían con el paquete gnome-extra icons. ¿Puede estar ahí el problema?

---


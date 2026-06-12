---
title: "ajust backlight nouveau"
date: 2010-11-14
forum: Catalan Team
---

### Post by quitus on 2010-11-14
Hola

tinc un portàtil vaio amb una tarja nvidia GeForce 8400M GT i ubuntu 10.04 Des que va sortir el driver nouveau que no puc ajustar la lluentor del backlight de la pantalla.

Estic molt content amb aquest driver, ja que la tarja no deu estar en bon estat i amb els drivers propietaris al cap de l'estona deixava de funcionar correctament, en canvi amb el nouveau el 2D funciona de meravella.

En versions anteriors, amb el driver NV feia servir nvclock per ajustar-ho, però amb nouveau no se com fer-ho

gràcies

---

### Post by quitus on 2010-11-30
Bé, encara no se com ajustar la intensitat de la llum de la pantalla, però he trobat una aplicació que permet ajustar els colors de la pantalla i així no deixar-te els ulls.

"redshift" ajusta els colors automàticament agafant la franja horària del applet gnome-clock

per instal·lar-ho

sudo add-apt-repository ppa:jonls/redshift-ppa
sudo apt-get update && sudo apt-get install redshift

salut.

---

### Post by kimet on 2010-12-01
No se si ACPI funciona amb la teva marca de portatil o amb la bios que porta.

Investiga sobre ACPI i acpid.

Pots mirar si existeix el directori /proc/acpi, si es així, mira si existeix un fitxer lcd i si canviant els valors, canvia la lluentor de la patalla. P.ex.

# echo n > /proc/acpi/lcd 

O una cosa semblant, hauria de pujar o baixar la lluentor (canviant la "n" per un número del 1 al 7. 
Si això et funciona, només et falta fer dos petits scripts i assignar-els-hi una tecla de funció per pujar i una altre per baixar la lluentor.


Salut.

---

### Post by quitus on 2010-12-01
Gracies per respondre. Buscant a google acpi nouveau he trobat un arxiu backlight a /sys/class/backlight/nv_backlight/brightness, però no se com modificar el valor original (1025) per un altre.

salut

---

### Post by kimet on 2010-12-01
Mira aixó es mes o menys el vaig fer jo però en altres marques.
[http://tuxeando.wordpress.com/2007/08/05/cambiando-el-brillo-del-sony-vaio-en-ubuntu/](http://tuxeando.wordpress.com/2007/08/05/cambiando-el-brillo-del-sony-vaio-en-ubuntu/)

(els escripts es poden millorar):D

En resum es instal.lar els mòduls acpi i modificar els valors a /proc

---

### Post by PatrickVogeli on 2010-12-05
pots provar aixo:

sudo su
echo 500 > /sys/class/backlight/nv_backlight/brightness

et canvia la brillantor?

---

### Post by quitus on 2010-12-06
Ha funcionat a la perfecció, gracies, ara només queda afegir això als botons de funció, però ja es un altre tema.

salut

---


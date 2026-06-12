---
title: "Ubuntu desayuna GBs"
date: 2007-04-25
forum: Argentina Team
---

### Post by sebas.rhcp on 2007-04-25
Yo tenia Windows XP en esta particion y con 10gb siempre alcanzo pero con Ubuntu ahora me quedan 150MBs libres (borre unas *********), algun consejo?

---

### Post by lugonesjoaquin on 2007-04-25
Pero debes tener muchas macanas instaladas o muchos arhivos al ****.

Ubuntu instalado ocupa 1.8 GB, Windows XP 1.25. 
Peeeeeroooo, Windows te trae el office con esos 1.25 gb? Nop..

Trata de hacer esto aver si te ahorra algo:

sudo apt-get clean

---

### Post by gepatino on 2007-04-25
Despues de limpiar el cache del apt como te dijo lugonesjoaquin, proba de ejecutar el siguiente comando estando en /home:

sudo du -m --max-depth=1


Deberia tirarte una lista de cuanto esta ocupando cada usuario. A veces (muy ocasionalmente) si un X se va de viaje deja atrás un .xerror muy grande. Este archivo es un log de errores que se puede eliminar sin inconveniente.

Si no encontras nada demasiado grande en /home, hace lo mismo en /tmp

---

### Post by Al_maverick on 2007-04-25
es muy raro. Yo tengo una instalacion completa, que tiene casi un año ya, y un monton de aplicaciones, y sacando /home apenas si llega a los 4.5GB (KDevelop, KOffice completo, OO.o, KDE 3.5.6, GIMP, etc.)

---

### Post by marianom on 2007-04-25
Si usás thunderbird y tenés mucho tráfico de mails, es necesario periodicamente compactar las carpetas para que te libere espacio ya que nunca borra los mails, solo los oculta.

---

### Post by sebas.rhcp on 2007-04-26
Ahora usa 4.7GB igual borre/movi un par de cosas. La carpeta home ocupa 265MB y la tmp 8MB. Yo vengo de Edgy y seguramente quedaron cosas obsoletas, que puedo hacer?

---

### Post by Al_maverick on 2007-04-26
Esta thread tiene algunos consejos: [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by sebas.rhcp on 2007-04-26
Bueno ya mas parece que no puedo liberar, debe ser por los programas que instale :)

---


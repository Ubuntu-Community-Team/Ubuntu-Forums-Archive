---
title: "problema para instalar paquetes"
date: 2007-12-11
forum: Argentina Team
---

### Post by jotix on 2007-12-11
hoy estaba tratando de instalr unos paquetes necesarios para compilar unas cositas para mi teclado g15 y cuando trate de instalar el libusb-dev me salio este error en el synaptic:

W: Falló al obtener [http://ar.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.6.1-1ubuntu10_amd64.deb](http://ar.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.6.1-1ubuntu10_amd64.deb)
  404 Not Found

W: Falló al obtener [http://ar.archive.ubuntu.com/ubuntu/pool/main/libu/libusb/libusb-dev_0.1.12-7_amd64.deb](http://ar.archive.ubuntu.com/ubuntu/pool/main/libu/libusb/libusb-dev_0.1.12-7_amd64.deb)
  404 Not Found

quisiera saber a que se debe esto, son problemas en mi instalacion? o problemas con los servidores donde estan los archivos? y si es asi como lo puedo solucionar.

Desde ya muchas gracias

---

### Post by jotix on 2007-12-11
bueno estaban caidos los servidores para argentina, cambie desde synaptic a los servidores principales y problema resuelto

---

### Post by kowal on 2007-12-11
Parece que siguen caídos los servidores .ar..

---

### Post by Baroh on 2007-12-12
Tratando de instalar unrar me pasaba lo mismo.

```
Err http://ar.archive.ubuntu.com gutsy/multiverse unrar 1:3.7.3-1.1
  404 Not Found
E: Failed to fetch http://ar.archive.ubuntu.com/ubuntu/pool/multiverse/u/unrar-nonfree/unrar_3.7.3-1.1_i386.deb: 404 Not Found
```

Después fui a la segunda dirección con Firefox y podía ver la lista de paquetes, sin embargo cuando trataba de bajar alguno me aparecia el 404... pero el de ISS! :confused:

---

### Post by facundocorradini on 2007-12-12
> **Baroh said:**
> 

Después fui a la segunda dirección con Firefox y podía ver la lista de paquetes, sin embargo cuando trataba de bajar alguno me aparecia el 404... pero el de ISS! :confused:

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

WTF???!!!!!!!!!! ??!?!?!!!!!!!!!!

IIS??? servidores de Ubuntu corriendo IIS????!!!!!!!!!!!!...

---

### Post by Hei Ku on 2007-12-12
> **facundocorradini said:**
> !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

WTF???!!!!!!!!!! ??!?!?!!!!!!!!!!

IIS??? servidores de Ubuntu corriendo IIS????!!!!!!!!!!!!...

Ahora entiendo entonces por qué estan con problemas :lolflag:

---

### Post by Baroh on 2007-12-12
¡Netcraft [dice]("http://toolbar.netcraft.com/site_report?url=http://ar.archive.ubuntu.com") que usa Apache en Ubuntu! ¿Qué onda? :-s

- Edit -

Me fijé de nuevo y ahora anda el mirror de Argentina.

Algo que me llamó la atención es que ahora Netcraft reporta que el mirror de Argentina esta en UK. Hoy a la tarde cuando no andaba el mirror y los paquetes daban el 404 de IIS también había consultado Netcraft para ver si realmente corría en IIS. En ese momento, al igual que ahora, Netcraft reportaba Apache en Linux, pero los servers estaban en Argentina y si mal no recuerdo el Network Owner (que ahora figura como Canonical Ltd) era Prima S.A.

Saludos

---

### Post by beuno on 2007-12-12
Hace unas 36 horas pusieron en marcha un mirror local en Argentina, que parece que no funciono muy bien.
Cuando lo detectamos, avisamos a los sysadmins y volvieron a apuntar todo a .uk hasta que se resuelva el problema.

Cualquier otro inconveniente, por favor sigan posteando en este thread asi lo seguimos.

---

### Post by facundocorradini on 2007-12-12
Pero ... están jodiendo??? enserio los servidore de ubuntu van a correr con IIS???!!!

edit:

Ok, ahora chequeo y veo que al menos los servidores de UK están corriendo Apache...

---

### Post by beuno on 2007-12-12
> **facundocorradini said:**
> Pero ... están jodiendo??? enserio los servidore de ubuntu van a correr con IIS???!!!

No, no son "los servidores de Ubuntu".
Es un mirror que donaron, y no se sabe que problemas estan teniendo.

---


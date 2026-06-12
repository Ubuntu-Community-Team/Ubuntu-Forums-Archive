---
title: "¿ Cómo levanto un Server FTP ?"
date: 2007-03-22
forum: Argentina Team
---

### Post by jpmorelli on 2007-03-22
Traté de instalar y configurar el proftpd para levantar un server FTP en mi máquina pero ya de entrada me da errores de instalación, ni siquiera puedo lograr configurarlo, tambien lo intenté desde la GUI gproftpd uqe parece bastante amigable pero no lo es, por lo menos no para mi gusto.
¿ Alguién sabe como levantar el servicio o algun programa para acceder via FTP a mi máquina ? :confused:

---

### Post by gepatino on 2007-03-22
generalmente uso vsftpd, y es muy facil de configurar:

sudo apt-get install vsftpd

y ya esta funcionando


si queres que tus usuarios puedan acceder (en forma no anonima), y subir archivos tenes que editar el /etc/vsftpd.conf tenes que habilitar las siguientes opciones:

local_enable=YES
write_enable=YES

---

### Post by jpmorelli on 2007-03-22
Muchas gracias !!! Funcionó perfecto.

---


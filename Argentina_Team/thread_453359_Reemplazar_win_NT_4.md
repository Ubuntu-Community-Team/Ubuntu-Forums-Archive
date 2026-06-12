---
title: "Reemplazar win NT 4"
date: 2007-05-24
forum: Argentina Team
---

### Post by blackknightr89 on 2007-05-24
Hola, en la oficina donde trabajo tenemos un servidor con Windows NT 4 para autenticación de usuarios, entre otras cosas menos importantes. El punto es: como puedo reemplazar esa función usando Ubuntu 7.04 Desktop? La información que encontré, ya sea usando OpenLDAP o el mismo Samba no es completa o está desactualizada.
Saludos

---

### Post by kalel on 2007-05-24
fijate si esto te sirve 

[http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10](http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10)

es para ubuntu edgy 6.10 pero yo hice lo mismo en la 7.04

---

### Post by blackknightr89 on 2007-05-28
Siguiendo las instrucciones, llegué a la parte donde tengo que ingresar:
**sudo mount -o remount /**
y me tira el siguiente error:
**mount: / no estÃ¡ montado todavÃ*a o una opciÃ³n es incorrecta**
Saludos

---

### Post by kalel on 2007-05-28
en que parte dice eso pk la verdad, no lo veo.

---

### Post by blackknightr89 on 2007-05-28
[http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10_p3](http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10_p3)
El subtítulo es **Quota**
Saludos

---

### Post by blackknightr89 on 2007-05-30
Hola, si alguien sabe que puedo estar haciendo mal que lo postee por favor, necesito terminar ésto con cierta urgencia.
Saludos

---

### Post by elrengo79 on 2007-05-30
recien segui el tutorial hasta donde te fallo a vos y no me tiro ningun error.
seguramente te quedo algo mal cuando modificastes el fstab, revisa bien la linea que monta tu particion root
asi esta la mia
# /dev/hda2
UUID=3f428f4c-8f2f-4f28-b5ac-3e5589f506ed /               ext3    defaults,errors=remount-ro,usrquota,grpquota 0       1

---

### Post by blackknightr89 on 2007-06-01
Ingresé  mount /dev/hda3 -o remount / , no se si iba así, pero me lo tomó.
Cuando llego a quotacheck -avugm me tira
quotacheck: Cannot find filesystem to check or filesystem not mounted with quota option.
No se si tengo que mandarle algún parametro o algo.
Saludos

---


---
title: "Problema montando carpetas compartidas de Win XP"
date: 2007-04-05
forum: Argentina Team
---

### Post by matog on 2007-04-05
Hola gente. Como siempre, con dudas y problemas, je.

Edité mi fstab para que me monte, automaticamente al arrancar, las carpetas compartidas de una maquina que está en red y que corre WinXP.
Agregué:
```
//MARIANA/Escritorio /media/red smbfs username=Matias,password=pass,workgroup=workgroup,user,owner,noauto 0 0
```

En un principio, me aparecia el icono del rigido con "smb" sobre el mismo, porque solamente el root podía montarlas. Hice un gksudo nautilus (no la tengo clara con la consola) y le cambia los permisos a esas carpetas para que mi usuario en Ubuntu, "Mato", puede escribir, borrar, todo.

Perfecto. Ahora las monta, puedo abrir archivos, pero....no los puedo borrar.

Que demonios tengo que hacer para que mi usuario en ubuntu pueda hacer de todo en esas carpetas? Tiene que ser el mismo que el usuario en WinXP, o no? Me imagino que no...

Gracias!!!!

---

### Post by Nemesis Teufel on 2007-04-05
Eso es porque solo tenes acceso a lectura en los discos, para escritura necesitas darle soporte de NTFS y acá hay una explicación de como hacerlo:

[Soporte de NTFS]("http://ubuntuforums.org/showthread.php?t=312107&highlight=soporte+ntfs")

---

### Post by matog on 2007-04-05
No, son FAT32, si cuando entro por Lugares/Servidores de Red no tengo problemas en escribir....

---

### Post by kowal on 2007-04-06
Probá agregando a toda la línea esta:

```

//MARIANA/Escritorio /media/red smbfs username=Matias,password=pass,workgroup=workgroup,user,owner,noauto 0 0
```

Lo siguiente: **dmask=777,fmask=777**

O sea que quede algo así:

```

//MARIANA/Escritorio /media/red smbfs username=Matias,password=pass,dmask=777,fmask=777 0 0
```

Saludos.

---

### Post by matog on 2007-04-06
Me queda así:

```
//MARIANA/Escritorio /media/red smbfs username=Matias,password=pass,workgroup=workgroup,user,owner,noauto 0 0,dmask=777,fmask=777 0 0
```

Y no funciona....Adjunto como veo los esas carpetas (y no están montadas)

---

### Post by kowal on 2007-04-06
Está mal como estás poniendo.. (hay un 0 0 en el medio que no va) copiá y pegá como te dije en el ejemplo:

//MARIANA/Escritorio /media/red smbfs username=Matias,password=pass,dmask=777,fmask=777 0 0

PD: No te olvides de volver a montar, una vez que grabaste los cambios en fstab con el comando **sudo mount -a**

---

### Post by matog on 2007-04-06
Kowal, sos un capo! Peor sigo sin poder borrar archivos....

Puse lo anterior porque pensé que te lo habías comido...jeje.

---

### Post by kowal on 2007-04-09
No podés borrar? que raro, yo lo tengo exactamente así y puedo borrar/modificar sin problemas.. Probaste fijarte en las opciones de WinXP de compartir.. que esté tildada la opción "Permitir que usuarios de la red cambien mis archivos"? Estás seguro que es una partición FAT32?.

Saludos

---


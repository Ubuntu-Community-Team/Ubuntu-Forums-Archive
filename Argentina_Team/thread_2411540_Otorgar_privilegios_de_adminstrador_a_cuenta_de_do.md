---
title: "Otorgar privilegios de adminstrador a cuenta de dominio"
date: 2019-01-31
forum: Argentina Team
---

### Post by angork on 2019-01-31
Buen día a todos!
Estoy teniendo un problema al momento de querer otorgarle privilegios de administrador a usuarios con cuentas del dominio de la empresa donde trabajo. El equipo ya está unido al dominio y puedo loguearme con cuentas del AD de Windows Server pero figuran como "estandar".
Realicé la siguiente acción desde la cuenta "user" local que según tengo entendido le daría los permisos de admin a las cuentas pero no pasa nada.
 [COLOR=#000000][FONT=&quot]"Editar el archivo /etc/sudoers (nano /etc/sudoers) para ser administradores del equipo. Ingresar la siguiente línea:[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]- *userdomain* [/FONT][/COLOR][COLOR=#333333][FONT=Arial] [/FONT][/COLOR][COLOR=#000000][FONT=&quot]ALL=(ALL:ALL) ALL "


[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Eso lo hice en la linea "User privilege specification"

Alguna sugerencia? Gracias![/FONT][/COLOR]

---

### Post by aromo2 on 2019-01-31
Ya reiniciaste el servidor? Para que los cambios a /etc/sudoers tengan efecto sin reiniciar el servidor, tienes que haber usado visudo en vez de nano:
```
visudo -f /etc/sudoers
```
de lo contrario tienes que reiniciar el servidor para que sudo aplique los cambios hechos al archivo.

PS/ visudo es derivado de vim, asi que tienes que saber usarlo. De lo contrario no hay otra alternativa que usar otro editor y reiniciar el servidor.

---

### Post by angork on 2019-01-31
> **aromo2 said:**
> Ya reiniciaste el servidor? Para que los cambios a /etc/sudoers tengan efecto sin reiniciar el servidor, tienes que haber usado visudo en vez de nano:
```
visudo -f /etc/sudoers
```
de lo contrario tienes que reiniciar el servidor para que sudo aplique los cambios hechos al archivo.

PS/ visudo es derivado de vim, asi que tienes que saber usarlo. De lo contrario no hay otra alternativa que usar otro editor y reiniciar el servidor.

Si gracias, eso mismo hice pero no logro poner como adminsitrador a mi user de dominio.

---

### Post by aromo2 on 2019-02-01
Ya veo. El problema es que sudo no tiene manera de saber si un usuario es de dominio. Tendrias que crear y mantener un grupo (/etc/group) y dar permiso a ese grupo en sudoers:
```
%grupousuariosdedominio ALL=(ALL) ALL
```

---


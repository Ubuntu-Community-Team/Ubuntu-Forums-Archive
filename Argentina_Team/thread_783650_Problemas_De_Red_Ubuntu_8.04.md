---
title: "Problemas De Red Ubuntu 8.04"
date: 2008-05-05
forum: Argentina Team
---

### Post by gualge73 on 2008-05-05
Estimados integrantes del foro, soy nuevo en esto y necesitaria saber si uds, tuvieron el mismo problema. En el trabajo todos usan windows, pero yo por las malas experiencias con los programas de bill, me pase a ubuntu, Bueno al cambiar a la ùltima version de Ubuntu, me surge un problema de red, puedo ver algunas maquinas (via samba), pero en la maquina que es servidor no lee ninguna carpeta o archivo. Hable con el administrador de la Red y me dijo que es un problema mio, con la anterior versión de Ubuntu no tenia problema. la red esta configurada a traves de dominio y las cuentas las habilita el administrador. La mia esta creada y funciona. 
Tengo una AMDX2 4000, disco de 60 gb, memoria 512. 
Gracias por su tiempo!!!!!!!!!!!!!!!!!!!!!

---

### Post by faktorqm on 2008-05-06
Hola, necesitariamos que nos dejes mas datos de la red para saber cual es el problema, por ejemplo si el server usa LDAP para seguridad y esas cosas, el samba "solo" digamos, solo ve carpetas e impresoras, nada mas. Antes que smb.conf tenias? Supuestamente si solo tienen ACL's nt4-like no deberias tener problemas. Descartaste problemas en la red? es decir, tenes ping contra el server? si arrancas en win te podes meter? Salu2!

---

### Post by gualge73 on 2008-05-09
Hola, necesitariamos que nos dejes mas datos de la red para saber cual es el problema, por ejemplo si el server usa LDAP para seguridad y esas cosas, el samba "solo" digamos, solo ve carpetas e impresoras, nada mas. Antes que smb.conf tenias? Supuestamente si solo tienen ACL's nt4-like no deberias tener problemas. Descartaste problemas en la red? es decir, tenes ping contra el server? si arrancas en win te podes meter? Salu2!
__________________
<IN TUX WE TRUST>_|_ <LINUX BE MY GUIDE> 

Gracias por el post, la red, esta configurada bajo dominio, de las maquinas de red puedo ver casi todas pero la del server no, puede ser que tenga seguridad porque el administrador es medio freacky. Cuando voy al acceso directo a la carpeta creado en la ubuntu 7.10, me tira el cartel que no puede mostrar los archivos, si quiero entrar mediante red no me muestra ningun archivo. Desconozco la configuracìon anterior, puedo pingear y me devuelve todos los paquetes. Instale de nuevo todos los paquetes de samba y conexion de red y nada, gracias a Dios no tengo màs programas de Bill. HELP!!!!!!!!!!!!!!!!

---

### Post by faktorqm on 2008-05-11
O sea, para mi el problema esta en cuando te autenticas al dominio digamos, por eso te manda el cartelito de que no podes ver los archivos o de que tenes permisos insuficientes. A las otras compus te deja por que no tienen tanta seguridad. Y si le pedis al chabon que revise los permisos de tu usuario? una opcion puede ser que haya tocado algo sin querer y te haya sacado los permisos de lectura sobre esa carpeta.
No sé qué niveles de seguridad tendrás, pero hay muchas cosas por ver digamos. Tu ip es el mismo que antes? Si el samba anterior te lo veia, este tambien debe hacerlo. Samba es independiente de la version de ubuntu.
Y tambien, podes probar esto: mete el live cd de la version que vos decis que te andaba, instala el samba, e intenta ingresar, sino podes, entonces el problema esta en la configuracion del samba o de la red.
En sistema -> administracion -> red, en la ficha "general" tenes el nombre del dominio BIEN puesto?
Nos vemos! Salu2!

---

### Post by gualge73 on 2008-05-14
El Problema se soluciono, era un tema de los permisos de windows. Gracias por tu ayuda!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
NO se como poner que el tema se soluciono.

---


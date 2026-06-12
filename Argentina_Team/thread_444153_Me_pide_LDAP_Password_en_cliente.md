---
title: "Me pide LDAP Password en cliente"
date: 2007-05-15
forum: Argentina Team
---

### Post by electronpositivo on 2007-05-15
He configurado dos ordenadores con Ubuntu Feisty uno como servidor y otro como cliente y parece que todo va bien... o casi.

Al ejecutar la orden finger usuario desde el cliente, me devuelve los datos que he puesto en el servidor correctamente (si los cambio los datos del usuario en el servidor y ejecuto de nuevo la orden finger en el cliente tambien cambian). 

El problema está en que cuando intento autenticar contra el servidor utilizando algún usuario que he puesto, me pide usuario, password y LDAP Password. He probado a dejar el LDAP Password en blanco, a escribir el password que utilizo para el usuario admin, el password del usuario y nada...

Se trata de algún error mío? Alguien me puede ayudar (si hace falta pego lo que he puesto en los ficheros de configuración).

Muchas Gracias

---

### Post by electronpositivo on 2007-06-01
Si en consola tecleo lo siguiente:

$finger antonio

Me devuelve:

Login: antonio                           Name: Antonio
Directory: /www/antonio                  Shell: /bin/sh
Never logged in.
No mail.
No Plan.

Esto es correcto.

Ahora si intento loguearme con ese usuario:

$su antonio

Me pide la contraseña y la "contraseña LDAP"... esto segundo es lo que no me cuadra. En teoría no es necesario escribir ninguna contraseña de LDAP para loguearme. Es como si me pidiera la contraseña de root para poder acceder a una sesión normal, me explico?

Password: ***
LDAP Password: ***
su: Authentication failure
Disculpe.

Además, no sé qué LDAP password debo poner, he probado con la contraseña de administración de LDAP, la del usuario antonio, a dejarlo en blanco... y nada, Authentication failure.

Supongo que se trata de una tontería, pero no lo pillo. Ayuda por favor!!!

---


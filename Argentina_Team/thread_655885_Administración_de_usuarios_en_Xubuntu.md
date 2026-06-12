---
title: "Administración de usuarios en Xubuntu"
date: 2008-01-01
forum: Argentina Team
---

### Post by jclevien on 2008-01-01
Hola,

Estoy buscando un programa para Xubuntu Gutsy que me permita administrar usuarios.

Básicamente, lo que necesito es:

1. Crear grupos de usuarios y asignarles gente.
2. Cada grupo tiene ciertos atributos.
3. Limitar el uso de CPU (supongamos el grupo 'Ingenieros' usa hasta el 50% del CPU como máximo, el grupo 'Generales' hasta un 30%).
4. Limitar la RAM y la swap utilizada (para que no haga thrashing el sistema operativo, simplemente que no lance más aplicaciones luego de un punto y salga un cartel informando la limitación).
5. Que cada usuario tenga una cuota asignada máxima de utilización de espacio en disco duro (por ejemplo, el grupo 'Ingenieros' por defecto tiene 200 MB pero el usuario Pepe, que es Ingeniero y tiene una prerrogativa, le asignamos 100 MB más).
6. Limitar el ancho de banda utilizado para cada usuario. Supongamos, Juan tiene asignados 10 Kb/s para bajar y 2 Kb/s para subir, y por más que intente, el sistema no lo deje hacer lo que quiera.
7. Permisos del filesystem. Por defecto, nadie puede hacer un browse de todo el filesystem, y menos ejecutar un programa no asignado a su grupo o perfil. Solo usará un directorio asignado en forma predeterminada, con las características antes mencionadas (cuota, permisos restringidos, etc).

¿Existe este sistema? Yo vi que hay sistemas de Computer Associates que están diseñados para hacer este tipo de administración fina, pero necesito algo free, y si es basado en Ubuntu, mejor... :)

Muchas gracias por sus comentarios.
Un saludo en este Año que recién comienza.


Juan

---

### Post by jclevien on 2008-01-01
Me contesto yo mismo: parece que lo que busco es SELinux.
¿Alguien ha usado SELinux en Xubuntu Gutsy? ¿Que front-end me recomiendan para empezar a trabajar con el?

Gracias.


Juan

---

### Post by marianom on 2008-01-03
¿SELinux anda en distros basadas en debian? Siempre creí que solo lo usaba RedHat y Fedora (porque lo asumí vaya uno a saber).
De todos modos en Ubuntu existe el AppArmor como variante al SELinux (que no es muy simpatico que digamos). Busca algo de info al respecto y comentanos si cumple lo que necesitas.

---

### Post by jclevien on 2008-01-05
Que tal Mariano,

El AppArmor parece una buena variante al SELinux.
Por lo poco que pude ver, sería más sencillo de configurar que el SELinux.

Con respecto al manejo de recursos que necesito, lo que parece excelente es el Linux-VServer.

Creo que combinando los dos sistemas tengo lo que busco. ¿Vos por casualidad usaste el VServer?


Saludos.


Juan

---

### Post by marianom on 2008-01-05
Hola Juan, lamentablemente no tengo experiencia en VServer. 

Ahora que Linux ha dejado de ser un paradigma solo para servidores y de a poco se está trasladando como algo viable a nivel usuarios en empresas, es bueno que empecemos a echarle un ojo a este tipo de soft. 
Espero que puedas compartir tus hallazgos, yo por mi parte prometo a hacer otro tanto.

Si tenes dudas en la implementación de SELinux o AppArmor, tiralas nomás que ahí me defiendo como gato entre la leña.

---


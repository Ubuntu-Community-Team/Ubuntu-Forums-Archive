---
title: "Nuevo En Linux Problema Con Root"
date: 2007-09-27
forum: Argentina Team
---

### Post by akrasiel334455 on 2007-09-27
Hola y gracias por abrir mi post, he instalado varios distros linux en mi vaio y ubuntu me agrado mas, al probar las opciones de usuarios en administracion pretendi hacer que mi nombre de usuario y el usuario root tuvieran el mismo perfil y privilegios, puse el mismo password para ambos (estupido de mi:() y cambie mi grupo de usuario al grupo /root, ahora comienzo con mi antiguo nombre de usuario pero me ha quitado todos los privilegios de instalar, remover y configurar el sistema, y no se como hacer o desde donde ingresar para cambiar dichos errores, alguien podria ayudarme? estoy usando la version 7.04 fiesty fawn, y la pc tiene tambien win xp en particion.
GRACIAS:confused:

---

### Post by Hei Ku on 2007-09-28
de mas esta decir que fue al menos imprudente lo que hiciste, y desde el punto de vista de seguridad, es un NO rotundo. Para eso existen cosas como el sudo.

- probaste a volver tu usuario al grupo anterior?
si no podes con tu usuario, tendrias que hacerlo con root.

---

### Post by leo_rockway on 2007-09-28
si, eso que hiciste es comun en windoze (ser usuario y administrador todo el tiempo) pero eso esta muy mal. una vez que logres solucionar tu problema no vuelvas a intentar hacerte administrador constante (para algo estan los usuarios)

---

### Post by Hei Ku on 2007-09-28
la practica comun en linux es la escalacion temporal de privilegios, para tareas especificas, con sudo.
Sudo es un programa que te permite realizar temporalmente tareas de administrador, y es lo recomendado para el uso diario.

Pero primero resolvamos el problema, pudiste volver tu usuario al grupo original?

---

### Post by akrasiel334455 on 2007-09-28
no, por que escondio lo las opciones del menu de administracion aunque todas las deje activadas cuando hice mi tonteria, y no puedo acceder a dichas opciones de nuevo ni instalar programas que me premitan hacerlo

---

### Post by Hei Ku on 2007-09-28
hmmm, vas a tener que entrar con un liveCD y editar un archivo a mano.
La opcion mas facil seria que entraras como root y editaras el archivo, pero supongo que no lo habilitaste, y en este punto seguro no podes usar "sudo", asi que la opcion es entrar desde el LiveCD, montar el disco, y editar el archivo /etc/group, que es el que tiene la configuracion de usuarios y grupos

De paso, copia aca el contenido de ese archivo, asi podemos entender que ***** te mandaste. Y tranquilo que entre todos te vamos a ir ayudando. Ahi una thread con un problema similar aqui: [http://ubuntuforums.org/showthread.php?t=420110](http://ubuntuforums.org/showthread.php?t=420110)

---


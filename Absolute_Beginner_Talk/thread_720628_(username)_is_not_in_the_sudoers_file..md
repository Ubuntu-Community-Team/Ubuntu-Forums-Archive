---
title: "(username) is not in the sudoers file."
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by mmonnar on 2008-03-10
¡¡¡Necesito Ayuda!!!

Recien acabo de instalar la version 7.10 de ubuntu-server y me he encontrado con un problema que no logro resolver. he buscado material de soporte pero no he encontrado algo que me sirva.

Resulta que no puedo utilizar sudo para realizar tareas administrativas, cuando intento utlizarlo me aparece el mensaje siguiente : 

(username) is not in the sudoers file.

He intendo editar el /etc/sudoers con visudo para agregar mi usuario pero no me deja, cada vez que intento algo me aperece el mensaje de arriba.

Agradece cualquier sugerencia que me pueda dar.

Gracias mil.


Manuel Monnar

---

### Post by Cypher on 2008-03-10
English is the primary language on this forum, so I'm using my very limited High School spanish and knowledge of Linux to determine your problem and will answer, but if you re-post in English or other Spanish speakers can expand more on what I say..

The only user added to the /etc/sudoers file by default is the user you create during Ubuntu installation. It is this user that has SUDO (root) privileges. All other user accounts will have to be manually added by that first user to the /etc/sudoers list..

---

### Post by p_quarles on 2008-03-10
Thread closed, as this is an English language Forum. There are, however, five Spanish language sub-forums in the LoCo Team area here.

Your username is not supposed to be in the sudoers file by default. The easiest way to give a user sudo privileges is to add it to the admin group. You can do this by booting into single-user mode and running the following:
```
adduser *username* admin
```
Feel free to ask any followup questions in the appropriate area of the forum.

---

### Post by Rocket2DMn on 2008-03-10
Hola Manuel,
Lo siento para mi español pobre. 

Necesitas "reboot" la computadora y utilizar "Recovery Mode" kernel en "GRUB".  Aqui, usa
```
usermod -a -G admin <login_nombre>
```

Entonces "reboot" normalmente y ahora puedes usar "sudo".  No necesitas cambiar /etc/sudoers

---

### Post by bodhi.zazen on 2008-03-10
> **p_quarles said:**
> Thread closed, as this is an English language Forum. There are, however, five Spanish language sub-forums in the LoCo Team area here.

I briefly re-opened the thread to allow a response from the beginner team in Spanish.

Hope this information helps the OP

---


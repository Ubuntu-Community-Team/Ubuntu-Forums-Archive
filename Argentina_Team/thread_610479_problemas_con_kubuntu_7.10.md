---
title: "problemas con kubuntu 7.10"
date: 2007-11-12
forum: Argentina Team
---

### Post by Skavenger on 2007-11-12
hola, me habia bajado esta distro hace un par de semanas ya, pero recien ahora la instale... cuestion que instala todo perfecto, una vez que inicio el so me sale un aviso para actualizar los paquetes entonces acepto todo, pero casi terminando me da un error de que no puede instalar un par de paquetes porque no los encontro, entonces acepto y seguido a eso me sale otro aviso diciendo que hay una nueva distro disponible, la 7.10, pero es la que acabo de instalar :confused:

acepte todo y al momento de instalar los paquetes que bajo, se cuelga en 0% [paso un tiempo laaaaargo...], entonces reinicio la maquina y cuando selecciono kubuntu en grub, sale la pantalla de loading, carga lo mas bien, pero dps de eso se ve todo negro =/

ademas de esto, tenia el problema de la resolucion del monitor, no me dejaba seleccionar mas de 65hz, me rompia los ojos con el que tenia -.-

una ultima cosa, tengo entedido que ahora esta version viene con compiz fusion por default, pero busque por todos lados y no encontre nada de esto para configurar o activar [o es que solo viene con ubuntu y no con kubuntu?]

espero puedan ayudarme. gracias!

---

### Post by tzulberti on 2007-11-12
Lo de que se te quede tildado el programa del update me resulta muy raro... Para poder ver de nuevo el mensaje hace desde una consola: " sudo apt-get update" y despues "sudo apt-get dist-upgrade"

Una consulta: lo de la pantalla en negro es mientras se esta cargando el linux, o al momento de loguearte? Si es al momento de loguearte, te deberia dejar en una consola. Logueate ahi, y escribi "sudo dpkg-reconfgure xserver-xorg" (sin las comillas). Selecciona las opciones correctas, y para iniciar la parte grafica hace:
"sudo /etc/init.d/kdm restart" en caso de que uses KUbuntu o "sudo /etc/init.d/gdm restart" en caso de que uses Ubuntu.

En Ubuntu (Gnome) la opcion para activar los efectos de Compiz estan en: System -> Preferences -> Appearence -> Visual Efects (eligi uno distinto de None).

---

### Post by Skavenger on 2007-11-12
es al momento de loguear, pero no me sale ninguna consola ni nada =/

lo reinstale y segui teniendo problemas, asi que me harte y le meti ubuntu, me reconocio todo como la ultima vez que lo probe y se ve que mejoro bastante esta ultima version =)

---


---
title: "Hoja de referencia de ubuntu"
date: 2008-04-29
forum: Argentina Team
---

### Post by atatiducken on 2008-04-29
Navegando por internet me encuentro con **[esta]("http://falada.googlepages.com/ubunturef.pdf")** hoja de referencia de Ubuntu q puede ser muy util, tiene muchos comandos utiles q se suelen usar, asi nos amigamos con la terminal de a poco, espero les sirva
 un saludo

Fuente: Think Ubuntu

---

### Post by totoloco on 2008-04-29
Copado.

Bajado!

:KS

---

### Post by PatoDB on 2008-04-29
Gracias man!!!

Te digo que el resumen de apt y dpgk me vienen bastante bien!!!


Exitos!!!


=)

---

### Post by faktorqm on 2008-04-30
Actualización para HH y algunas correciones:

Privilegios:
-----------

a) sudo <comando> &#8211; ejecutar el comando <comando> como super-usuario (root)
b) sudo su &#8211; abrir consola como super-usuario (root)
c) sudo su <usuario> &#8211; abrir consola como el usuario <usuario>
d) sudo -k &#8211; olvidar contraseñas de sudo utilizadas recientemente
e) gksudo <comando> &#8211; ejecutar el comando <comando> como super-usuario (root) gráficamente para GNOME y para XFCE
f) kdesudo <comando> &#8211; ejecutar el comando <comando> como super-usuario (root) gráficamente para KDE
g) sudo visudo &#8211; editar el archivo /etc/sudoers
h) gksudo nautilus &#8211; Ejecutar el gestor de archivos como super-usuario (root) (para GNOME)
i) kdesudo konqueror &#8211; Ejecutar el gestor de archivos como super-usuario (root) (para KDE)

Configuracion de la pantalla:
----------------------------

a) sudo /etc/init.d/gdm restart &#8211; reiniciar el Gnome Display Manager, como consecuencia de esto también reinicia el servidor X (para GNOME)
b) sudo /etc/init.d/kdm restart &#8211; reiniciar el Kde Display Manager, como consecuencia de esto también reinicia el servidor X (para KDE)
c) sudo /etc/init.d/xdm restart &#8211; reiniciar el Xfce Display Manager, como consecuencia de esto también reinicia el servidor X (para XFCE)

d) SOLO PARA 7.10 Y ANTERIORES:

1) cat /etc/X11/xorg.conf &#8211; mostrar configuración del servidor X
2) sudo dpkg-reconfigure -phigh xserver-xorg &#8211; reconfiguración del servidor X (SOLO SECCIÓN DE VIDEO)

PARA 8.04:

1) sudo displayconfig-gtk - configuración de la placa de video y monitor (GNOME)

e) Ctrl + Alt + Bksp &#8211; Reiniciar el servidor X
f) Ctrl + Alt + FN &#8211; cambiar a consola número N (menos la 7)
g) Ctrl + Alt + F7 &#8211; cambiar a consola reservada para el servidor X

Servicios del sistema:
---------------------

a) sudo start <servicio> &#8211; iniciar el servicio <servicio>
b) sudo stop <servicio> &#8211; parar el servicio <servicio>
c) status <servicio> &#8211; comprobar si el servicio <servicio> se está ejecutando
d) sudo /etc/init.d/<servicio> start &#8211; iniciar el servicio sysv <servicio>
e) sudo /etc/init.d/<servicio> stop &#8211; parar el servicio sysv <servicio>
f) sudo /etc/init.d/<servicio> status &#8211; comprobar el servicio sysv <servicio>
g) sudo /etc/init.d/<servicio> restart &#8211; reiniciar el servicio sysv <servicio> (equivalente a hacer start y luego stop)
i) runlevel &#8211; obtener runlevel actual

Gestor de paquetes:
------------------

a) sudo apt-get update &#8211; Actualiza la lista de paquetes disponibles en los repositorios
b) sudo apt-get upgrade &#8211; Realiza la comprobación para determinar si existen actualizaciones de paquetes ya instalados en el sistema.
c) sudo apt-get dist-upgrade &#8211; Actualiza la distribución entera a una nueva versión.
d) sudo apt-get install <paquete> &#8211; Instalar el paquete <paquete>
e) sudo apt-get remove <paquete> &#8211; Desinstalar el paquete <paquete>
f) sudo apt-get install <paquete> --reinstall &#8211; Reinstalar el paquete <paquete> manteniendo la configuracion (equivalente a hacer remove y luego install)
g) sudo apt-get remove <paquete> --purge &#8211; Desinstalar el paquete <paquete> y además eliminar todas las configuraciones (no incluye las del /home)
h) sudo apt-get autoremove &#8211; Desinstala paquetes obsoletos que ya no se necesitan mas. No borra los instaladores.
i) sudo apt-get -f install &#8211; Intentar arreglar paquetes rotos o dependencias incompletas
j) sudo dpkg --configure -a &#8211; Intentar arreglar paquetes rotos o dependencias incompletas
k) sudo dpkg -i <paquete>.deb &#8211; Instalar el paquete <paquete>.deb
l) El archivo /etc/apt/sources.list posee la lista de repositorios APT, también disponible gráficamente en Orígenes del software.
m) sudo apt-get autoclean - Borrar del repositorio local los paquetes que ya no pueden ser descargados, o son claramente inservibles.
n) sudo apt-get clean - Borras todo el cache de APT ENTERO.

Redes:
-----

a) ifconfig &#8211; mostrar información de las interfaces de red del sistema
b) iwconfig &#8211; mostrar información de las interfaces de red wireless del sistema
c) sudo iwlist scan &#8211; escanear las redes inalámbricas
d) sudo /etc/init.d/networking restart &#8211; reiniciar el servicio de red
e) cat /etc/network/interfaces &#8211; ver la configuración de las interfaces de red
f) ifup <interfaz> &#8211; Habilitar la interfaz <interfaz>
g) ifdown <interfaz> &#8211; Deshabilitar la interfaz <interfaz>

Paquetes especiales:
-------------------

ubuntu-desktop &#8211; Entorno Ubuntu estándar de escritorio GNOME
kubuntu-desktop &#8211; Entorno Kubuntu estándar de escritorio KDE
xubuntu-desktop &#8211; Entorno Xubuntu estándar de escritorio Xubuntu
ubuntu-minimal &#8211; Utilidades base de Ubuntu
ubuntu-standard &#8211; Utilidades estándar de Ubuntu
ubuntu-restricted-extras &#8211; No libres, pero útiles (GNOME)
kubuntu-restricted-extras &#8211; No libres, pero útiles (KDE)
xubuntu-restricted-extras &#8211; No libres, pero útiles (XFCE)
build-essential &#8211; metapaquete utilizado para instalar una serie de paquetes cuya utilidad es compilar programas
linux-image-generic &#8211; última imagen genérica del kernel
linux-headers-generic &#8211; últimas cabeceras genérica del kernel

Cortafuegos (firewall):
----------------------

a) sudo ufw enable &#8211; Iniciar el cortafuegos
b) sudo ufw disable &#8211; Detener el cortafuegos
c) sudo ufw default allow &#8211; Permitir todas las conexiones por defecto
d) sudo ufw default deny &#8211; Denegar todas las conexiones por defecto
e) sudo ufw status &#8211; Muestra las reglas y el estado actual
f) sudo ufw allow <puerto> &#8211; Permitir tráfico entrante en el puerto número <puerto>
g) sudo ufw deny <puerto> &#8211; Denegar tráfico entrante en el puerto número <puerto>
h) sudo ufw deny from <IP> &#8211; Bloquear tráfico de la dirección ip <IP>

Nombre de algunas aplicaciones:
------------------------------

nautilus &#8211; gestor de archivos (GNOME)
dolphin &#8211; gestor de archivos (KDE)
thunar - gestor de archivos (XFCE)
konqueror &#8211; Navegador web (KDE)
kate &#8211; editor de texto (KDE)
gedit &#8211; editor de texto (GNOME)
mousepad - editor de texto (XFCE)

Sistema:
-------

a) lsb_release -a &#8211; Obtener la versión de Ubuntu
b) uname -r &#8211; obtener versión del kernel
c) uname -a &#8211; obtener toda la información del kernel
d) uname -m - obtener informacion de la máquina
e) lspci - Obtener una lista de dispositivos PCI conectados
f) lsusb - Obtenes una lista de dispositivos USB conectados
g) ps - Obtener lista de procesos ejecutándose (recomendado: ps -ax)
h) top - Mostrar de forma interactiva los procesos del sistema, el estado de utilización de la CPU, la memoria utilizada y libre, la RAM que utiliza cada proceso, etc.

Manejadores de ventanas:
-----------------------

a) metacity para GNOME (por defecto en la instalacion)
b) xfwm4 para XFCE (por defecto en la instalacion)
c) kwin para KDE (por defecto en la instalacion)

Apagado y reiniciado del sistema:
--------------------------------

a) sudo halt - Apagar el sistema (su equivalente: sudo shutdown -h now)
b) sudo reboot - Reiniciar el sistema (su equivalente: sudo shutdown -r now)


Administración de usuarios:
--------------------------

a) sudo adduser <usuario> - Agrega el usuario <usuario> al sistema
b) sudo passwd <usuario> - Establece la contraseña para el usuario <usuario>
c) sudo userdel <usuario> - Elimina el usuario <usuario> en el sistema
d) exit - Salir de la sesión de terminal de algún usuario.

Bueno listo, ya arreglé todo. Espero que les haya gustado, Salu2!!!!!!!!

EDITO: Sigo corrigiendo cosas. Tengo pensado en la medida de lo posible poner ejemplos. Arregle en la parte de instalacion de paquetes la diferencia entre autoremove, clean y autoclean.
Agregué como reinstalar paquetes y como borrar con sus configuraciones.
Agregué más comandos, la fuente fue [http://www.microteknologias.cl/linux_consola2.html](http://www.microteknologias.cl/linux_consola2.html)

---

### Post by MeduZa on 2008-04-30
> **faktorqm said:**
> Se puede reiniciar el sistema presionando las teclas, alt + pet sis + B. 

eso no lo sabia y no lo puedo probar (no quiero reiniciar mi pc) pero difiere del otro y no entiendo como deberia hacerlo

alt + sys rq + b pero en el otro dicen otra cosa alt + sys rq + muchas letras por 1 segundo, no entendi o.O

---

### Post by faktorqm on 2008-04-30
[http://doc.ubuntu-es.org/Pet_Sis](http://doc.ubuntu-es.org/Pet_Sis)
[http://www.kalcobrena.com/?p=39](http://www.kalcobrena.com/?p=39)

En realidad no se que quizo hacer el chabon ahi, eso esta de mas, mejor lo saco. Salu2!

---

### Post by atatiducken on 2008-04-30
buenisima aclaracion faktorqm, muchas gracias

---

### Post by sergiom99 on 2008-04-30
gracias che.

---

### Post by euzkoarima on 2008-04-30
> **faktorqm said:**
> 
Bueno listo, ya arreglé todo. Espero que les haya gustado, hace una hora que estoy escribiendo esto :@ y encima perdió el pincha..... Aca les vamos a ganar... GGRRR 
Salu2!!!!!!!!

Buenísimo tu aporte, gracias.

---

### Post by atatiducken on 2008-05-01
se me ocurrio, que seria util y bastante practico y comodo que esta lista q se esta armando, con los comandos mas utiles, si es posible, se ponga en la seccion de sticky.
Que los mods y los q mas entienden la armen y actualizen bien(tomando como base la de faktorqm, si es q le falta algo, porq es un lujo :)) y alli en ese sticky podriamos ir pidiendo comandos para q los agreguen, asi si necesitamos algo buscamos ahi sino hacemos una peticion para q lo agreguen o algo, obviamente falta depurar esta idea pero me parece practica,
Podriamos armar una version en PDF u ODT para bajarla e imprimirla ademas de la "online"
gracias por tomarse el tiempo de leer, un abrazo

---

### Post by aregnando on 2008-05-01
> **atatiducken said:**
> Navegando por internet me encuentro con **[esta]("http://falada.googlepages.com/ubunturef.pdf")** hoja de referencia de Ubuntu q puede ser muy util, tiene muchos comandos utiles q se suelen usar, asi nos amigamos con la terminal de a poco, espero les sirva
 un saludo

Fuente: Think Ubuntu

Muchas gracias atatiducken, muy útil sobre todo para los que somos bastante nuevos en Ubuntu.

---

### Post by faktorqm on 2008-05-01
Bueno, faltan igual un par de cosas por pulir..... 

por ejemplo, en gnome el sudo grafico es gksudo, en kde es kdesudo, y en xfce cual es? 

otra: konqueror es violentamente bueno, tanto asi que sirve como visor de archivos, explorador de internet, y explorador de archivos, y supongo que muchas mas cosas que desconozco. a donde lo pongo? por que aparece duplicado :S

otra mas: en gnome es gdm, en kde es kdm, en xfce, cual es?

Espero que los users de xubu me digan asi lo agrego :D Salu2!

---

### Post by Hei Ku on 2008-05-01
> **faktorqm said:**
> Bueno, faltan igual un par de cosas por pulir..... 

otra: konqueror es violentamente bueno, tanto asi que sirve como visor de archivos, explorador de internet, y explorador de archivos, y supongo que muchas mas cosas que desconozco. a donde lo pongo? por que aparece duplicado :S

otra mas: en gnome es gdm, en kde es kdm, en xfce, cual es?


al konqueror ponelo en la categoria cortaplumas suizo, porque hace todo. Basicamente, es un visor de KIO Parts, que son APIs que permiten exponer la funcionalidad de una aplicacion en KDE. Asi que cualquier aplicacion que se exponga como KIO Part se puede acceder con Konqueror. Eso incluye archivos, samba, ssh, ftp, visor de archivos, visor de info del sistema, impresoras, musica, streams, etc.

en xfce, es xdm. el windows manager para hacer replace si se quiere sacar compiz es xfwm4.

como xfce usa el toolkit gtk, probablemente el gksudo funcione bien.

---

### Post by faktorqm on 2008-05-12
bump, mas agregados :D

---


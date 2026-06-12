---
title: "Problema con Aceleración 3D"
date: 2008-03-12
forum: Argentina Team
---

### Post by jimyelrojo on 2008-03-12
Hola a todos, soy nuevo en ubuntu y apreciaría mucho la ayuda!!!, mi problema es el siguiente:tengo una tarjeta de video integrada Mesa DRI UniChrome (K8M800) 20060710 x86/MMX+/3DNow!+/SSE2, instale el cedega 6.0 y al correr el system test del mismo, falla la aceleración 3D,alguien podria ayudarme con eso?:(

---

### Post by Mafber on 2008-03-12
Hola, lamento no poder ayudarte con cedega porque no lo tengo. Pero te hago una pregunta ¿tenes activada la aceleradora? si la respuesta es no o no tenés idea, fijate en:
[http://ubuntuforums.org/showthread.php?t=674030](http://ubuntuforums.org/showthread.php?t=674030)
Espero que te sirva
Suerte!!!

---

### Post by faktorqm on 2008-03-12
necesitas instalar el driver de video. El tema es que no esta, pero hace poco salio a la luz. Yo lo probe con otro modelo mas nuevo y todavia no anda, pero con el tuyo estan todos chochos. 

[http://ubuntuforums.org/showthread.php?t=485646](http://ubuntuforums.org/showthread.php?t=485646)

de todas maneras, si queres aceleracion 3d tambien podes probar el comando "glxgears" y te muestra tu fps. Salu2!

---

### Post by jimyelrojo on 2008-03-12
Mafber, escribi en una terminal:
glxinfo
Según me sugerian y lo que aparecío entre otras cosas fue:
direct rendering: Yes
Así que supongo que si tengo instalada la aceleradora, tal vez solo sea que no paso el test de cedega pero eso no quiere decir que no esté la aceleración 3d, igual esto solo lo supongo, igual voy a ver si encuentro algo en el link q pasaste, gracias por la ayuda.

---

### Post by guisheca on 2008-03-13
A mi también me da los mismo en el cedega, pero probaste instalar un juego de todas formas a ver que pasa?
Otra cosa, que juego estás intentando instalar? hay muchísimos juegos que se pueden instalar de manera extremadamente sencilla mediante un programa que se llama "playonlinux". Si te interesa ponelo en google que te sale un montón de información.
Un saludo.

---

### Post by jimyelrojo on 2008-03-15
> **guisheca said:**
> A mi también me da los mismo en el cedega, pero probaste instalar un juego de todas formas a ver que pasa?
Otra cosa, que juego estás intentando instalar? hay muchísimos juegos que se pueden instalar de manera extremadamente sencilla mediante un programa que se llama "playonlinux". Si te interesa ponelo en google que te sale un montón de información.
Un saludo.

Hola, si el juego que instale es el Age of Empire II, lo corro en el cedega 6.0 pero como en camara lenta, por eso pense que podría ser mi tarjeta de video ya que no pasa el test cedega, instalé el wine para probar pero ni siquiera puedo abrirlo xq se cuelga toda la maquina.
PD: bajé el playonlinux, pero no tengo idea de como instalarlo. Es que soy novato:(,si alguien puede ayudarme se lo agradezco

---

### Post by guisheca on 2008-03-15
Mmm son los drivers de la placa che. La verdad que no tengo idea como viene la mano con esa placa. Entré al enlace que te dan mas arriba y algo dice, pero está en ingles, y si bien algo entiendo me da fiaca traducirlo. Me parece que por ahí viene la mano.
Hasta que no arregles ese tema no van a haber jueguis en 3D che.
Por las dudas te pregunto: Tenés compiz-fusión activado?

---

### Post by Mafber on 2008-03-17
hola, 
fijate en la pag que te pasó faktorqm que hay para bajar un scrip (openchrome-stable.sh). Según entiendo, simplemente descargalo y luego dale doble-click para que te descargue e instale los driver para la placa de video.
Hace esto primero y después seguimos avanzando :)

---

### Post by jimyelrojo on 2008-03-18
> **guisheca said:**
> Mmm son los drivers de la placa che. La verdad que no tengo idea como viene la mano con esa placa. Entré al enlace que te dan mas arriba y algo dice, pero está en ingles, y si bien algo entiendo me da fiaca traducirlo. Me parece que por ahí viene la mano.
Hasta que no arregles ese tema no van a haber jueguis en 3D che.
Por las dudas te pregunto: Tenés compiz-fusión activado?

Puse en el synaptic: compiz-fusion y me figura como que está instalado, ahora no tengo idea de como usarlo. Pero si es uno de los efectos visuales dentro de las preferencias de apariencias, al seleccionarlo me salta: Desktop effects could not be enabled

---

### Post by jimyelrojo on 2008-03-18
Hola, descargué el scrip,pero con doble click no pasa nada, busqué y vi que se hace así:
te ubcicás en la carpeta donde descargaste es scrip y ahi: 
./openchrome-stable.sh 
Espero que sirva de algo, yo de  igual forma sigo sin solucionar mi problema, saludos

---

### Post by jimyelrojo on 2008-03-18
Hola, hice lo que dice la pagina que recomendó faktorqm, así:
./openchrome-stable.sh 
Install the necessary tools [Y/n]?y 
apartir de ahi te dice un par de veces:
Necesito descargar xxxkB de archivos. 
Se utilizarán XXMB de espacio de disco adicional después de desempaquetar. 
¿Desea continuar [S/n]? s
Luego:
create new symbolic link 
Prepare the installation files [Y/n]? y
Install the via openchrome 2D driver [Y/n]? y
Remove the installation files [Y/n]? y
Remove the installed development packages [Y/n]? y
Necesito descargar xxB de archivos. 
Se liberarán xxMB después de desempaquetar. 
¿Desea continuar [S/n]?s
ldconfig deferred processing now taking place 
Set up the xorg.conf file for the openchrome driver [Y/n]? y
Do you want to gathering device information, to post on the forum [Y/n]?y
Necesito descargar xxxkB de archivos. 
Se utilizarán XXMB de espacio de disco adicional después de desempaquetar. 
¿Desea continuar [S/n]? s
ldconfig deferred processing now taking place 
devince information has been stored at the following location: 
file: /root/hwinfo-2008-03-18-19:32.txt 
root@omar-desktop:/media/sda3/Omar/Descarga# 
Para proba, como recomiendan en [http://ubuntuforums.org/showthread.php?t=485646](http://ubuntuforums.org/showthread.php?t=485646) :
root@omar-desktop:/home/omar# grep openchrome /var/log/Xorg.0.log
(II) LoadModule: "openchrome"
(II) Loading /usr/lib/xorg/modules/drivers//openchrome_drv.so
(II) Module openchrome: vendor="http://openchrome.org/"
(!!) For support, please refer to [http://openchrome.org/](http://openchrome.org/).
root@omar-desktop:/home/omar# glxinfo | grep render
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
root@omar-desktop:/home/omar#
Antes me daba me daba "yes",además se me ocurrio correr el test de cedega y ahora no solo no pasa la aceleración 3D sino que tampoco pasa el Renderizado directo de OpenGL que antes si pasaba!!!!,creo que ahora tengo dos problemas en vez de uno,jajaja.Saben ¿qué hice mal?, agradezco la ayuda.

---

### Post by faktorqm on 2008-03-18
hola, bueno ni el script ese si el otro archivo te anduvieron? 
ahora bien, como tenes configurado el xorg.conf, por que mira que el configurador ese es medio medio, no se como te lo deja seteado. Fijate en ese thread que hay varios xorg.conf de ejemplo.
Si te parecio que por alguna cosa te mandaste alguna macana, revisa de arrancar en el grub con la version anterior del kernel, asi te arranca el sistema con el kernel "viejo" (el 2-6-15 si mal no recuerdo) y proba ahi el script. (yo tuve que hacer eso por que tenia la 2-6-16 y el script dice que solo es para la 2-6-15).
Si no sabes cual es tu version de kernel, pone "uname -r" en una consola.

Otra cosa, por que trabajas con root? no deberias hacerlo a menos que realmente sea necesario, y yo no veo que sea asi. no te olvides que root es super usuario y que si por alguna casualidad algo malo llega a pasarte podes kedar sin SO en una patada. en cambio, tu usuario con root tiene un monton de permisos menos que el root. De todas maneras no viene al caso, yo cuando los probe los instale utilizando sudo.

Salu2!!!

---


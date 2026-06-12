---
title: "¿Cómo usar IE en Ubuntu?"
date: 2007-10-08
forum: Argentina Team
---

### Post by nunox on 2007-10-08
Hola hermanos, primero que nada disculpen mi ignorancia soy nuevo en este de ubuntu y me he fijado en el foro y la única explicación que han hecho a mi pregunta (como usar ie en ubuntu) no la pude entender o mejor dicho no supe como aplicarla... pasa que mi conocimiento de consola es mínimo:oops:.
Me conacte con ustedes a partir de la CaFeConf y me recomendaron este foro también me quisieron explicar en el "aire" como hacerlo pero no dió resultado :oops:
Nuevamente perdón por la ignoracia  y si es posible guienme un poquito.
Desde ya mil gracias!
Un abrazo
Nuno
bytes!
P/D:necesito el IE por el tema de enviar sms a personal y me pide los acitveX :oops:

---

### Post by marianom on 2007-10-08
Seguro que te han recomendado IE4Linux.

[Aca]("http://www.tatanka.com.br/ies4linux/page/Es/Instalaci%C3%B3n") están las instrucciones de instalación.

Esto es lo que podemos hacer: seguilas al pie de la letra y ante la menor duda o error, posteás un mensaje informando que estás haciendo, que parte no sale o que error tenés. De esa forma te guiamos para que logres tenerlo.

---

### Post by nunox on 2007-10-08
Gracias Marianom, te comento... va a sonar patético pero bueno jaja desde la primer linea que me pasaste (que deducí que baja un archivo) no funciona porque me dice "archivo no encontrado":404 not found...
Te sigo contando... yo me baje de una web ese mismo archivo que me hiciste bajar y lo tengo en el escritorio descomprimido (por si ayuda de algo) y quise seguir probando las otras lineas de comando pero nada xD.
Así que si me podrías tirar un plan "B" lograrías "iniciar" a un noob jaja
Desde ya gracias otra vez!
Nuno

---

### Post by sajnox on 2007-10-08
nunox, 

En primer lugar bienvenido!!! te aporto otro link que vi hoy de  el IE en Ubuntu

[http://www.cesarius.net/instala-internet-explorer-en-gnulinux-un-mal-necesario-para-los-disenadores/]("http://www.cesarius.net/instala-internet-explorer-en-gnulinux-un-mal-necesario-para-los-disenadores/")

Espero que sirva.

Saludos

---

### Post by nunox on 2007-10-08
Hoal Sajnox desde ya muchas gracias por la bienvenida...
Dos cositas:
primero perdón a marianom porque no habia visto un link dentro del que me envío donde explicaba específicamente para ubuntu los siguiente:
Ubuntu Edgy 6.10

Primero tienes que habilitar los paquetes universe. También se recomienda que utilices el paquete winehq oficial de Ubuntu:

1) Abre una terminal

2) Abre /etc/apt/sources.list

 sudo gedit /etc/apt/sources.list

3) Descomenta las siguientes líneas:

  deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe
  deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe

4) Agrega esta línea:

 deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

5) Cierra gedit. Actualiza e instala wine y cabextract:

 sudo apt-get update
 sudo apt-get install wine cabextract

6) Descarga e instala IEs4Linux

 wget [http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz)
 tar zxvf ies4linux-latest.tar.gz
 cd ies4linux-*
 ./ies4linux


cosa que me perdí cuando me ordena "descomentar y agregar"

y la segunda:
Sajonx... empece a probar tu guía pero cuando actualizaba me decia: /var/lib/dpkg/ etsa siendo usado? y no sabia como responder xD.
y cerré la ventana :$ y despues cuando quise probar instalar directamente me decía lo siguiente:
root@santiago-desktop:/home/santiago# apt-get install wine cabextract
E: No se pudo bloquear /var/lib/dpkg/lock - open (11 Recurso temporalmente no disponible)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@santiago-desktop:/home/santiago# sudo apt-get install wine cabextract
E: No se pudo bloquear /var/lib/dpkg/lock - open (11 Recurso temporalmente no disponible)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


¿Qué estoy haciendo mal? :S

---

### Post by rojojuan on 2007-10-08
Hola Nunox:
Uso Ubuntu para enviar sms desde Personal, sin problemas. Entra en la página de Personal y luego en Accesos Directos, tenés mensajes de texto, cliqueá y listo. Ubuntu se la banca.

---

### Post by nunox on 2007-10-08
Rojojuan! si vos decis voy a seguir probando a ver que sucede jaja UBUNTU SE LA BANCA y mejor si no pongo la mrd del IE :D
Un abrazo y gracias a todos...
Cualquier cosa volveran a saber de mi xD
bytes!
Nuno!

---

### Post by JoACoV on 2007-10-09
ojo ahora no esta funcionando muy bien el servicio de personal y la pagina no deja mandar sms

---

### Post by rojojuan on 2007-10-09
Tenés razón, ahora lo acabo de comprobar.

---

### Post by JoACoV on 2007-10-11
de todas formas cuando lo solucionen (o sea los de personal) vas a poder mandar mensajes desde el firefox tranquilamente, por lo menos yo en windows usaba firefox y podia....:)

---

### Post by spg76 on 2007-10-12
Yo uso Opera (en Ubuntu y en Windows) y la página de Personal funciona bien.
Lo comento para que tengan otra alternativa.

---


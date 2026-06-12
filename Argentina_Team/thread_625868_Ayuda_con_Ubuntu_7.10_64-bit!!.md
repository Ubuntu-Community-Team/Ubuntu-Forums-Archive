---
title: "Ayuda con Ubuntu 7.10 64-bit!!"
date: 2007-11-28
forum: Argentina Team
---

### Post by berni21 on 2007-11-28
Hola bueno me presento Soy Bernardo, de argentina tengo 21 años.. y prbando el ubuntu 7.10 64-bit,ytengo varios problemitas, la primera ves que puse el cd para instalarlo, me carga la pantallad e boot elejia ejecutar o instalar ( algo asi no recuerdo bien ) y depues se me apagaba el monitor y  la maquiina seguia trabajando la lectora leia, me parecio raro y lo ke hize saque la placa de video ke tengo y active la del mather la onboard, bueno lo pude instlar tod joya, depues pongo  la placa mia la geforce8500 gt 512mg y cuadno carga el sistema operativo se pone la pantalla en negro y se apaga el monitro onda que no le manda señal, bueno pasan 5 segundos y vuelve y me pide el usuario y entro a ubuntu pero en una resolucion tan grande ke no podes hacer nada, bueno intente bajar los drivers de la pagina oficial, los baje y cuando los abro me tira un error, bueno eso e slo de menos, el otro tema es que no puedo  instlar mi modem Huawei SmartAX MT810 usb " Arnet, telecom"
no se como instalarlo si me dan una ayudita, baje unos driver que encontre recorriedno el foro, lo instala tod jya , modifico el dsl-provider pongo el user, y cuadno quiero modificar un tal topsecret o algo asi donde va la pass no me deja ni siquiera entrar, que tengo que hjacer , y depeus para conectarme como hago, bueno desde ya muchisimas gracias quiero ver ke onda ubnuntu y me esta gustando pero tengo esto por resolver ayudenme pls !!
saludos un abrazo

---

### Post by margori on 2007-11-28
Ubuntu 7.10 32 o 64 bits, arrancan con la maxima resolucion que soporta tu placa de video.

Apreta Ctrl + Alt + '+' para cambiar entre resoluciones.

Los controladores los vas a poder instalar una vez que tengas instalado Ubuntu en el disco duro.

Por favor, instanta no escribir tal cual como pensas, hacelo un poco mas tranquilo y especifico.

Por ejemplo "los baje y cuando los abro me tira un error...". Que error?

Por otro lado, bienvenido!

---

### Post by alfredo_cba on 2007-11-28
yo desisti de la version de 64bit por algo similar, la instalación se realiza correctamente, al inciciar aparece el mensaje "starting up" y luego un mensaje abajo que no recuerdo bién, algo como "Kernel 1000@100000", después de eso sigue andando el cpu y se apaga el monitor.
Por ahora seguiré con la versión de 32 que me anda barbaro.
suerte.

---

### Post by tzulberti on 2007-11-29
Cuando entres a la consola, logueate con tu user, y escribi: "sudo dpkg-reconfigure xserver-xorg". Eso te va a dejar elegir todos los datos para configurar el entorno grafio. Luego escribi: "sudo /etc/init.d/gdm restart" y deberia de iniciarte la parte grafica (pone kdm en vez de gdm si usas Kubuntu).

---


---
title: "id baja con puertos abiertos y sin ningun firewall"
date: 2007-08-20
forum: Argentina Team
---

### Post by piruleitor on 2007-08-20
Hola, tengo instalado ubuntu 7.04 y conectado a un router por puerto de red de hasta 20 Mb de vel. con windows consigo una ID alta y en ubuntu todas las pruebas que hago a diferentes puertos me dan que estoy detrás de un cortafuegos o de un router. En el router abrí todas los puertos y no tengo ningun cortafuegos y continua igual.
Alguien tiene el mismo problema o alguna idea de que tendria que hacer para conseguir ID alta?
Gracias.

---

### Post by leo_rockway on 2007-08-20
hasta donde tengo entendido iptables viene activado por default.
fijate de instalar el firestarter y detener el firewall.

(no estoy seguro de q lo q estoy diciendo sea realmente asi... pero con probar no perdes nada. si no funciona simplemente desinstala el firestarter y listo)

---

### Post by faktorqm on 2007-08-20
a mi me paso, y lo solucione de la siguiente manera:

me baje el nodes.dat de algun sitio de esos y lo puse en la carpeta /home/<tu_usuario>/.amule.
Despues en el router, abrí el puerto que quieras tcp, otro tcp + 3, y el udp.

ejemplo: 7000, 7003 y 7010.

Esperas a que el router tome los cambios, abris el amule, y vas a ver que solo se pone todo en verde. Al menos a mi me funciono asi. salu2!!!

---

### Post by rretamar on 2007-08-20
Una forma de comprobar si tenés los puertos abiertos EN EL ROUTER, es usar un chequeador de ports remoto. De esa forma descartas que no exista un problema en el router. No uso Ubuntu (tengo Kubuntu), pero no creo que instale un firewall por defecto.

Como scanner remoto de puertos, suelo usar el de Steve Gibson:

[http://www.grc.com](http://www.grc.com) (sección "Shields Up")

Es bastante práctico y configurable.

Saludetes !

---

### Post by piruleitor on 2007-08-21
Gracias por contestar a mi consulta, los iptables los desinstale e igual me da ID baja (con o sin firestarter) ademas el problema no es solo con aMule sino que con aMsn, Frostwire, etc. Los puertos los chequeo desde [http://www.amule.org/testport.php](http://www.amule.org/testport.php) y cualquiera que se me ocurra da error y detras de cortafuego. Seguire investigando y a la escucha...

---

### Post by faktorqm on 2007-08-21
che, no tendras la compu configurada con dhcp no?!?!?!
revisa eso. salu2!

---

### Post by Hei Ku on 2007-08-21
tenes configurado el port forwarding en el router? tenes que tener tu pc con ip fija y en el router configurar que forwardee esos puertos a la ip de tu pc.

---

### Post by piruleitor on 2007-08-23
Les he hecho caso y quite el dhcp en la configuracion, coloque la ip fija (entiendo que eso estaria mal configurado) pero sigue igual. Gracias por los concejos, seguire en la busqueda.

---

### Post by faktorqm on 2007-08-23
Si, pero si pones ip fija y no haces un port forwarding es lo mismo que nada. No hay algo que diga "NAT" en la configuración de tu router/modem? ahi tenes que poner los puertos que queres a tu pc. salu2!

---

### Post by piruleitor on 2007-08-27
si faktorqm , era asi nomas. Estaba direccionando mal, no interpretaba bien las ip a completar en el control manual de la red. Tengo id alta en todos los puertos.
GRACIAS.

---

### Post by facundocorradini on 2007-08-27
disculpen la ignorancia, pero qué es "una id alta" y para qué sirve?

---

### Post by faktorqm on 2007-08-27
Hola, bueno basicamente id baja en el emule es cuando tenes cerrado el puerto tcp. como no tenes escuchando nada o no se puede conectar, te da id baja, que vendria a ser como una marca de que no podes subir a maxima velocidad. entonces los servidores te bajan lento. pero lento mal, o sea, tener un emule con id baja es como tener conexion de dial/up
para tener id alta tenes que abrir el puerto tcp y udp en el firewall, y uno mas que es el tcp+3. y si aparte del firewall de windows tenes otro, abrilos ahi tambien. para mas informacion, anda a los foros del emule, que ahi esta todo mega explicado. (demasiado para mi gusto) salu2!!!

---


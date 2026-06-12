---
title: "nVidia y booteo lento"
date: 2007-11-19
forum: Argentina Team
---

### Post by Fikcio on 2007-11-19
Hola, gente. Ahora tengo el siguiente problema: instalé [ los controladores de mi placa de video]("http://www.nvidia.com/object/linux_display_ia32_100.14.19.html") y ahora una de las etapas del booteo (no sé cuál [sé que debería fijarme, pero ahora mismo no puedo]) se toma *cerca de cinco minutos* en que (para colmo) parece no haber actividad alguna (parece un cuelgue irremediable).

¿Alguna idea? Es poca información, pero podría ser un contratiempo común.

Sí necesitan más datos, chiflen. Muchas gracias.

---

### Post by Hei Ku on 2007-11-19
Fijate en /var/logs
El log de messages y el de xorg te pueden dar una pista de lo que esta tardando, o dando error.

---

### Post by Fikcio on 2007-11-27
Buenas, gente. Les cuento: yo creí que tenía que ver con los drivers de nVidia, pero parece que no; se cuelga durante unos minutos (aunque no siempre) en "* configuring networking interfaces". ¿Alguna idea? Gracias.

---

### Post by kowal on 2007-11-27
Evidentemente es un tema con la red. Qué tipo de conexión/es tenés? Funciona correctamente una vez que inicia la red?

---

### Post by BiTFx on 2007-11-27
Tal vez podria ser tu problema:

Después de instalar los driver nVidia en mi pc, y de habilitrar compiz fusion, también se demoraba bastante en arrancar.

El problema era que tenia una resolucion de 1280 x 960 (esa se puso luego de instalar los drivers nvidia), la cambié por 1024 x 768 y todo anduvo muy bien.

---

### Post by faktorqm on 2007-11-28
fijate por que capaz tenes dhcp y no te lo esta tomando y tarda en asignar la ip. salu2!

---

### Post by Fikcio on 2007-11-28
Amplío: hubo problemas con mi ISP y quedé sin Internet... y también sin Ubuntu, puesto que se colgaría en el paso ya mencionado indefinidamente. Ya me restituyeron el servicio y, si bien todavía no probé, estoy seguro de que ahora no voy a tener drama para entrar.

Tengo un modem ADSL conectado a la placa de red.
> 
fijate por que capaz tenes dhcp y no te lo esta tomando y tarda en asignar la ip. salu2!

Sí, seguramente es algo así. ¿Qué hago, entonces?

Espero que les sirva. Gracias a todos.

**(Confirmé que ahora que vuelvo a tener Internet sí puedo entrar).**

---

### Post by faktorqm on 2007-11-29
y..... para sacar el dhcp tenes que primero configurar el modem para que este en la misma red que vos y demas..... si sigue tardando decime y te digo, sino tarda dejalo asi, por que es media larga la explicacion. salu2!

---

### Post by Fikcio on 2007-11-29
> si sigue tardando decime y te digo, sino tarda dejalo asi, por que es media larga la explicacion. salu2!

Sí, sigue tardando. Parece que le resulta *necesario* resolver algo — si no puede ya porque el modem está apagado, ya porque hay algún problema con el ISP, cuélgase. Modifiqué el parámetro maxfail de... ¿ppp_on_boot? (me parece que era ése), que estaba en 0 y lo bajé a 3 (0 es "reintentá ad infinitum"). Ningún cambio. Tiene que ser una bolude* , ¿no?

Gracias.

---

### Post by Fikcio on 2007-12-01
Modifiqué el archivo /etc/network/interfaces. Hice lo siguiente: "comenté out" la línea *auto dsl-provider*, desenchufé mi módem, reseteé y arrancó como si nada -- aunque sin Internet, claro. ¿Alguien tiene alguna idea? Por cierto, éste es el contenido de /etc/network/interfaces:

```
auto lo
iface lo inet loopback




auto dsl-provider #ésta es la línea que deshabilité
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider



auto eth0
iface eth0 inet manual

```

Gracias.

---

### Post by faktorqm on 2007-12-03
hace una cosa, entra al modem por la web, y deshabilitale el dhcp. y en la interfaz LAN del modem ponele 192.168.1.1 mascara 255.255.255.0 y la parte de WAN, NO LA TOQUES.
despues pone el modem en modo router, y listo, salis teniendo internet sin pppoeconf ni nada de nada.

en tu pc pones:

ip: 192.168.1.2
mascara: 255.255.255.0
puerta de enlace: 192.168.1.1
DNS: 192.168.1.1

salu2!

---

### Post by Fikcio on 2007-12-03
Gracias, faktorqm. Voy a probarlo. Pero tiene que haber algo que hacer desde Linux, ¿no es cierto?

Muchas gracias.

---

### Post by faktorqm on 2007-12-04
se... digamos, si tenias un script al inicio con el pppoeconf sacalo, y

en tu pc pones:

ip: 192.168.1.2
mascara: 255.255.255.0
puerta de enlace: 192.168.1.1
DNS: 192.168.1.1

si queres probalo en windows, luego en linux. salu2!!

---


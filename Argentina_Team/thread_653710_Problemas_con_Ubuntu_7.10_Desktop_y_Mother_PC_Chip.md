---
title: "Problemas con Ubuntu 7.10 Desktop y Mother PC Chip P23G"
date: 2007-12-30
forum: Argentina Team
---

### Post by gdavideh on 2007-12-30
Gente,

Me esta ocurriendo algo insolito.

Cada vez que inicio mi Ubuntu 7.10, en primera instancia el sistema funciona perfecto, detecta mi conexion a internet, mi placa de video, mi placa de sonido, el sistema es de lo mejor.

Ahora bien, cuando reinicio el equipo y se carga nuevamente Ubuntu, la placa de red queda deshabilitada y no solo desde el S.O. sino tambien en el BIOS, ya que recurro a este para chequear la configuración y no me esta apraceriendo la opcion del dispositivo.

Lo mas raro es que luego de resetear el BIOS Jumpeando, me detecta la placa de Red y esta todo como al principio.

El problema vuelve a repetirse cuando reinicio el equipo.

Alguno paso tambien por este mismo inconveniente?

Agradecere mucho sus comentarios.

Un abrazo y feliz año nuevo para todos!!!


David García

---

### Post by facundocorradini on 2007-12-30
si te queda trabado tambien desde el bios, entonces estás teniendo algún problema de hardware, probablemente entre la cuestión energética y la placa de red.

---

### Post by gdavideh on 2007-12-31
Puede ser.

Igualmente me suena raro, dado que Windows no tengo ningún problema, ni cuando reinicio ni nada.

Esto tambien ocurre cuando corro Ubuntu en Live CD.

No puedo entender a que se debe.

Es rarisimo que un soft pueda deshabilitar el hard, nunca me paso.

Muchas Gracias igual

---

### Post by faktorqm on 2007-12-31
para mi hay solo 2 opciones, o que tenes baja la pila del bios y por alguna casualidad te borra la conf o tenes ekl bios mal configurado :D
te recomendaria que si tenes la opcion en el bios de poner dispositivo por dispositivo a mano lo hagas, y le vayas asignando uno a uno la irq, y toda la bola, sé que rompe las ***las, pero una vez con eso, capaz se te soluciona el problema. ponele pass de administrador tb, asi no te entra nadie y cada vez que arrancas no te molesta salu2!

---

### Post by gdavideh on 2008-01-01
Gracias a ambos.

El problema persiste.

Asigne dispositivo por dispositivo y agregue pass, no solo para el setup sino también para el boot.

Corro Ubuntu en LIVE CD y cuando reinicio en Windows no me detecta la placa de red. Voy al BIOS para chequear la config y sorpresa, desaparece la placa de red. Por ende tengo que hacer un CLR CMOS y configurar nuevamente el BIOS.

Supongo que tendre que resignarme a seguir con las ventanitas, jajaj.


Gracias nuevamente a ambos.

Un abrazo.

---

### Post by Hei Ku on 2008-01-01
Aparentemente es un problema conocido del mother al resetear, que se resuelve flasheando el BIOS con el ultimo update.

Te paso un thread sobre problemas similares. Ahi dan un link a pcchips con la informacion del error y como flashear el BIOS.
[http://ubuntuforums.org/archive/index.php/t-285233.html](http://ubuntuforums.org/archive/index.php/t-285233.html)

---

### Post by gdavideh on 2008-01-01
Muchas Gracias!

Voy a chequear esta posible solución y despues les comento como me fue.

Un abrazo!

---

### Post by JunCTionS on 2008-05-02
hola, [SIZE="1"](va sin acentos porque el teclado no los agarra aun)[/SIZE]
oye, luego de instalar kubuntu (7.10 y actualizar de una vez al 8.04) no reconocio para ninguno de los dos el Ethernet, luego vi el post al que haces referencia y entonces me fui a Windows, ahi tambien entonces dejaron de funcionar todos los dispositivos de red (incluso el adaptador wifi USB que uso en kubuntu ahora)
Bueno, descargue en otra compu el programa para hacerle el flash que consegui [aca]("http://www.pcchips.com.tw/PCCWebSite/Downloads/ProductsDetail_Download.aspx?detailid=370&DetailName=Bios&DetailDesc=&CategoryID=1&MenuID=6&LanID=0") (pagina de pcchips.com.tw>Downloads>Motherboards>Socket 775(in...)>P23G>BIOS)

y al reiniciar igual siguio fallando (e imagino que ahora Windows tambien).

ahora voy a intentar ver si reiniciando "en frio" (apagando y volviendo a encender  funciona) pero dudo que ayude mucho. Alguna sugerencia?:confused:

---

### Post by Hei Ku on 2008-05-02
si flasheaste el bios tenes que reiniciar en frio. y reza, porque es lo que deberias haber hecho apenas flasheaste ;)

---

### Post by JunCTionS on 2008-05-02
reiniciar en frio no funciono, asi que busque el manual (las descargas de pcchips estan malasimas en conexion por cierto) y resetee el bios.
imagino que quizas debi haber hecho esto antes tambien.
Ya esta funcionando :)
Otra cosa es que luego vi la falla en la pagina y ciertamente no tiene absolutamente nada que ver con linux, sino que para que iniciara por el disco entre al Bios para cambiar el orden de booteo y eso daño todo... curioso que nunca antes habia entrado al bios de esta compu entonces.
gracias :)

---


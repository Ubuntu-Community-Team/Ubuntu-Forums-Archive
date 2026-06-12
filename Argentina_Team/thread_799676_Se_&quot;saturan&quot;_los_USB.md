---
title: "Se &quot;saturan&quot; los USB?"
date: 2008-05-19
forum: Argentina Team
---

### Post by qntal on 2008-05-19
Tengo 3 puertos USB en la notebook y actualmente estoy usando los 3; teclado, mouse y webcam. La webcam la estoy usando para una prueba piloto a ver si sirve como para cámara de seguridad, con lo cual esta continuamente monitoreando.

Estoy usando Ubuntu 8.04 y las pruebas las estoy haciendo con Motion y ZoneMinder. La maquina es un Celeron M 1.73ghz y 2gb RAM, hard le sobra calculo...

El tema es que noto que a veces se "saturan" los puertos USB, más precisamente donde esta la webcam. Quiero acceder a la imagen y me tira que /dev/video0 esta busy, desconecto y conecto un par de veces y por ahi agarra de nuevo, o arranca pero me muestra la mitad de la imagen solamente.
Si la conecto a otro puerto USB vuelve a andar bien pero el puerto donde estuvo queda muerto, ni el mouse agarra.

Mi pregunta es... alguno tiene idea si esto es un drama de Ubuntu, las webcam USB, mis puertos USB de mala calidad o algo por el estilo?

Quiero aclarar que como son pruebas lo que estoy haciendo, no llego a tenerla mucho tiempo activada... a los 20/30 minutos pasa. A veces aguanta todo el día sin problemas por ejemplo...

En una reiniciada, el daemon khubd tenia 100% de uso de procesador, desconecté la webcam y bajó a lo normal... eso me pasó una sola vez.

El tema es que quiero algo estable como para dejar una pc dedicada a eso y olvidarme de andar tocando... Si no se puede con las cam USB tendré que comprar una placa capturadora de varios chips y conectar cámaras ahi, pero se me hace que debe ser mas complicado de configurar.

---

### Post by oktubrer on 2008-05-19
> **qntal said:**
> El tema es que quiero algo estable como para dejar una pc dedicada a eso y olvidarme de andar tocando... Si no se puede con las cam USB tendré que comprar una placa capturadora de varios chips y conectar cámaras ahi, pero se me hace que debe ser mas complicado de configurar.

Si tenés que llegar a esa instancia, averiguá bien, no estoy mucho en tema pero existen cámaras ip, que podes conectar a un router y transmiten por ethernet.  Son las que ofrece Speedy para uno de sus productos (Cam 24, quizás podes sacar más info sobre las cámaras en el sitio de speedy)
[http://www.telefonica.com.ar/telefoniafija/pymes/cam24/](http://www.telefonica.com.ar/telefoniafija/pymes/cam24/)

---

### Post by qntal on 2008-05-19
> **oktubrer said:**
> Si tenés que llegar a esa instancia, averiguá bien, no estoy mucho en tema pero existen cámaras ip, que podes conectar a un router y transmiten por ethernet.  Son las que ofrece Speedy para uno de sus productos (Cam 24, quizás podes sacar más info sobre las cámaras en el sitio de speedy)
[http://www.telefonica.com.ar/telefoniafija/pymes/cam24/](http://www.telefonica.com.ar/telefoniafija/pymes/cam24/)

Las cámaras ip lamentablemente son carísimas, con lo que me salen 2 cámaras pago una PC con una licencia de windoze y las cámaras comunes para monitorear con cualquier soft :(

Speedy cobra una fortuna, me sale más barato que me roben todos los meses a estar pagando ese servicio :lolflag:

Además que me corre un escalofrío cada vez que oigo ese nombre, tengo ADSL Wi-Fi de speedy en el negocio y cada vez que tuve que hablar con un "técnico"... madre mía. Frases célebres: "ah no en linux no anda" "no, con esto no, tenés que tener algo mas nuevo como el windows xp o vista" "qué es esto?" (por ubuntu) "internet wi-fi no te anda con esto (esto = el router WI-FI que me dio Speedy y si, logicamente andaba)"

En fin... es una lucha :P

---

### Post by oktubrer on 2008-05-19
No, si yo te decía que averigues que cámaras eran nomás, no le estaba haciendo publicidad a Speedy.

No sabía que eran tan caras, busqué recién en ML y si, mínimo $300.

Volviendo al tema original acerca del USB, no encontré nada al respecto.

---

### Post by clasificado on 2008-05-20
> **qntal said:**
> El tema es que noto que a veces se "saturan" los puertos USB, más precisamente donde esta la webcam.
Si, se saturan. la especificación usb 2.0 define una velocidad máxima de transferencia de 480 Mbps. 

Los dispositivos que se enchufan al puerto usb conocen el límite, por lo que ningun dispositivo enchufado al usb deberia saturar el ancho de banda salvo que

1) Tengas enchufado un hub usb (lo que significa varios dispositivos enchufados al mismo puerto)

2) Tengas un dispositivo muy malo: pero muy malo eh!

>  Si la conecto a otro puerto USB vuelve a andar bien pero el puerto donde estuvo queda muerto, ni el mouse agarra.

La única saturación de puertos usb es la de ancho de banda. en cuanto se deja de usar se libera la saturación. Si un puerto queda mocho, ya es lugar de pensar en problemas de otra ídole mas específicas a tus equipos.

> 
Mi pregunta es... alguno tiene idea si esto es un drama de Ubuntu, las webcam USB, mis puertos USB de mala calidad o algo por el estilo?


- De Ubuntu no es (En mi desktop, la webcam anda joya). 
- Las webcam usb estan preparadas, justamente, para ser de webcam en usb (salvo que la tuya haya venido mal de fábrica, posibilidad nº1).
- Puertos usb de mala calidad: no veo porqué descartarlo. Tendrias que probar la misma configuracion en otra pc (ubuntu + wireless). Junto con este punto se mezcla la idea de que pueden no ser los puertos usb pero sí el chipset controlador de dichos puertos. Las notebooks son equipos muy específicos y no todas son estables en todas partes. Si nos pasas marca + modelo en una de esas encontramos algo.

Todo tiende a la idea de que hagas la misma prueba, pero en otro equipo.

> Si no se puede con las cam USB tendré que comprar una placa capturadora de varios chips y conectar cámaras ahi, pero se me hace que debe ser mas complicado de configurar.

Nada que no sea humanamente realizable.

clasificado.

---

### Post by qntal on 2008-05-20
si, en cuanto pueda voy a hacer lo que no quería, llevarme trabajo a casa y probarla con mi desktop. aunque ahi también tengo un mother muy ****(ABIT LG-95C)

la notebook es una Oliveti XPSE610. Celeron M 430 1.73ghz, 2gb RAM DDR2 533, chipset i945GM/ICH7

la webcam es una genius vieja que debe haber salido $30, asi que es muy probable que el combo **** pueda estar ****. lo que me sorprendió fue que justo el usb donde estaba la cámara quedó muerto, después de reiniciar volvió a andar con normalidad pero no hice mas pruebas con la cam.

de última podría comprar un par de estas como para probar:
[http://articulo.mercadolibre.com.ar/MLA-33845880-web-cam-genius-look-316-_JM](http://articulo.mercadolibre.com.ar/MLA-33845880-web-cam-genius-look-316-_JM)
si no logro montar el sistema sobre linux lo puedo armar sobre osx.

---


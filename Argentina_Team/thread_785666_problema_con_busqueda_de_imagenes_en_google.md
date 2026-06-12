---
title: "problema con busqueda de imagenes en google"
date: 2008-05-07
forum: Argentina Team
---

### Post by marceze on 2008-05-07
holas en primera quiero presentarme, ya que soy nuevo en el foro, soy Ezequiel, argentino, 20 años, y fiel usuario de linux, Ubuntu para ser especifico...
hace unos días, actualice mi Ubuntu 7.10 al 8.04, pero como tenia un desastre toda la pc, llena de cosas y "experimentos", saque mis archivos y la borre e instale desde 0 el 8.04...
hasta ahí todo bien...
intente instalar el AWN + xserver-xgl + compiz-fusion, los cuales no pude hacer funcionar bien, creo, por falta de una placa de vídeo (tengo onboard), luego de esto intente entrar al google para buscar unas imágenes y estaba todo bien, hasta que de repente me salto un error y me desaparecieron las imágenes y los links... pero esto solo sucede con el google y en la búsqueda de imágenes...
en Mozilla, en el apartado de:  {herramientas > consola de errores} aparece las siguientes advertencias:

-----------------------------------
error in parsing value for property 'height'. declaration droped.  línea 1
[http://www.google.com.ar](http://www.google.com.ar)
-----------------------------------
error in parsing value for property 'width'. declaration droped.  línea 1
[http://www.google.com.ar](http://www.google.com.ar)
-----------------------------------
error in parsing value for property 'cursor'. declaration droped.  línea 1
[http://www.google.com.ar/search?hl=es&q=piedras&btnG=Buscar+con+Google&meta=](http://www.google.com.ar/search?hl=es&q=piedras&btnG=Buscar+con+Google&meta=)
-----------------------------------
error in parsing value for property 'cursor'. declaration droped.  línea 1
[http://images.google.com.ar/images?hl=es&q=piedras&um=1&ie=UTF-8&sa=N&tab=wi](http://images.google.com.ar/images?hl=es&q=piedras&um=1&ie=UTF-8&sa=N&tab=wi)
-----------------------------------

no se si sera por los cambios que estuve haciendo al instalar las mejoras visuales, si alguien sabe por que sucede esto...
saludossss...

---

### Post by clasificado on 2008-05-08
> **marceze said:**
> holas en primera quiero presentarme
Bienvenido :KS
> intente instalar el AWN + xserver-xgl + compiz-fusion, los cuales no pude hacer funcionar bien, creo, por falta de una placa de vídeo (tengo onboard)
Si bien es cierto que las placas onboard dan un poco mas de trabajo mirá que se puede eh!. Un par de tips:
1 - Lo mejor que te puede pasar es una placa onblard ati, nvidia o intel. Sino, estas frito.
2 - El AWN no afecta. El compiz fusion esta joya, pero lo que mejor anda es el Aiglx que reemplaza al xgl. Podés tener complicaciones con Aiglx + ATI, pero este foro tiene experiencia en eso. Busque nomás

> luego de esto intente entrar al google para buscar unas imágenes y estaba todo bien, hasta que de repente me salto un error y me desaparecieron las imágenes y los links... pero esto solo sucede con el google y en la búsqueda de imágenes...

No te das una idea lo IMPORTANTE que es ese mensaje de error. 

De hecho, si hubieras escrito textual el mensaje solo suelto arriba y te hubieras olvidado incluso de presentarte estariamos mas informados :lolflag:

Por ejemplo: 
- Si el error tuviera que ver con el servidor x, se podria llevar a un modo mas compatible y deshabilitando compiz fusion y demás hasta ver cual es el problema. 
- Si el error es de Toolkits (GTK para firefox) habria que hacerle mantenimiento, borrando configuraciones y demás
- y así

**Una captura de pantalla es lo mas recomendable en casos como ese**, asi vemos no solo el error, sino también los detalles que lo circundan

> 
en Mozilla, en el apartado de:  {herramientas > consola de errores} aparece las siguientes advertencias: [...]

no se si sera por los cambios que estuve haciendo al instalar las mejoras visuales, si alguien sabe por que sucede esto...


Es normal. Basicamente internet es una gran bola de ****, todos los sitios tienen html mal construidos (incluso google) y esa consola te dice los malabares que hace el browser para mostrarte lo que ves. 

Es absolutamente normal. Podes ignorarlo nomás.

> saludossss... 

Mucha suerte!

clasificado

---


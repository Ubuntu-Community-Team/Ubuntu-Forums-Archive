---
title: "¿Alguien está teniendo problema con las últimas actualizaciones de Compiz?"
date: 2008-01-18
forum: Argentina Team
---

### Post by v1ncent on 2008-01-18
Uso Ubuntu 7.10, con la versión de Compiz que viene por default. La cuestión es que ayer hubo actualizaciones y ahora Compiz no funciona.
(No sé que paquetes actualizó, porque yo no estaba usando la PC en ese momento)
Cuando inicio sesión directamente me devuelve a la pantalla de login, por eso tuve que iniciar en modo seguro.

Y bueno, no tengo idea de qué puede ser, tal vez a alguno le pasa lo mismo, aunque supongo que la mayoría usa Compiz Fusion desde GIT.

---

### Post by Mauro22 on 2008-01-18
Nada por el momento!!

Mantendremos informados.

:popcorn:

---

### Post by Thalskarth on 2008-01-18
Yo tembien uso el compiz que viene por default... pero ultimamente no se bajo ninguna actualizacion del mismo... las de ayer, a mi me bajaron eran del Xorg.Org..


pero igualmente, me siguio andando todo normalemnte...

---

### Post by v1ncent on 2008-01-18
Hoy averigüé más, al parecer el problema es con los drivers de nvidia y la actualización del Kernel, porque cuando ejecuto CUALQUIER cosa que tenga algo en 3D me desloguea automáticamente.
Instalé nuevamente últimos drivers de nvidea y Compiz funcionó hasta que reinicié (como la instalación requería) y simplemente dejó de funcionar.

Debería ser fácil, porque la actualización del Kernel hizo que los drivers dejaran de funcionar, por eso solo hay que instalarlos nuevamente, pero (aunque lo haga) no funciona.

---

### Post by Mafber on 2008-01-18
Hola, por el momento no tengo problema pero no vi que se me haya actualizado el kernel
te recomiendo que instales los drivers desde envy 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
y pruebes con volver a activar compiz

---

### Post by rojojuan on 2008-01-19
Por aquí todo bien después de todas las actualizaciones.

---

### Post by brunovecchi on 2008-01-19
En los últimos dos días han habido instalaciones de Compiz y tres (!) de xorg.org. Aparentemente con el primer patch la han pifiado y han dejado sin soporte a Java a muchos. Yo no he visto esos problemas porque no estoy utilizando efectos 3d.
Al respecto, (y quizás sea un poquito off-topic), ¿la gente de acá que tiene Nvidia está usando los drivers que instala Gusty por defecto? Porque yo si, y Compiz se me vuelve inusable de lo inestable que está. Estoy usando la última versión de los Nvidia-glx-new.

---

### Post by rojojuan on 2008-01-19
Estuve leyendo que en la anteúltima actualización había un bug en xserver; en la última actualización lo corrigieron. Así, que aparentemente esta solucionada la cuestión. Después de la última actualización, alguien tiene problemas igual?

---

### Post by margori on 2008-01-19
> **brunovecchi said:**
> ¿la gente de acá que tiene Nvidia está usando los drivers que instala Gusty por defecto? Porque yo si, y Compiz se me vuelve inusable de lo inestable que está.
Yo tengo nvidia y si, es cierto, compiz consume, consume y consume RAM hasta volver a ubuntu imposible de usar. Es debido a un gran bug en el controlador de nvidia. Ya hay un lanzamiento de un beta, aunque aun no lo estoy utilizando, digamos que por cierto pudor.

---

### Post by brunovecchi on 2008-01-19
> **margori said:**
> Yo tengo nvidia y si, es cierto, compiz consume, consume y consume RAM hasta volver a ubuntu imposible de usar. Es debido a un gran bug en el controlador de nvidia. Ya hay un lanzamiento de un beta, aunque aun no lo estoy utilizando, digamos que por cierto pudor.

Ahh está bien... es lo que me parecía, ya que "de oído" me enteré que algunos estaban usando unos drivers que instalaban manualmente... yo honestamente desde que tuve que usar Automatix y alguna que otra instalación manual de los drivers antes de Feisty dije nunca más. Lo que se pueda usar con el soporte nativo de la placa, se usará, lo que no mala leche. Me cansé de que se me caiga X y editar a mano el xorg.conf.

Igual en mi caso la inestabilidad no viene de un consumo excesivo de RAM (con Compiz abierto recién usa el 25% de 2GB). Pero con mucha suerte funciona 2 horas antes de colgarse.

---

### Post by Thalskarth on 2008-01-19
> **brunovecchi said:**
> En los últimos dos días han habido instalaciones de Compiz y tres (!) de xorg.org. Aparentemente con el primer patch la han pifiado y han dejado sin soporte a Java a muchos. Yo no he visto esos problemas porque no estoy utilizando efectos 3d.
Al respecto, (y quizás sea un poquito off-topic), ¿la gente de acá que tiene Nvidia está usando los drivers que instala Gusty por defecto? Porque yo si, y Compiz se me vuelve inusable de lo inestable que está. Estoy usando la última versión de los Nvidia-glx-new.

Yo instale y uso los drivers de NVIDIA a travez del "Envy"... y no he notado esos problemas con el compiz-fusion...

prueben con esta opcion.

---

### Post by pablo0469 on 2008-01-19
Desde que recibi estas ultimas actualizaciones tambien estoy teniendo problemas con Java y cuando arranco la PC, se ahora se queda la pantalla en negro y debo mover el mouse o apretar algo del teclado para que aparezca el escritorio...
 
Conozco personalmente un programador oficial Debian, y esta es una de las razones que me esgrimio para que no use Ubuntu, ellos testean mucho mas los paquetes actualizados antes de largarlos por la red, aunque tampoco son perfectos...
 
Saludos.

---

### Post by v1ncent on 2008-01-19
> **brunovecchi said:**
> ¿la gente de acá que tiene Nvidia está usando los drivers que instala Gusty por defecto? Porque yo si, y Compiz se me vuelve inusable de lo inestable que está. Estoy usando la última versión de los Nvidia-glx-new.

> **Thalskarth said:**
> Yo instale y uso los drivers de NVIDIA a travez del "Envy"... y no he notado esos problemas con el compiz-fusion...

prueben con esta opcion.

Tenía instalado los últimos drivers desde la página oficial de nvidia, ahora los tengo instalados mediante ENVY, resultó mucho más útil, configura todo automáticamente.
El problema ya lo tengo solucionado, aunque realmente no fue fácil descifrar cuál era la verdadera causa del problema, porque si instalaba los drivers, después seguía sin querer funcionar el Compiz.
Tal vez tuvo algo que ver el [**bug**]("http://www.fentlinux.com/web/?q=node/5078") de *xerver-xorg*, el cual se actualizó ya varias veces y creo que ahora funciona bien.
Finalmente desinstalé los drivers, dejé todo limpio y lo instalé de vuelta, por suerte funcionó, así que gracias por su ayuda.

Lo que no entiendo es por qué se me actualizó el kernel y a otros todavía no, en fin, les dejo el dato: se actualizó desde la 2.6.22-14-generic a la 2.6.22-14-386.

Gracias a todos!

P.D.: Como joden todos estos problemas, siempre pasa algo por el estilo y parece que no solo a mi me pasan.

---


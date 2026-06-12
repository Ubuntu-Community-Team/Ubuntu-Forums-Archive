---
title: "Ubuntu 16.04-sin entorno gráfico"
date: 2017-04-18
forum: Argentina Team
---

### Post by Vero1 on 2017-04-18
Hola nuevamente.

Explico lo que me pasa. 

Tenía instalado Ubuntu y Mate. Como el Sistema se estaba tornando muy lento (tengo Intel Pentium IV, 2 Gib de Ram, 3,0 Mhz) Disco de 500 Gib, particionado para Ubuntu y Windows7, decidí desinstalar Mate Environment. Para éso fuí a Ubunlog( de ahí instalé Mate) para seguir las instrucciones de desinstalación. Al reiniciar me sale un escritorio color verde completamente vacío pero con cursor funcionando. 

He estado estos útimos 3 días buscando una solución pero en todos lados indica entrar en tty para poder escribir los comandos necesarios para recuperar el entorno gráfico.

Lo que pasa es que no me puedo loguear con mi usuario porque me rechaza el password.

Por favor, alguna orientación para poder solucionar este problema, ya que no sé qué más hacer y como Administro una Fan-Page pues...

Gracias de antemano y saludos

pd.
pueden avisar por mail porque mi celular los recibe

---

### Post by aromo2 on 2017-04-18
Tienes dos problemas. Uno: no tienes ningun entorno grafico instalado, y Dos: el problema del password de tu usuario.
Te sugiero, cuando arranques el sistema y llegues al escritorio verde que mencionas, presiona las teclas Alt-F2 simultaneamente. Eso de debe hacer que te pida el nombre de usuario en modo texto. Como tu usuario no funciona, intenta entrar como root si sabes el password. De lo contrario vas a tener que reiniciar con el LiveCD y escoger la opcion de rescate mientras esté arrancando el CD. Una vez entres en modo de recuperacion, puedes cambiar el password de root y de tu usuario. Y ya que estás ahí cambia el runlevel:
```
[COLOR=#000000]systemctl set-default multiuser.target[/COLOR]
```

Espero esto te ayude.

---

### Post by Vero1 on 2017-04-18
Hola aromo2 (me encantó tu Nick) :)

Probaré a ver como me va con el LiveCD y te informo.

Muchas gracias por la pronta respuesta.

Saludos

---

### Post by Vero1 on 2017-04-18
Hola aromo2,
He recorrido todas las opciones del LiveCD (rescate, según me dijiste) pero me informa que este disco no tiene opción de rescate. Me sugiere indagar en Internet...
Alguna otra sugerencia?

Gracias

---


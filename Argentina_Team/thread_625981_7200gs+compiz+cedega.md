---
title: "7200gs+compiz+cedega"
date: 2007-11-28
forum: Argentina Team
---

### Post by llove on 2007-11-28
hola, tengo un problema q seria el siguiente, luego de luchar logre finalmente instalar los drivers de nVidia, y desinstalando xserver-xgl logre tener direct rendering, entonces cedega anda, pero compiz me anda lento con estos drivers, a diferencia de los restricted drivers+xgl, pero de esta ultima manera no logre conseguir direct rendering, a alguien le pasa lo mismo?' soluciones??

edit: instale compiz icon y tilde las opciones indirect rendering, y loose binding, y la verdad q anda muy bien ahora, y cedega tambien. saludos ,

---

### Post by faktorqm on 2007-11-29
hola, no entendi lo que quisiste decir. a ver si te ayudo un poco:

con el envy, te instala el driver de nvidia y aiglx, y yo tengo asi a compiz-fusion y me anda de maravillas. aiglx es mas rapido y tiene mejor soporte que xgl. xgl usa una capa mas para renderizar. en mi caso, utilizar xgl mas compiz-fusion, significa ver la mitad de las pantallas negras, la mitad de las ventanas sin marco, y ese tipo de cosas.
la verdad no probe con lo del cedega, pero el direct rendering lo podes activar o desactivar independientemente de si tenes aiglx o xgl. yo para correr compiz-fusion tengo agregado en el inicio esto:

```
compiz --replace -c emerald
```

Ahora si tenes el problema de las pantallas negras, o del vlc que se cierra ni bien queres ver un video, tenes que cambiar por:

```
compiz --replace --indirect-rendering -c emerald
```

fuente de los datos: [http://tuxpepino.wordpress.com/2007/06/30/instalar-compiz-fusion-en-ubuntu-feisty/](http://tuxpepino.wordpress.com/2007/06/30/instalar-compiz-fusion-en-ubuntu-feisty/)

espero que te haya servido. salu2!

---

### Post by llove on 2007-11-29
hola, con envy, no tenia direct rendering, al menos el cedega me decia q no tenia openGL, y cuando ponia en la conosola, glxinfo | grep direct, me decia q no tenia direct rendering,,,,despues probare de nuevo. gracias por la data. saludos

---


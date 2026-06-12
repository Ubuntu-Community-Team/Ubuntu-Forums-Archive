---
title: "Ubuntu fesity se empezo a colgar"
date: 2007-06-07
forum: Argentina Team
---

### Post by katon on 2007-06-07
Hola gente ,  les hago una consulta.
Estoy usando Ubuntu Feisty desktop desde hace un tiempo , con Beryl funcionando relativamente bien para una placa de video 64 mb 3d , Pentium 4 1.6 ghz es el microprocesador.

Ahora, dede hace unas semanas se me cuelga la maquina mal, osea no es que solo se cuelga el Xserver la parte grafica, sino todo, no puedo entrar a las lineas de comando con Cntrl+alt+F1 ....
Hace un par de semanas hubo una actualizacion del kernel la cual se efectuo automaticamente y despues de eso tuve problemas para con la parte grafica pero desde ese entonces arranco la maquina con el kernel  anterior en las opciones del GRUB. No se si el problema sera ese o otra cosa. 
No se por donde empezar a verificar. O sea en realidad no es terrible no se cuelga siempre y todo el tiempo, pero antes nunca tenia problema, aparte es linux que funciona bastante mejor que otros sistemas operativos en cuanto a errores fatales de colgarse. 
Por otro lado empece a pensar en el hardware que talvez tiene algun problema, o el mother (algun capacitor) para el que entiende de electronica.. o que se esta bancando varias cosas juntas que consumen recursos como Beryl y otros programas abiertos al mismo tiempo le pesa para el tipo de PC. Pentium 4 1.6 ghz , 640 mb RAM , P. video Ati mobility 440 mx 64mb .
Por otro lado los requerimientos para estas versiones de linux no deberian tener problemas aunque corran en pentium 3 ...
Bueno nose que opinan..
Gracias desde ya.

---

### Post by gepatino on 2007-06-07
Suponiendo que no tengas problemas de hardware, ¿probaste deshabilitando beryl?

Entiendo que todos esten como locos con sus cubos :) pero hasta donde sé no hay versiones estables de beryl o compiz aún... en algunas maquinas funcionan bien, en otras no tanto.

Si te parece que el problema surgió después de actualizar el kernel, también puede ser que los modulos de la placa de video no sean estables para este nuevo kernel. Podes volver a instalar el kernel anterior (si no lo eliminaste deberias tenerlo todavía), y al iniciar seleccionarlo en el menu del grub.

---

### Post by undiaperfecto on 2007-06-07
yo tengo el mismo problema, aunque hace un par de dias que no se cuelga mas.
desde la ultima actualizacion de kernel que me pasa, es como si fuera un problema de la placa de video, tambien tengo una gforce de 64mb, al principio pense que era la placa que fallaba, o tal vez el micro que calentaba mucho, pero despues del cuelgue verifique y los coolers funcionaban perfecto.
se puede decir que todavia me pasa, aunque hace ya como 4 dias que no se cuelga mas.

---

### Post by katon on 2007-06-07
Gracias por las respuestas..
mira Undiaperfecto ahora estos ultimos 3 dias tampoco me pasa... 
igualmente estos cuelgues son en el kernel anterior osea yo cuando bootea la Pc selecciono el viejo. 
puede ser que sea beryl..aunque me anda de maravilla para la poca placa de video que tengo...
y me cuesta creer que por correr cosas como Beryl  y KIBA-DOCK (lo instale ayer) en mi "vieja" maquina se cuelgue ....deberia andar lento o no correr pero no colgarse ... aunque no descarto lo que decis GEPATINO de que beryl no es estable.

---

### Post by godzeus on 2007-06-07
Estaba leyendo tu post, y me llamo la atencion, porque hcace un par de dias, hice la actualizacion automatica, y actualizo, el kernel, por lo que temi tener algun tipo de problemas, con el video, ya que en Edgy, cuando actualizaba el kernel dejaba de andar la mitad de las cosas, pero el unico problema que tube ahora fue, reemplazar el xorg.conf, con un backup que tenia, entrar en gnome, ejecutar Envy, y listo el pollo, el escritorio tal como lo tenia antes, solo que con otro kernel.
Quizas puede ser un problema de restricted-modules o algo asi, yo te recomendaria, probar Envy, qe te baja los ultimos driver, te los compila, instala todo lo que haga falta, y solo tenes que reiniciar el modo grafico, y todo funcando perfecto.

Saludos.

---


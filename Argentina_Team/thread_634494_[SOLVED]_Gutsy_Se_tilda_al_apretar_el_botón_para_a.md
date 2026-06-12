---
title: "[SOLVED] Gutsy: Se tilda al apretar el botón para apagar."
date: 2007-12-07
forum: Argentina Team
---

### Post by valucha on 2007-12-07
[COLOR="DarkOrchid"]Hola niños, acá vengo nuevamente con un nuevo problema.
Reinstalé Gutsy, porque estaba aburrida, suelo hacerlo o más cuando tengo que estudiar y necesito buscar una excusa para distraerme :)
En fin, es algo que nunca me habia pasado, misma distro y versión, mismo ordenador y todo pero un nuevo problema nunca antes visto!!...

EL tema es el siguiente. apenas aprieto el botón de apagar (tanto en el panel como en la Avant WIndow Navigator- porque también lo tengo allí-) se tilda completamente, EXCEPTO el mouse. LO único que puedo hacer es apretar ctrl +alt +backspace y desde el GDM poner "apagar".
¿Qué puede ser?. Hice cosas de optimizaciòn que antes con las otras versiones no había hecho, como por ejemplo sacar algunos servicios de inicio ¿Puede ser eso?.


Desde ya mil gracias :D Saludos.[/COLOR]

---

### Post by Mafber on 2007-12-07
Hola, a mi me pasa lo mismo. Se me colgaba todo.
Lo reinstalé y después de instalar algunos programas.. otra vez!!!
Lo volví a reinstalar... otra vez se me cuelga. Empezó todos los problemas después que instalé algo que era para usar los temas de emerald. Pero no estoy seguro que sea esto del emerald. y no encuentro entre los log algo que me diga que esta pasando :confused:

---

### Post by santiagoward2000 on 2007-12-07
> **valucha said:**
> [COLOR="DarkOrchid"]Hola niños, acá vengo nuevamente con un nuevo problema.
Reinstalé Gutsy, porque estaba aburrida, suelo hacerlo o más cuando tengo que estudiar y necesito buscar una excusa para distraerme :)[/COLOR]
JAJA! Somos 2!!!

> **valucha said:**
> [COLOR="DarkOrchid"]EL tema es el siguiente. apenas aprieto el botón de apagar (tanto en el panel como en la Avant WIndow Navigator- porque también lo tengo allí-) se tilda completamente, EXCEPTO el mouse. LO único que puedo hacer es apretar ctrl +alt +backspace y desde el GDM poner "apagar".[/COLOR]

¿A que te referís con que se cuelga todo? ¿Puede ser que se oscurezca la pantalla como pasa normalmente antes de que aparezcan las opciones para apagar?

---

### Post by valucha on 2007-12-07
[COLOR="DarkOrchid"]No directamente no llega ni a oscurecerse y mucho menos aparecer el cuadro de dialogo en el que puedo poner "apagar" osea... aprieto la puertita para salir y chau, solo puedo mover el mouse o reiniciar las X... y con sueret proque hay vees que ni eso me deja hacer :S.


Voy aportando más datos:

Compu:
M2N4-Sli (mother con chipset nforce 4)
AMD X2 4200+
1024 ddr2 667 Kingston
Nvidia Gforce 7300 gt
Disco Sata II de 80 creo que es maxtor :P
monitor SyncMaster 740N Samsung
mouse y teclado Genius :p jaja

Tengo Compiz Fusion que viene por defecto, con las opciones extendidas que las bajé desde el Synaptic, AWN, Screenlets (pero los instalé hoy y esto venia desde hace rato).

Nada más creo, cualquier cosa pregunten.[/COLOR]

---

### Post by santiagoward2000 on 2007-12-07
A ver Vale, ¿pasa algo si despues de apretar el boton tocas ESC?

---

### Post by valucha on 2007-12-08
[COLOR="DarkOrchid"]Lo probé y no me da bola.
Noté que minimamente pareciera que la pantalla se oscurece (pero muyyyyyyyyyyy poquito) ¿Será algo de compiz?[/COLOR]

---

### Post by Mauro22 on 2007-12-08
Me anoto!


Me sucede cuando quiero apagar la PC con menos de 10 minutos de estar encendida...

Apreto el boton y lo unico que anda es el mouse. A los 3/4 minutos aparece el cuadro.


Lo solucione haciendo un script con 'sudo halt' y lo puse en el escritorio.

Sino hagan Alt+F1 cambian a consola y lo apagan.


:guitar:

---

### Post by ariel on 2007-12-09
> **valucha said:**
> [COLOR=DarkOrchid]Hola niños, acá vengo nuevamente con un nuevo problema.
Reinstalé Gutsy, porque estaba aburrida, suelo hacerlo o más cuando tengo que estudiar y necesito buscar una excusa para distraerme :)
En fin, es algo que nunca me habia pasado, misma distro y versión, mismo ordenador y todo pero un nuevo problema nunca antes visto!!...

EL tema es el siguiente. apenas aprieto el botón de apagar (tanto en el panel como en la Avant WIndow Navigator- porque también lo tengo allí-) se tilda completamente, EXCEPTO el mouse. LO único que puedo hacer es apretar ctrl +alt +backspace y desde el GDM poner "apagar".
¿Qué puede ser?. Hice cosas de optimizaciòn que antes con las otras versiones no había hecho, como por ejemplo sacar algunos servicios de inicio ¿Puede ser eso?.


Desde ya mil gracias :D Saludos.[/COLOR]

cuando se tilda, yo haria alt-f2, login en la consola, y chequearia los logs a ver que esta esta pasando (/var/log/messages, /var/log/Xorg etc etc)
necesitas mas info sobre el problema para poder ver como solucionarlo
ciao

---

### Post by ombzzz on 2007-12-09
[ligeramente off-topic]

> **Mafber said:**
> ... Empezó todos los problemas después que instalé algo que era para usar los temas de emerald. 

mmmm.. yo estuve teniendo problemas con el "switch user" ( el cambio de usuario )... cuando cambio el usuario muchas veces me muestra la pantalla toda en blanco y no tengo forma de volver a ver bien la pantalla de ese usuario y tengo que reiniciar

para solucionarlo suspendi el Compiz y deje Metacity nomas y desde ahi no tuve mas problemas ( ahora el switch user anda joya ).

tambien tenia el infamous problema de compiz-me-deja-las-ventanas-sin-la-barra-de-titulo que lo veo archi-repetido en casi todos los foros de ubuntu

conclusion: creo que falta un poco mas de testing y desbicheo al compiz+ubuntu-7.10 para que sea usable y no se torne una molestia, por lo menos en mi maquina ( Athlon 32 bits 2.4ghz 512 MB Nvidia 6600gt driver binario nvidia 100.4.19 )

mas alla de eso esta bueno el compiz+emerald. cuando se me solucionen esos "detalles" los voy a volver a habilitar

valucha, fijate de probar volver a metacity ( /preferencias/apariencias/efectos visuales -> ninguno ) a ver si es eso...

----
Aguante ubuntu!

---

### Post by valucha on 2007-12-11
[COLOR="DarkOrchid"]Mmmm no puedo abrir la terminal, no puedo hacer nada aveces :S
Alguna otra forma de ver el log?

Me parece igual que deshabilitar compiz no es la solución, puedo vivir sin el, pero si descubro que es un bug mejor reportarlo, sino lo hago yo ni nadie nunca se soluciona :)[/COLOR]

---

### Post by Mafber on 2007-12-15
ombzzz: ya volé compiz y no pasa nada. Estoy medio perdido y no se que puede ser :( . Por lo pronto lo solucioné: cuando quiero reiniciar pondo en reboot y listo. 
No quiero reinstalar... voy a seguir este problema hasta encontrar una solución o que con una actualización se solucione. Si encuentro algo lo posteo :)

---

### Post by valucha on 2007-12-16
> **Mafber said:**
> ombzzz: ya volé compiz y no pasa nada. Estoy medio perdido y no se que puede ser :( . Por lo pronto lo solucioné: cuando quiero reiniciar pondo en reboot y listo. 
No quiero reinstalar... voy a seguir este problema hasta encontrar una solución o que con una actualización se solucione. Si encuentro algo lo posteo :)

[COLOR="DarkOrchid"]A mi me pasa igual ya probé mil cosas y lo que hago es control alt backspace y despues ahi apago...
No voy a reinstalar hasta encontrar la solución o cansarme :p[/COLOR]

---

### Post by valucha on 2007-12-16
[COLOR="DarkOrchid"]Ya encontré la solución, por lo menos a mi problema.
Había notado que la otra vez cuando instalé Gutsy no me había pasado y esta vez era porque tratando de optimizar removí (siguiendo una guía que encontré en internet) servicios que no debía haber removido. UNo de ellos: grnome-power-manager.
Lo agregué de nuevo y anda de maravillas.

Igualmente fijate en internet Mafber, está reportado 2 veces el bug pero desde "perspectivas" diferentes.una dice quew tenes que agregar el servicio que yo quité... y la otra dice que tenés que sacar el gdm me parece... 

SUerte  y ojalá te sirva mi data :)[/COLOR]

---

### Post by Moonlit Knight on 2007-12-19
Mmmm pensé que el gnome-power-manager era para administrar la batería en las laptops

---

### Post by Mafber on 2007-12-19
Valucha: te cuento que no se que pasó pero dejo de hacer el cuelgue. Debe de haber corregido algo alguna actualización :confused: no lo probe a fondo pero ya van 3 dias que no se cuelga. si vuelvo a tener problema pruebo lo que me decís. Gracias :)

---

### Post by FiGi on 2007-12-20
me pasaba exactamente lo mismo que a vos valucha.
Habia desactivado gnome-power-manager y al volverlo a activar salio andando todo correctamente.
Espero que dure. 
Saludos a todos, este fue mi primer post :lolflag:

---

### Post by User21 on 2007-12-20
**Felicitaciones por tu 1er post :D **

---

### Post by vmstkd on 2008-01-02
Ja! me pasaba lo mismo, gracias por la solucion, parece que varios seguimos ese tutorial de optimizacion (muy bueno por cierto:) ) y pensabamos que era para las baterias de las laptop. Active de nuevo la opcion y todo de 10. 
Gracias:lolflag:

---

### Post by sanflores on 2008-02-22
misma situación... decidi "optimizar" mi ubuntu (jeje) y me puse a borrar cosas innecesarias como todo lo de impresora... (no tengo) lo de bluetooth... (no tengo) el power manager... (no tengo notebook :P), etc. Me empezo a pasar eso (pero dps de 30 segundos mas o menos se me solucionaba...) volvi a instalar el power manager... y anda la mitad de las veces... y como tengo el home en otro lado... borron y cuenta nueva :D

CONCLUSIÓN: No borrar cosas de ubuntu :popcorn:

---

### Post by hernan blau on 2008-02-22
A Mi me pasa algo parecido éro sólo en la de escritorio y no en la portáti. Aprieto el botón, la pantalla se pone oscura y queda así, la luz verde de la cpu queda encendida. Probé con halt, shutdown, agregando a algunos archivos poweroff (según posts que encontré) y nada. Sólo me queda desenchufar. Suerte.

---


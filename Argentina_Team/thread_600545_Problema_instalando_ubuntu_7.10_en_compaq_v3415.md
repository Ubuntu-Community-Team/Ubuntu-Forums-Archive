---
title: "Problema instalando ubuntu 7.10 en compaq v3415"
date: 2007-11-02
forum: Argentina Team
---

### Post by niko_3100 on 2007-11-02
Gente desintale feisty formatie el disco y quise instalar gutsy el problema es que cuando queire cargar el live cd va todo joya pero me tira este error siempre **bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed. ** y se me qeuda colgada ahi, probe tirando el modo grafico seguro y lo mismo, prove apretando F6 en donde dice splash poniendo nosplash y ahi fuie donde me fije el error, lo peor este cd de gutsy ya lo instale en una pc (la del laburo) y otra en mi vieja notebook y todo joya, evidentemente tengo un problema con ese bcm43xx que es el controlador o algo de la tarjeta wifi broadcom que tengo en mi compaq v3415. Me grabe otro cd de gutsy a ver si era eso y nada, ahora me estoy bajando otra ves gutsy desde un ftp de estados unidos pero me parece que es un error del gutsy mas que nada. Tambien probe levantando el live cd de feisty y me lo levanto de diez me tiro el mismo error pero siguio cargando todo, despues eso se soluciona con ndiswrapper y los driver de xp del wifi broadcom pero no entiendo porque me cuelga eso el live cd o sea ni siquiera termina de cargar todo ni en modo grafico ni en modo texto y ya no se que hacer estoy con windows xp y me quiero suicidar jajaj!!! Hay algun comando para que no intente cargar la tarjeta wifi? o desactivarla o algo?? Esta tarjeta broadcom es de terror para linux me quiero cortar un.... eso. AYUDA PLEASE!!!

---

### Post by Hernán-Amaya on 2007-11-02
probaste instalándolo con el cd alternativo?

---

### Post by niko_3100 on 2007-11-02
Sip, es lo mismo el tema no es ni la placa de video es la tarjeta wifi siempre la carga en el alternate cd tambien :S

---

### Post by Apipote on 2007-11-02
Yo tengo una Compaq f566la y podes leer mis post del padecimiento que es instalar ubunutu en mi laptop, sobretodo con la placa de video nvidia, y  las tarjetas wifi broadcom. De terror!!
Los drivers propietarios que hay en los repositorios, a mi, no me sirvieron para nada.
Habrá que esperar, o metele un xp que anda bárbaro asi que no te cortes las ........
Slds a todos
:)

---

### Post by niko_3100 on 2007-11-03
Bueno gente desisti y volvi a la version 7.04 creo que gutsy todavia esta con un par de bugs, alguien sabe como puedo informar este problema a los desarrolladores?? Como soy nuevo (desde marzo que uso GNU Linux) no se bien eso, otra cosa si espero un poquito subiran una imagen mas actualizada?? Gracias. OJO EL PROBLEMA ES CON LA TARJETA WIFI BROADCOM.

---

### Post by marianom on 2007-11-03
Intentá encontrar tu error [aca]("https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=broadcom&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=") para ver si alguien lo reportó y si existe solución. Si el bug está, te sugiero te suscribas a él contando tu problema. Cuando esté solucionado, recibirás un mail informativo.
Si no existe tu problema mi sugerencia es que subas el bug. Fijate antes de hacerlo de recolectar toda la información que te sea posible (cuando pasa, con que entorno y hardware, cuales son los mensajes de error, etc).
Con esa información podés crear tu bug (que tiene que ser en inglés). Si no tenés confianza para escribir el bug (ya sea por nivel de conocimientos o por nivel de inglés) te invito a que postees aca toda la info que puedas y entre todos te damos una mano para que lo armes.

---


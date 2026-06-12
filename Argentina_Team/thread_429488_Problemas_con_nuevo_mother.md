---
title: "Problemas con nuevo mother"
date: 2007-05-01
forum: Argentina Team
---

### Post by backstab on 2007-05-01
Antes tenia un mother MSI 795x platinum power up edition con chipset Intel 975x. me cayo un rayo y se me quemó. compre un nuevo mother es un Asus P5W DH con el mismo chipset. el problema es que cuando quiero cargar el ubuntu se cuelga cuando carga y cuando quiero poner el cd para reinstalar me pone

//bin/sh: can't access tty ; jobcontrol turned off (initramfs)

les agradezco su ayuda

---

### Post by Gideon26 on 2007-05-01
hola revisate que este bien configurada la mother? por lo que decis es un problema de hardware, reviza  tambien la memoria si son las mismas que tenias antes es probable que estas se halllan dañado.

---

### Post by backstab on 2007-05-01
la memoria no es. anda perfectamente en windows. es más el ubuntu edgy eft que tengo me anda perfecto si desabilito el jmicron pero al deshabilitarlo se desabilita la grabadora de DVD y cuando arranca no me funcionan ninguna de las dos placas de red que trae onboard el mother ni tampoco la inalambrica. El tema es que queria instalar feisty, pero me dice lo que puse arriba. Tengo un solo disco rigido con la particion ocupada por el edgy que queria pasar a feisty, y otra particion con xp.

---

### Post by Gideon26 on 2007-05-01
Probaste usar el Live Cd de Feisty? (osea arrancando desde el live?) por lo que tengo entendido el jmicron, es soportada por feisty fawn pero no por edgy creo que ahi es todo tu dolor de cabeza. 
Te recomiendo que hagas unas modificaciones a tu hardware no es mas que conectar tu grabadora en el PRI_IDE (actualmente seguramente la tenes conectada en el PRI_EIDE que es el que controla JMICRON)
fijate en el manual donde esta el PRI_IDE y conecta ahi tu grabadora(por lo general esta al lado de la Floppy) luego de conectada la Grabadora en PRI_IDE entra a la BIOS. Y hace este cambio

Bios==> Menu Main===> IDE Configuration 

IDE Operate Mode selecciona "Enhance mode"  y en Enhance Mode Suported on=> S-ATA + P-ATA
guarda los cambios y sali ya te detecta la grabadora y creeria que no tendrias problemas con la placa de red. y si queres vas a poder hacer el upgrade para feisty fawn. el problema surge de que el edgy (el kernel mejor dicho) no soporta el jmicron lo que el feisty si(o al menos deberia) bueno saludos intenta hacer el cambio y contame si te funciono. saludos

---

### Post by backstab on 2007-05-01
antes que nada gracias por contestar y tratar de ayudarme, tengo un embole con esto :mad: ,estuve probando esta tarde y efectivamente la config del bios esta como vos me decis y la grabadora esta conectada en el primary ide (solamente trae uno) cuando quiero bootear con el live cd de feisty me pone el bendito:

//bin/sh: can't access tty ; jobcontrol turned off (initramfs)

la unica que me queda me parece es hacer backup y formatear para instalar el XP porque con el edgy no tengo internet ni grabadora :( 
Tendre que esperar a mas adelante

---

### Post by Gideon26 on 2007-05-01
Hola bueno queria decirte que te fijes bien en la mother estuve revizando el manual por lo que vos me decis es la P5W DH DELUXE (linda mother por lo que estuve viendo) tenes dos conectores ide uno controlado por Jmicron(color negro cerca de los slot pci y los 2 conectores usb son de color azul) y uno por ICH7R (de color azul esta acostado medio raro pero esta asi parece que quieren ahorrar espacio) pegado a la floppy bueno este ultimo ide es donde tenemos que hacer funcionar la dvd ya que por desgracia el kernel se colapsa con el controlador jmicron fijate eh intentalo (acordate de activar el dma en la bios) saludos espero que te sirva esa configuracion. la mother tome referencia de [http://www.psicofxp.com/forums/recomendaciones-de-compra-venta-de-hard.271/387666-review-asus-p5w-dh-rev-001-a.html](http://www.psicofxp.com/forums/recomendaciones-de-compra-venta-de-hard.271/387666-review-asus-p5w-dh-rev-001-a.html)
bueno y googleando encontre uno que soluciono instalando el feisty en esa mother te dejo la dire de la pagina.

[http://foro.noticias3d.com/vbulletin/showthread.php?t=191721](http://foro.noticias3d.com/vbulletin/showthread.php?t=191721)

saludos y suerte (felicidades por esa mother esta muy buena por lo que vi )

otra solucion es que pruebes con la version alternate de feisty

---

### Post by backstab on 2007-05-01
huy man no puedo ser tan pero tan colgado.ni bien dijiste slot pci acostado azul me acorde crei que solo traía uno... se me re paso por alto me parece que ahora sale. voy a hacer los cambios. mil gracias.

---

### Post by backstab on 2007-05-02
Bueno todo salio perfecto. (perdon por olvidar el pequeño detalle del otro ide). me arranco el ubuntu Edgy y tambien me anduvo el Feisty desde el cd pero no me anduvieron ninguna de las placas de red que tiene el mother. pero encontre una solucion :)  antes de que se me queme por completo el otro mother anduvo un tiempo y como se le habia quemado la placa de red en un principio empeze a usar una placa 3com que si me reconocia el Edgy y la voy a usar ahora de nuevo.
Bueno Gideon te agradezco muchisimo la ayuda que me diste. Estoy feliz con el ubuntu de nuevooo!!

---

### Post by backstab on 2007-05-02
Al final todo anduvo en Edgy... (perdon por los repetidos post) me reconocio las placas de red y también la inalambrica, no se desconfiguró ni siquiera la aceleracion grafica.

Tuve la oportunidad de ver como se comportan windows y ubuntu ante un cambio de hardware:

Windows: tuve que Reinstalar absolutamente todos los drivers incluidos los de la placa de video (hasta el mouse) 

Ubuntu: no tuve que intervenir en nada Solo poner la ip la mascara de subred y la puerta de enlace en la configuracion de red.

---

### Post by Gideon26 on 2007-05-02
jaja que bueno Backstab viste esa es la ventaja de un OS GNU/Linux y el ubuntu es una linda distro de las versiones que podemos encontrar. bueno me alegro el haberte sido de ayuda. Saludos:popcorn: :lolflag:

---


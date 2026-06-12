---
title: "instalación no detecta ningun lector de cd rom"
date: 2007-07-13
forum: Argentina Team
---

### Post by martin cocco on 2007-07-13
Hola, estoy tratando de instalar xubuntu con el alternate cd, pero cuando hace la deteccion de hardware me dice que no encuentra ninguna lectora de cd rom...
Tengo una grabadora samsung cd-rw
Si alguien puede ayudarme con esto se lo agradecería

---

### Post by Al_maverick on 2007-07-13
la grabadora es sata o ide? yo tuve ciertos problemas con un DVD sata de las ultimas HP, aunque anduvo con la ultima version.

---

### Post by martin cocco on 2007-07-13
Si, es IDE... va, estoy en la pagina de la lectora y dice conector de la interfaz: ATAPI BUS (E-IDE)
Tiene la conexion comun... pasa que como nunca vi las otras no se si esta es la que se llama IDE...

---

### Post by Al_maverick on 2007-07-13
si es la conexion comun, entonces es un IDE. Lo que tendrias que hacer es buscar el modelo especifico del mother y de la lectora, y ver si hay algun problema reportado.
Tambien podes probar con el switch acpi=off y nolapic=off
Eso funciona con algunas lectoras problematicas.

---

### Post by martin cocco on 2007-07-14
Ya pude instalar xubuntu! agregue un poco de ram en mi maquina y pude hacer la instalacion desde el livecd. No hubo ningun problema con la lectora de cd... Ahora lo que no consigo es configurar la red. 
La conexion es con una placa ethernet, desde un router. Por lo que vi en las otras maquinas conectadas, el servidor es del tipo DHCP, con lo cual deberia detectar la conexion y configurarla automaticamente, pero no lo hace. En la ventana de propiedades de la conexion ethernet esta puesto '' configuracion: DHCP '', pero los datos de abajo estan en blanco (direccion IP, puerta de enlace, etc). Probe de llenarlos a mano poniendo IP estatica pero no pasa nada. 
Lo que me llama la atencion en que tengo la version Damn Small Linux (DSL), y esta si me reconoce la conexion sin que configure nada. De hecho ahora estoy escribiendo esto desde la DSL. 
Alguien sabe algo???
graciass

---

### Post by Al_maverick on 2007-07-14
Me alegro que lo hayas podido instalar. En general yo uso el alternate CD para instalar porque tuve mejores experiencias con ese.

la placa te la reconoce bien. Que te aparece si pones ifconfig en la consola?
tambien verifica que pasa cuando intenta conseguir una direccion por dhcp:

sudo dhclient

---


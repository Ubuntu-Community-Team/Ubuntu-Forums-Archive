---
title: "Apagado automatico con bateria baja"
date: 2007-12-03
forum: Argentina Team
---

### Post by santiagoward2000 on 2007-12-03
Hola gente!
Tengo una duda. En Xubuntu, en las propiedades del plugin **Battery Monitor** para el panel, hay una opción para correr algún comando cuando la batería llega a nivel crítico. ¿Se puede poner algún comando para que la compu se apague automáticamente? ¿Cuál sería?
Gracias!

---

### Post by marianom on 2007-12-03
No sería mejor un hibernate? Por lo menos así vas a recuperar lo que estuvieras haciendo apenas la puedas reconectar.

En ese caso, proba con 
/etc/acpi/hibernate.sh 

Ahí vas a encontrar muchos scripts más con variados comandos (apagar cuando se presiona el boton de apagado, suspender, poner a dormir, etc, etc) para que investigues un poco.

---

### Post by santiagoward2000 on 2007-12-03
> **marianom said:**
> No sería mejor un hibernate? Por lo menos así vas a recuperar lo que estuvieras haciendo apenas la puedas reconectar.

En ese caso, proba con 
/etc/acpi/hibernate.sh 

Ahí vas a encontrar muchos scripts más con variados comandos (apagar cuando se presiona el boton de apagado, suspender, poner a dormir, etc, etc) para que investigues un poco.

GRACIAS :KS
Ya mismo me pongo a revisar qué hay ahi!

---

### Post by santiagoward2000 on 2007-12-04
Una pregunta: ¿no necesito correr esos comandos como root? Porque no sería muy "automático" si tengo que poner mi clave...

---


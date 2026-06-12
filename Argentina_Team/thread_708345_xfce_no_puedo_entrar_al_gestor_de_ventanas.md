---
title: "xfce no puedo entrar al gestor de ventanas"
date: 2008-02-26
forum: Argentina Team
---

### Post by Hernán-Amaya on 2008-02-26
Cuando quiero entrar para configurar a mi gusto  las opciones del gestor de ventanas me sale este mensaje :"Esta configuración no puede funcionar con su gestor de ventanas actual (unknown)"

Aclaro tengo ubuntu y kde4, como quise probar Xfce instale xubuntu desktop

espero que algún xubuntero me pueda tirar una mano.

desde ya muchas gracias!!

---

### Post by santiagoward2000 on 2008-02-26
> **Hernán-Amaya said:**
> Cuando quiero entrar para configurar a mi gusto  las opciones del gestor de ventanas me sale este mensaje :"Esta configuración no puede funcionar con su gestor de ventanas actual (unknown)"

Aclaro tengo ubuntu y kde4, como quise probar Xfce instale xubuntu desktop

espero que algún xubuntero me pueda tirar una mano.

desde ya muchas gracias!!

Hola!
Yo tengo el mismo problema cuando cierro Compiz. Lo que pasa es que no se carga bien el xfwm. Probá tocar Alt-F2 y poner:
```
xfwm4 --replace
```
Espero que te ayude.
Saludos!

---

### Post by Hernán-Amaya on 2008-02-26
gracias por la respuesta pero ahora que reinicie donde antes decía unknown ahora dice metacity así que me esta tomando el gestor de gnome.

Alguien sabe que archivo tocar para que cuando entre a xfce utilice xfwm4 y no metacity?

desde ya muchas gracias!!

---

### Post by santiagoward2000 on 2008-02-26
> **Hernán-Amaya said:**
> gracias por la respuesta pero ahora que reinicie donde antes decía unknown ahora dice metacity así que me esta tomando el gestor de gnome.

Alguien sabe que archivo tocar para que cuando entre a xfce utilice xfwm4 y no metacity?

desde ya muchas gracias!!

Podrías pobrar agregar **xfwm4 --replace** a Autostarted Applications. Andá a **Applications/Settings/Autostarted Applications** y agregalo.
Lo único que no sé es si eso se aplica a todos los DE, como yo solo uso Xfce. No sé si cuando entres a KDE o Gnome no va a tratar de correr xfwm4 igual.
Saludos

---

### Post by Hernán-Amaya on 2008-02-27
no lo puse en el inicio pero ya había probado con "xfwm4 --replace" pero sigue saliendo el mismo mensaje que antes.

voy a seguir buscando. graciass a todos por responder!!!!

---


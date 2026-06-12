---
title: "Cambiar del Adept al Synaptic"
date: 2007-02-17
forum: Argentina Team
---

### Post by Darth Trix on 2007-02-17
Estoy usando Kubuntu y el adept pero me recomendaron el synaptic.
¿como hago para que adept no me siga bajando las actualizaciones automáticas y de ahora en mas lo haga el synaptic?

---

### Post by spg76 on 2007-02-17
Para instalar Synaptic hace:

```
sudo apt-get install synaptic
```

Para instalar el Gestor de Actualizaciones de Gnome (que es el que usa Ubuntu) tenes que
poner:

```
sudo apt-get install update-manager
```
y 
```
sudo apt-get install update-notifier
```

Espero que te sirva.

---

### Post by Darth Trix on 2007-02-18
Si me sirve, muchas gracias, pero ¿como hago para desactivar las actualizaciones del Adept?

---

### Post by spg76 on 2007-02-18
> **Darth Trix said:**
> Si me sirve, muchas gracias, pero ¿como hago para desactivar las actualizaciones del Adept?

Creo que tenes que ir a Kcontrol > KDE Components > Service Manager.
Hay están listados los servicios que inician con el sistema. Fijate si está adept-notifier o adept-updater, y desactivalo.
No sé muy bien como tenes que hacer para agregar el notificador de actualizaciones de Gnome (update-notifier) para que inicie automaticamente pero calculo que la opción estará por ahí.
Tené en cuenta que no uso KDE y lo que te digo puede ser inexacto.

---


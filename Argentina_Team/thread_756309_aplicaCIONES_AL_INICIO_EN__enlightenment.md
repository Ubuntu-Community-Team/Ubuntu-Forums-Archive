---
title: "aplicaCIONES AL INICIO EN  enlightenment"
date: 2008-04-15
forum: Argentina Team
---

### Post by andy_91 on 2008-04-15
bueno tengo Xubuntu GG e instale  enlightenment ahora q yo ejecuto xfce4-panel para qpoder usarlos paaneles de xfce  asi los combino con el elegante epanel
ahora como hago que se me guarde al inicio del sistema?

---

### Post by faktorqm on 2008-04-16
Hola, no tengo un linux cerca, pero creo que era algo de etc/rc/rc.local o /etc/rc.local algo asi. Es un archivo que le pones comandos y te los ejecuta cuando arranca el sistema, espero te sirva. salu2!

---

### Post by tzulberti on 2008-04-16
Creo que el se refiere a las aplicaciones que se ejecutan cuando incia E17. La edicion del archivo /etc/rc.d/X (tampco se cual es), es para el incio de la PC. 
Sino me equivoco el se refiere a algo similar a lo que tiene gnome para editar cuando incia el mismo.

---

### Post by oktubrer on 2008-04-16
Algo encontré en 
[http://blogdrake.net/node/6017](http://blogdrake.net/node/6017)

Calculo que estarás usando la versión 17
Según entendí, primero:
```
cd ~/.e/e/applications/all
e_util_eapp_edit xfce4-panel.eap
```

y después 
```
echo "xfce4-panel.eap" >> ~/.e/e/applications/startup/.order
```

Creo que el panel se lanzaba con xfce4-panel, pero por las dudas corroboralo y cambialo en el código.

**[COLOR="Red"]EDITO: hay un comentario en el mismo sitio diciendo que e17 ya no usa .eap sino .desktop, asi que no debe funcionar lo de arriba.[/COLOR]**

---

### Post by andy_91 on 2008-04-16
> **oktubrer said:**
> Algo encontré en 
[http://blogdrake.net/node/6017](http://blogdrake.net/node/6017)

Calculo que estarás usando la versión 17
Según entendí, primero:
```
cd ~/.e/e/applications/all
e_util_eapp_edit xfce4-panel.eap
```

y después 
```
echo "xfce4-panel.eap" >> ~/.e/e/applications/startup/.order
```

Creo que el panel se lanzaba con xfce4-panel, pero por las dudas corroboralo y cambialo en el código.

**[COLOR="Red"]EDITO: hay un comentario en el mismo sitio diciendo que e17 ya no usa .eap sino .desktop, asi que no debe funcionar lo de arriba.[/COLOR]**
no no funciona lo de arriba = grax

---


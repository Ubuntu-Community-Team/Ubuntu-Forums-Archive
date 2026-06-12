---
title: "actualizar desde CD LIVE"
date: 2007-10-18
forum: Argentina Team
---

### Post by josedamico on 2007-10-18
AMIGOS..
no puedo actualizar desde internet de ubuntu 7.04 a 7.10. Está muy lento el servidor y me dice que tardaría como 17 hs.
Mi pregunta es la siguiente: se puede actualizar si bajo el CD live??
qué manera hay ? gracias

---

### Post by sajnox on 2007-10-18
Si podes, para eso tenes que habilitar en Origenes del software al cdrom como una de las fuentes.

Disculpa que no te de mas detalles pero estoy con la maquina del trabajo

Saludos

---

### Post by santiagoward2000 on 2007-10-18
> **josedamico said:**
> AMIGOS..
no puedo actualizar desde internet de ubuntu 7.04 a 7.10. Está muy lento el servidor y me dice que tardaría como 17 hs.
Mi pregunta es la siguiente: se puede actualizar si bajo el CD live??
qué manera hay ? gracias

Si es sólo para actualizar, te conviene usar el AlternateCD.

---

### Post by josedamico on 2007-10-18
bien...estoy bajando el alternate cd....tanto de ubuntu como de kubuntu ambos 7.10. es exactamente lo mismo actualizarlo desde esos cd? Como tengo los dos escritorios (kde= kubuntu y gnome= Ubuntu), deberé actualizar ambos, por separado?? o al poner el cd alternate de ubuntu 7.10 y actualizar desde alli me actualiza tambien el kubuntu?
perdonen las preguntas, quizas algunas son reiterativas, pero no quiero hacer lio. Mi ubuntu anda de maravillas y me jodería muchos hacer algun desastre.gracias

---

### Post by clasificado on 2007-10-18
> deberé actualizar ambos, por separado??

No tengo esa experiencia, pero voto por que eso seguro que no.

Por lo anterior, bajo la pura influencia de mi imaginación, creo que lo que pasará es que, de todo lo que deba actualizar, va a sacar lo que pueda del cd, y lo que no esté lo va a actualizar desde los repositorios.

Lo que no está en los cds depende del uso que le hayas dado a la maquinola. Si instalaste PILA de paquetes, es probable que sea más.

Clasficado

---

### Post by spg76 on 2007-10-18
Para actualizar de Feisty a Gutsy desde un CD, copio (traduzco), y pegó lo que dice en el sitio oficial en [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

> Actualizar desde el CD/DVD alternate 

Usá esta método si el sistema que estás actualizando no está conectado a Internet. 
[LIST=1]
[*]Descargá y graba el CD de instalación alternate. 
[*]Insertalo en tu unidad de CD-ROM. 
[*]Aparecerá un cuadro de diálogo ofreciéndote la posibilidad de actualizar usando ese CD. 
[*]Seguí las instrucciones de la  pantalla.
[/LIST]
Si el cuadro de diálogo por alguna razón no aparece, podés también correr el siguiente comando usando Alt+F2: 
```
gksu "sh /cdrom/cdromupgrade"
```

O en Kubuntu corré el siguiente comando usando Alt+F2: 
```
kdesu "sh /cdrom/cdromupgrade"
```



Espero que sirva.
Saludos.

---

### Post by josedamico on 2007-10-18
si..gracias!!! la pregunta es: ¿¿es lo mismo?? me sirve igual??? es idéntico de lo que bajaría desde un upgrade por internet. Ya bajé el CD porque es IMPOSIBLE hacer el upgrade desde internet porque está atorado. gracias...

---

### Post by spg76 on 2007-10-18
El upgrade desde el CD es esencialmente lo mismo.
La diferencia es que después de actualizar, el sistema buscará otras actualizaciones en internet y te informará si tenés que actualizar algo más.

---

### Post by josedamico on 2007-10-18
ok..pero ¿qué diferencia puede haber entre el cd bajado hoy 18/10 y la actualizacion upgrade de hoy mismo? creo que nada verdad?

---

### Post by josedamico on 2007-10-18
y como actualizo el escritorio KDE para el Kubuntu que tambien tengo instalado como otra sesión?

---

### Post by clasificado on 2007-10-18
> **josedamico said:**
> y como actualizo el escritorio KDE para el Kubuntu que tambien tengo instalado como otra sesión?

Está todo en los mismos repositorios: Actualizas uno y se te actualiza todo (De hecho, vas a tener una cantidad muy por encima del promedio en paquetes)

Clasificado

---

### Post by joseluis on 2007-10-18
ok o sea que puedo actualizar tanto desde kubuntu como de ubuntu que la cosa siempre da el mismo resultado para ambos_?

---


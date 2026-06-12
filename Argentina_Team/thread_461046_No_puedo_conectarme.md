---
title: "No puedo conectarme"
date: 2007-06-01
forum: Argentina Team
---

### Post by Apipote on 2007-06-01
Hola a todos, soy un usuario avanzado de win xp que quiere venir a ubuntu. He bajado e instalado como live cd la ultima version. Es una maravilla como detecto mi hardware x64. Sin embargo no puedo conectarme a internet, pues tengo una conexion rara.

En xp es una lan ( un acces point conectado a una antena como cliente de una antena isp lejos de casa ) y sobre esa una pppoe "pero sin usar modem", solo tengo un username and password que en xp se setea facilmente, pero ubuntu no me da esa opcion, me pide nro de telefono que no tengo.
Ayuda por favor, pues me quiero ir de windows, y es lo unico que me falta.
Saludos y gracias.

---

### Post by Psicolonia on 2007-06-01
intenta marcar qualquer numero

---

### Post by Apipote on 2007-06-01
No, Psicolonia..............nada. Que frustrante !!
Alguna otra sugerencia?

---

### Post by fetova on 2007-06-01
Podrias especificar como te conectas en XP?
Puede dar la pauta de como hacerlo aca

Saludos :)

---

### Post by Apipote on 2007-06-01
Como no, perdon si no fui claro.

Tengo dos conexiones en "network conexions" de xp x64

La lan, que es mi placa de red conectada a un router, que por medio de una antena se conecta a otra antena ( lejos ) del proveedor. Ubuntu la toma perfectamente y operacional.

La Broadband ( wan miniport pppoe ) que simplemente me pide un username and password cuando la ejecuto, desde un acceso directo en mi escritorio. Facilmente se crea en xp.
Acá está  mi problema, pues no tengo la opcion de crearla en Ubuntu, y solo estan mi placa de red ( que anda bien ) y luego la opcion de setear un modem que yo no tengo ni uso, y me pide nros de telefono para funcionar.

Ojala me explique bien.

---

### Post by fetova on 2007-06-01
Probaste:

```
sudo pppoeconf
```?

---

### Post by Apipote on 2007-06-01
Si he probado ese comando en la consola y me da error algo como que "no encuentra el concentrador de pppoe" o que esta ocupado por otro modem. 
Me parece que estoy jodido.

---

### Post by fetova on 2007-06-01
> **Apipote said:**
> Si he probado ese comando en la consola y me da error algo como que "no encuentra el concentrador de pppoe" o que esta ocupado por otro modem. 
Me parece que estoy ******.

tu tranquilo, debe de haber una manera, busca aca primero: [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE), y despues aca si no das [http://ubuntu-ar.org/node/13](http://ubuntu-ar.org/node/13), ahi hay una serie de tips donde buscar informacion, puedes buscar con ayuda de ese como mientras alguien sabe algo :)

---

### Post by Apipote on 2007-06-01
Evidentemente hay un bug en Ubuntu. Ahora estoy conectado con XUbuntu y no tengo ningun problema. He hecho identicos pasos que con Ubuntu y vuela, realmente no entiendo nada.
Pero me gusta Ubuntu.
Alguna sugerencia

---

### Post by beuno on 2007-06-01
Es muy posible que el "network-manager" te este creando problemas.
Te recomendaria desinstalarlo, probar todo de vuelta.

---

### Post by Apipote on 2007-06-03
Estoy en xubuntu, que aparentemente no tiene ese bug ( pero si el de las particiones que me volvio loco hasta que encontre la solucion aca ), sin embargo me gustaria conservar las settings del pppoeconf que se pierden al reiniciar, y es muy molesto tener que repetir todo el proceso de pppoeconf.
Alguna sugerencia?
Gracias.

---

### Post by Al_maverick on 2007-06-03
> **Apipote said:**
> Estoy en xubuntu, que aparentemente no tiene ese bug ( pero si el de las particiones que me volvio loco hasta que encontre la solucion aca ), sin embargo me gustaria conservar las settings del pppoeconf que se pierden al reiniciar, y es muy molesto tener que repetir todo el proceso de pppoeconf.
Alguna sugerencia?
Gracias.

el pppoeconf debe guardar un archivo de configuracion. Lo que podes hacer es copiarlo y probarlo en ubuntu. La otra opcion, y creo q la mas simple es que instales el gnome directamente desde xubuntu.

para eso podes ir a la terminal y poner: sudo apt-get install ubuntu-desktop

Con eso te instala los paquetes necesarios para correr gnome y vas a poder elegirlo al iniciar.

---

### Post by Apipote on 2007-06-06
Buena idea, pero me molesta que en xubuntu pueda conectarme a internet y no en ubuntu, uso amd 64 bits, y la verdad no quiero 2 escritorios.

---

### Post by Al_maverick on 2007-06-08
Si, la verdad que es molesto. Lo que podes hacer es probar si instalando el gnome, la conexion te funciona. Si es asi, luego puedes desinstalar el escritorio que no uses. Una de las ventajas de como funciona el X es que puedes tener el escritorio q elijas sin tener que reinstalar todo.

---

### Post by Apipote on 2007-06-10
Mira Maverick por lo que he leido es un bug. Ojala se corrija con Gusty por ahora seguiremos con Xubuntu.
Saludos y gracias

---

### Post by Apipote on 2007-06-11
Maverick
Pensaba en tu buena idea y me pregunto, si instalo gnome, en xubuntu.
Como saco xfce?
me quedan mis aplicaciones y settings previas?
me queda limpio el sistema y booteando bien?
Gracias.

---

### Post by Al_maverick on 2007-06-11
> **Apipote said:**
> Maverick
Pensaba en tu buena idea y me pregunto, si instalo gnome, en xubuntu.
Como saco xfce?
me quedan mis aplicaciones y settings previas?
me queda limpio el sistema y booteando bien?
Gracias.

Las aplicaciones te quedan igual porque ya las tenes instaladas. Lo que podes hacer es desinstalar solo la parte del escritorio. No deberias tener problema con eso. En este mismo foro puedes ver ejemplos de gente que cambio de gnome a kubuntu, y a xfce sin problemas. El core de todos los *ubuntu es el mismo, los escritorios se pueden intercambiar sin problemas.

---

### Post by Apipote on 2007-06-11
bueno veamos y te cuento.
gracias

---


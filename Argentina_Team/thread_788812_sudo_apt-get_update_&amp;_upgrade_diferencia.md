---
title: "sudo apt-get update &amp; upgrade: diferencia?"
date: 2008-05-10
forum: Argentina Team
---

### Post by smrdelj on 2008-05-10
Hola que tal. Bueno, mi duda es basicamente eso: cuál es la diferencia entre sudo apt-get update y upgrade? Yo hago ambos, pero me da la impresión de q el update solo chequea repos y el upgrade ejecuta la actualizacion efectiva del sistema. Puede ser?

Saludos

---

### Post by santiagoward2000 on 2008-05-10
> **smrdelj said:**
> Hola que tal. Bueno, mi duda es basicamente eso: cuál es la diferencia entre sudo apt-get update y upgrade? Yo hago ambos, pero me da la impresión de q el update solo chequea repos y el upgrade ejecuta la actualizacion efectiva del sistema. Puede ser?

Saludos

Hola
Si, es justo eso. Primero se usa el update para ver si hay algo nuevo en los repositorios y después el upgrade para instalarlo.
Si ponés:
```
apt-get -h
```
te da una lista con las opciones que podés usar con apt-get y una explicación de qué hacen.
Saludos

---

### Post by smrdelj on 2008-05-10
Barbaro muchas gracias!

---

### Post by santiagoward2000 on 2008-05-10
> **smrdelj said:**
> Barbaro muchas gracias!

De nada!

---

### Post by pol666 on 2008-05-10
yo tengo otra duda cual es 
la diferencia entre apt-get y aptitude

---

### Post by Hei Ku on 2008-05-10
aptitude es solo un front-end para apt-get, o sea, usa las funciones de apt-get, solo presenta una interfaz un poco mas amigable.
es el mismo caso de apt-get y dpkg. apt-get se encarga de mantener los indices y repositorios, bajar los archivos, etc, pero la instalacion la hace a traves de dpkg, que es el que se encarga de instalar, desinstalar, controlar dependencias, etc.
Es el mantra de linux/unix, herramientas chicas, especializadas, que puedan integrarse con otras para hacer cosas complejas. Lo ves en un monton de casos en todo linux.

---

### Post by pol666 on 2008-05-10
> **Hei Ku said:**
> aptitude es solo un front-end para apt-get, o sea, usa las funciones de apt-get, solo presenta una interfaz un poco mas amigable.
es el mismo caso de apt-get y dpkg. apt-get se encarga de mantener los indices y repositorios, bajar los archivos, etc, pero la instalacion la hace a traves de dpkg, que es el que se encarga de instalar, desinstalar, controlar dependencias, etc.
Es el mantra de linux/unix, herramientas chicas, especializadas, que puedan integrarse con otras para hacer cosas complejas. Lo ves en un monton de casos en todo linux.

No te entendi nada  pero no hagas problema, que que es casi lo mismo. xD

---

### Post by Hei Ku on 2008-05-11
aptitude es solo una pantalla para hacer mas facil el apt-get. o sea que usar uno u otro es igual.

---

### Post by faktorqm on 2008-05-11
Mira vos lo que me vengo a enterar, yo pense que era exactamente al reves, que el apt-get era el front end de aptitude. Ahora que lo decis tiene mucho sentido. En realidad creo que creia eso por que en debian hay aptitude, y nunca probe de poner apt-get. Igual ojo! el aptitude te instala los paquetes recomendados por defecto y el apt-get no, se los tenes que especificar a manopla. Salu2!

---

### Post by tzulberti on 2008-05-11
> **faktorqm said:**
> Mira vos lo que me vengo a enterar, yo pense que era exactamente al reves, que el apt-get era el front end de aptitude. Ahora que lo decis tiene mucho sentido. En realidad creo que creia eso por que en debian hay aptitude, y nunca probe de poner apt-get. Igual ojo! el aptitude te instala los paquetes recomendados por defecto y el apt-get no, se los tenes que especificar a manopla. Salu2!

Otras de las diferencias es que con el aptitude cuando removes un paquetes, te remueve todas las dependencias del mismo que no son necesarias.

---

### Post by smrdelj on 2008-05-11
Y en conclusion qué es mejor usar?

Dan lo mismo? O depende de qué es lo q vayas a hacer?

---

### Post by faktorqm on 2008-05-12
Hola, eso lo aclaro en este post: [http://ubuntuforums.org/showthread.php?t=773722](http://ubuntuforums.org/showthread.php?t=773722) (nadie lo leyo? :()

---


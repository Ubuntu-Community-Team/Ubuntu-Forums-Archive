---
title: "Ubuntu 9,04, windows xp y seven"
date: 2009-09-03
forum: Bolivia Team
---

### Post by perendengue on 2009-09-03
Hola, soy nuevo en este foro y quería hacer la siguiente pregunta, si es que alguien podría darme una mano.

Tengo instalado windows xp en una netbook acer, la cual tiene una particion de rescate oculta, el disco duro es de 160 gb, el cual he particionado en 4 unidades, tres con formato y una no.

he instalado ubuntu desde una pendrive en la particion sin formato, ahora quiero instalar windows 7, pero no se como hacerlo, supongo que al instalarlo no me dejará levantar desde ubuntu.

mi pregunta es si se puede hacer esto de la forma que lo estoy planteando o tengo que instalar alguna jerarquía en cuanto a los sist op?. y de ser así como lo haria?

aaa me olvidaba , todo esto sin perder mi partición de rescate ni su tecla caliente alt+10

gracias de antemano.

---

### Post by mariocesar on 2009-09-04
Dificil, Dificil, Dificil ...

Windows Vista y las particiones ocultas de recuperación son drámaticas de hacerlas funcionar juntas, hasta el momento nunca ha sido igual en ninguna laptop con esas caracteristicas donde he instalado Ubuntu y Windows.

Lo que te aconsejo es.

1. Desiste de tu idea de mantener la partición de recupueración y formatea todo, Instalar primero Windows 7 y luego Ubuntu. Despues de todo, en muchos contratos pierdes la garantia de tu laptop al instalar otro sistema operativo. Y para muchas empresas de soporte la idea de garantia es formatear todo e instalarte un windows pirata asi que seria lo mismo.

2. Encuentra a gente de la comunidad en tu ciudad, y dedicale varios dias a estudiar como hacerlo sin problemas, actualizando y que siga funcionando la partición de rescate.

Disculpame si te desanime :D Pero enserio te recomiendo que hagas esto con amigos con gente que tengas a tu lado y a la que puedas gritar si le pasa algo a tu laptop :Djajajaja no es por que sea Ubuntu DIFICIL, si no por que tener dos sistemas operativos, y uno de ellos es muy EGOISTA es algo dificil.

Busca gente! si estas en santa cruz avisas para que organizemos de paso un junte, un install fest chiquito.

---

### Post by perendengue on 2009-09-05
Ok, gracias por tu respuesta, de todos modos seguiré intentando.
Ya he instalado ubuntu como te decia como segundo sist op en base de xp.
Luego instalé seven y al hacer esto , perdí ubuntu, claro que no seguí intentando, porque taba interesado mas en probar seven.
Al final tuve problemas con xp y traté de recuperarlo y no me funcionó la particion de rescate, asi que usé el acronis true image y pude restaurar con tecla caliente al reemplazar algunos archivos que pedía el original boot.ini de xp.
 
Sé que se puede, pero no se como hacerlo, y ahora está mas dificil ya que cambié mi netbook por una laptop mas grande, pero conseguiré otra y lo probaré, informaré si tengo alguna novedad.
 
No lo intento en mi nueva notbook porque no trae sistema operativo de rescate , ni windows, aparte que la estoy usando para trabajar.
 
Gracias por tu ayuda y ojala lleguemos a una solución.

---

### Post by Braik on 2010-04-23
Hola,
 
Bueno la situacion es la siguiente, en principio es posible lanzar todos los sistemas que quieres.
 
Cuando instalas Ubuntu el sistema te pone en tu particion Boot un programa que se llama GRUB que te permite decidir que sistema quieres lanzar. Windows, ya sea XP o 7 hacen lo mismo con un programa que se llama boot loader (si no me equivoco) que esta basado en un fichero boot.ini.
 
Evidentemente todo va a depender qe que sistema quieres que se ocupe de este detalle, pero en todos los casos, como no se quieren mucho vas a tener que urguetear los ficheros.
 
Si entiendes ingles, te aconsejo que vayas a los forums que se ocupan de eso. De todas maneras vas a tener que saber en que particion esta que y como se llama cada particion para cada sistema.
 
Si no puedes dime, voy a tratar de tener tiempo y te ayudo un poco.
 
Suerte

---


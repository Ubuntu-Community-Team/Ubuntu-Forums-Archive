---
title: "esto que hace?"
date: 2007-03-29
forum: Argentina Team
---

### Post by MeduZa on 2007-03-29
hola, me pasaron un archivo .rar (un windowuser q no sabe q las extenciones en linux no exiten) y me dice q eso es un virus
lo abro y es un texto de script (no tiene permisos de ejecucion) y tiene esto:

> #!/bin/bash
export DEV=`/bin/mount |grep 'on / type' |awk -F[0-9] '{print $1}'`
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX



obvio q si le pongo permisos y lo abro haria algo pero no entiendo que!
alguien que sepa mas de script q me ilumnine please?


EDIT: edite parte del scritp debido a q recibi una respuesta q me aclaro la duda y ya no es necesario mostrarlo por razones de seguridad (baja pero bueno algun nabo suelto siempre hay)

---

### Post by Rui Pais on 2007-03-29
"solamente" te apaga la MBR de lo disco duro... 
no es un virus pero es letal si lo corres.

podes hacer
```
 sudo /bin/mount |grep 'on / type' |awk -F[0-9] '{print $1}'
```
deve dicer:
/dev/hda o /dev/sda

Pero !!ATENCIÓN!! la mala parte es la que usa la instrucción **dd** e que graba ziero en lo primiero sector de tu disco :(
No lo executes!!!

---

### Post by MeduZa on 2007-03-29
> **Rui Pais said:**
> "solamente" te apaga la MBR de lo disco duro... 
no es un virus pero es letal si lo corres.

podes hacer
```
 sudo /bin/mount |grep 'on / type' |awk -F[0-9] '{print $1}'
```
deve dicer:
/dev/hda o /dev/sda

la mala parte es:
```
/XXXXXXXXXXXXXXXXXX1
```
graba ziero en lo primiero sector de tu disco :(

guau, ahora el que ejecute un rar en root de un archivo .rar que no lo es (ese tipo de cosas son para windows) tiene que ser muy pero muy :-k  no me sale la palabra :lolflag: 

gracias por la aclaracion

---

### Post by Rui Pais on 2007-03-29
> **MeduZa said:**
> guau, ahora el que ejecute un rar en root de un archivo .rar que no lo es (ese tipo de cosas son para windows) tiene que ser muy pero muy :-k  no me sale la palabra :lolflag: 

gracias por la aclaracion

:lol:

have fun

---

### Post by marianom on 2007-03-29
Gracias a ambos por su aporte, es bueno saber que estas cosas están dando vueltas y hay que tener cuidado.

Ahora bien ...

Visto y considerando que MeduZa ha obtenido la respuesta para su pregunta, me gustaría si pueden editar un poco vuestros posts de forma tal de hacer inutilizable el código. 
No me gustaría que alguien gracioso lo encuentra con un buscador. No avivemos giles.

Visto e considerando que MeduZa obteve a resposta para sua pergunta, me agradaria se podem editar um pouco vossos posts de forma tal de fazer inutilizável o código. Não me agradaria que alguém engraçado o encontra com um procurador.

---

### Post by Rui Pais on 2007-03-29
> **marianom said:**
> Gracias a ambos por su aporte, es bueno saber que estas cosas están dando vueltas y hay que tener cuidado.

Ahora bien ...

Visto y considerando que MeduZa ha obtenido la respuesta para su pregunta, me gustaría si pueden editar un poco vuestros posts de forma tal de hacer inutilizable el código. 
No me gustaría que alguien gracioso lo encuentra con un buscador. No avivemos giles.

Visto e considerando que MeduZa obteve a resposta para sua pergunta, me agradaria se podem editar um pouco vossos posts de forma tal de fazer inutilizável o código. Não me agradaria que alguém engraçado o encontra com um procurador.

Cierto. Hay cambiado mi post.
Gracias.

---

### Post by MeduZa on 2007-03-29
> **marianom said:**
> Gracias a ambos por su aporte, es bueno saber que estas cosas están dando vueltas y hay que tener cuidado.

Ahora bien ...

Visto y considerando que MeduZa ha obtenido la respuesta para su pregunta, me gustaría si pueden editar un poco vuestros posts de forma tal de hacer inutilizable el código. 
No me gustaría que alguien gracioso lo encuentra con un buscador. No avivemos giles.

Visto e considerando que MeduZa obteve a resposta para sua pergunta, me agradaria se podem editar um pouco vossos posts de forma tal de fazer inutilizável o código. Não me agradaria que alguém engraçado o encontra com um procurador.

listo yo tambien

gracias

---

### Post by marianom on 2007-03-29
Gracias muchachos.

---


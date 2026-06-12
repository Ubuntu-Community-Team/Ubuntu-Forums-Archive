---
title: "A ver una dificil !"
date: 2006-12-11
forum: Argentina Team
---

### Post by jpmorelli on 2006-12-11
Alguien encontrò la manera de crear una carpeta compartida para todos los usuarios asignados a un equipo.
No vale la de ponerle atributos 777 a la carpeta ya que igualmente quien cree el archivo lo deja como propietario y ningun otro usuario lo puede modificar.
Es para hacer una especie de carpeta comun donde todo usuario pueda escribir grabar y modificar las cosas que otro hace.
A ver si a alguien se le ocurriò o lo encontrò ?

---

### Post by scrooge_74 on 2006-12-11
ponerle atributos de rw para el grupo y otros no funciona? Siempre vas a tener un dueño, pero otros pueden modificarlo o ejecutarlo

---

### Post by Hex_Mandos on 2006-12-12
No funca chmoddearlo a 777? Hubiera apostado a eso (no por mi vástisima experiencia en Linux, que es de una semanita, es que lo uso en mis sitios de internet para instalar algunos scripts... en un server LAMP)

---

### Post by beuno on 2006-12-12
Si comparten el mismo grupo en rw, tienen que tener acceso todos.
Yo lo tengo funcionando asi.

---

### Post by jpmorelli on 2006-12-12
ah si, supongo que si, si comparten el mismo grupo, pero el tema es , puede ser alguien del mismo grupo sin estar con derechos sudo ? 
Hasta yo me maree ya con mi propia pregunta. ](*,)

---

### Post by beuno on 2006-12-12
> **jmorelli said:**
> ah si, supongo que si, si comparten el mismo grupo, pero el tema es , puede ser alguien del mismo grupo sin estar con derechos sudo ? 
Hasta yo me maree ya con mi propia pregunta. ](*,)

Mientras esten en el mismo grupo, con todos los archivos en 775 todo bien.
Yo lo tengo seteado asi con samba y funciona hace años.

---

### Post by jpmorelli on 2006-12-12
Gracias !

---


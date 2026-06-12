---
title: "Acceso a File Server Windows 2008"
date: 2014-05-08
forum: Argentina Team
---

### Post by roberto-0 on 2014-05-08
Estimados, trabajo para una escuela y estoy intentando migrar a Ubuntu las PCs de alumnos y profes, pero como siempre y en todo pasa, tengo trabas que les paso a comentar:

1 y fundamental. Tengo un server 2008 (el cual seria el ultimo en pasar ya que es de mucho uso), el cual todas las pcs se conectan a el como un File Server, cada división y profe tiene su usuario y pass para acceder a determinadas carpetas.
no encuentro la forma de que al acceder al mismo desde ubuntu me pida ahí el user y pass, ya que si mapeo las carpetas con el fbstat, tendrian acceso todos a todas las carpetas, otra seria crear un el usuario en ubuntu y con esa pass, pero son muchisimos los usuarios, tambien se me ocurrio el que se podria crear un script y levantarlo con cron, pero ya no se como se podria hacer eso.

2 existe algun tipo de deepfreeze para ubuntu o algo similar? 


Gracias desde ya!!!

---

### Post by aromo2 on 2014-05-08
Pienso que tu mejor opcion en este escenario seria configurar Samba Client en las PCs para que puedan accesar las carpetas compartidas en Windows.
 
Para hacer las cosas mas faciles para los usuarios (un poquito mas complicadas para vos), tambien podrias configurar el control de accesso a las PCs a traves de LDAP apuntando al controlador de dominio (asumiendo que usas Active Directory en la escuela).

Suerte en tu proyecto...

---

### Post by roberto-0 on 2014-05-09
> **aromo2 said:**
> Pienso que tu mejor opcion en este escenario seria configurar Samba Client en las PCs para que puedan accesar las carpetas compartidas en Windows.
 
Para hacer las cosas mas faciles para los usuarios (un poquito mas complicadas para vos), tambien podrias configurar el control de accesso a las PCs a traves de LDAP apuntando al controlador de dominio (asumiendo que usas Active Directory en la escuela).

Suerte en tu proyecto...

Gracias aromo2 por responder, el tema de samba client es que yo necesito que al hacer click en ese servidor, le pida que pongan el user y pass.
No tengo active directory.

Se me estan quemando los libros!!!

---


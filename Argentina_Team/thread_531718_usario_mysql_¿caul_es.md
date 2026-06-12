---
title: "usario mysql ¿caul es?"
date: 2007-08-21
forum: Argentina Team
---

### Post by aceki on 2007-08-21
Gente me estoy volviendo loco, estoy configurando sugar, y me pide el usuario de mysql, probe con con mi usario, con root, y nda, me dice que es incorrecto, alguien me dice como doy uno usuario a mysql con todos los permisos, desde ya muchas gracias.

---

### Post by facundocorradini on 2007-08-22
pues solo vos sabes cual es... se supone que vos hayas creado el usuario de mysql...

Probá con los default:   usr "root" pass "" (osea, vacío) 

(BTW: instalaste un ubuntu server o estás tratando de hacer andar todo esto en un desktop?)

---

### Post by tzulberti on 2007-08-22
Los user de linux no tienen que ver con los de mysql... El user por default de mysql es
user: root, sin password....

Para create un user, logueate como root, y despues corre:
CREATE USER user [IDENTIFIED BY [PASSWORD] 'password']
    [, user [IDENTIFIED BY [PASSWORD] 'password']] ...

La sentencia CREATE USER crea nuevas cuentas MySQL. Para usarla se debe tener el privilegio GRANT OPTION para la base de datos mysql. Para cada cuenta, CREATE USER crea un nuevo registro en la tabla mysql.user sin privilegios. Se produce un error si la cuenta ya existe. Se le puede dar una contraseña a la cuenta con la cláusula opcional IDENTIFIED. Los valores user y password se dan del mismo modo que para la sentencia GRANT.

La sentencia CREATE USER se añadió en MySQL 5.0.2.

sacado de: [http://mysql.conclase.net/curso/index.php?sen=CREATE_USER](http://mysql.conclase.net/curso/index.php?sen=CREATE_USER)

---

### Post by aceki on 2007-08-22
gracias a todos, si era el root sin pass, bastante obvio, muchas gracias nuevamente!!

---


---
title: "Curso entrenamiento de Ubuntu para descargar"
date: 2007-12-20
forum: Argentina Team
---

### Post by marianom on 2007-12-20
El sabdfl acaba de publicar [esta entrada]("http://www.markshuttleworth.com/archives/134") en su blog y me pareció interesante compartirla. Ciertamente más de 700 megas de información para entrenar gente en el uso de Ubuntu es algo digno de verse y compartir.
Atención: para descargar el material tal cual se anuncia necesitas cuenta de launchpad, bzr 1.0 instalado y una llave ssh subida al server.

---

### Post by sharkg on 2007-12-20
mmm me estas hablando en chino ya!!! jejejeje
no hay otra forma de bajarlo???? :S

---

### Post by User21 on 2007-12-20
Quien se anima a descargarlo y ponerlo en algun server, para el publico en general ? De todas formas, debe estar en INGLES! 

Alguien ? ¬_¬

Nota al pie: Despues de leer la biografia de Marky, siento que lo amo... JAJAJA xD

---

### Post by Pajblito on 2007-12-20
si pa enero me terminan de instalar internet en casa lo subo a mi server pa empezar la traduccion :)

---

### Post by tech9 on 2007-12-20
> **marianom said:**
> El sabdfl acaba de publicar [esta entrada]("http://www.markshuttleworth.com/archives/134") en su blog y me pareció interesante compartirla. Ciertamente más de 700 megas de información para entrenar gente en el uso de Ubuntu es algo digno de verse y compartir.
Atención: para descargar el material tal cual se anuncia necesitas cuenta de launchpad, bzr 1.0 instalado y una llave ssh subida al server.

da las gracias para compartir

---

### Post by faktorqm on 2007-12-21
uhhh son re limados los tipos.... seguro hacen eso para ke no vayan 5000 chabones a bajar al mismo tiempo ¬¬

ahora veo como lo hago, y lo cuelgo de rapidshare, o similar. salu2!

---

### Post by User21 on 2007-12-21
**Muchisimas gracias**. Estaremos esperando noticias tuyas! :) 

Al fin un valiente! xD

---

### Post by faktorqm on 2007-12-21
un bardo la verdad todo esto. 

les digo lo que hice: me olvide la clave de launchpad, asi que tuve que sacar una nueva. ¬¬ a mi mismo.
luego ```
sudo aptitude install bzr ssh
```
luego ```
ssh-keygen -t rsa
```
luego ```
cat /home/faktorqm/.ssh/id_rsa.pub
``` (en mi caso obviamente, sustituir faktorqm por el nombre de usuario de cada uno)
Despues lo puse en launchpad y subi la clave ssh. (es la salida del ultimo comando :D)
No contento con todo esto, que obviamente no lo sabia, sino que tuve ke investigar en google, estaba mal el link me parece en el blog ese. termine haciendo esto
 ```
bzr branch http://bazaar.launchpad.net/~billy-cina/ubuntu-desktop-course/ubuntu-desktop-course
``` 
(que lo sake de la pagina de launchpad del autor) y dice "Fetch phase 1/4" :P:P y avanza lento, asi ke supongo que algo esta bajando. a donde me lo va a poner no lo se, pero bue.......

ni bien termine, va a proceso de subida :D salu2!!!!!!!

---


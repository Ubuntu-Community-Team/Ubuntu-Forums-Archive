---
title: "[SOLVED] Sopcast + Totem player o el que sea"
date: 2008-02-02
forum: Argentina Team
---

### Post by alfredo_cba on 2008-02-02
Recientemente instalé sopcast, se instaló correctamente, se conecta perfectamente a los canales pero no me habre ningun player, La configuración es la siguiente, "totem -ontop -geometry 100%:100%" si alguién me da una mano, estaré agradecido. 
salu2

---

### Post by juanman on 2008-02-03
A ver si entiendo... instalaste el sopcast q corre en consola o alguno con entorno grafico? Yo uso el de consola y un script para simplificarme un poco la cosa (en los comentarios de este post esta el script: [http://linuxandcomputerscience.blogspot.com/2007/10/cmo-ver-todos-los-partidos-de-ftbol.html]("http://linuxandcomputerscience.blogspot.com/2007/10/cmo-ver-todos-los-partidos-de-ftbol.html"))

Para abrir el player y ver la tv, hay q escribir:
nombreplayer [http://localhost:numpuerto](http://localhost:numpuerto)

Donde nombreplayer es el nombre del binario del reproductor (vlc o wxvlc, mplayer, kaffeine, supongo q totem sera igual pero no lo probe)
Y numpuerto es el puerto en el q se escucha

Pregunta cualquier cosa...
Salu2

---

### Post by alfredo_cba on 2008-02-03
instalé uno que tiene entorno grafico, en la solapa " config" te da la opcion para elegir player, en mi caso como tenia solo instalado Totem decia "totem -ontop -geometry 100%:100%", probé también con el VLC y nada, pero en un último intento instalé el mplayer y anduvo. :D

asi que gracias por la ayuda, tema solucionado 

mplayer -ontop -geometry 100%:100% -fs

---

### Post by User21 on 2008-02-04
**Marche un SOLVED???**

Hoy la tengo con los solveds, lo se! :P
Pero me encanta que se resuelvan los problemas, y que conste que funcionan las cosas por aqui :P

---


---
title: "[SOLVED] Mal Sonido"
date: 2008-03-21
forum: Argentina Team
---

### Post by MaReaDo^ on 2008-03-21
estoy teniendo un problema de sonido escuchando musica
probe con totem, rythymbox y xmms
probe con alsa y oss
probe con los gstreamer codecs y los xine codecs
se me escucha medio saturado y con ruido los mp3
aca en el foro recomendaban tocar eso del oss y alsa, y algo de eds y probe todo y ni idea
o decian de cambiar de reproductor
yo probe todo y no se que onda
no se si tendre que bajar otros codecs o tengo todo mal configurado :S

---

### Post by Apokalyptica79 on 2008-03-21
Hola, decinos que placa de sonido tenés y que versión de ubuntu tenés.
Como no nos dijiste nada de eso te dejo esto que encontré:
[http://www.lugmen.org.ar/pipermail/lug-novatos/2005-August/005270.html]("http://www.lugmen.org.ar/pipermail/lug-novatos/2005-August/005270.html")
Saludos

---

### Post by pol666 on 2008-03-21
el sonido lo regulan 3 archivos 

asound.conf
asounrc
esd.conf (no se si es asi)

Bueno tenes que copiar una configuracion apropiada de alguien q tenga la misma placa de sonido y la misma configuracion de parlantes
por ejemplo

Sound Baster Audigy - sonido 5.1

---

### Post by MaReaDo^ on 2008-03-21
tengo una intel high definition audio, algo asi (viene con la placa madre intel D945Gnt)
tengo ubuntu 7.0
uso dos parlantes nomas
el ruido y la saturacion es sobre todo con las graves

edit:probe lo que decia el link de Apokalyptica79 y sigue pasando lo mismo
voy a probar buscar esos archivos para mi placa

edit: me confundi, tengo una Realtek Hign Definition, en la tapa del mother dice intel HDA, pero en los drivers de windows sale Realtek HDA

---

### Post by MaReaDo^ on 2008-03-21
baje de la pagina de intel los ultimos drivers de la palca intel para debian y baje de la pagina de realteak los ultimos para linux y segui una guia para instalarlos
volvi yt habia otro tipo d ruido, si n oreproducia nada y subia el volumen de los parlantes al palo se escuchaba fuertazo, mutie todos los canales porque tengo dos parlantes nomasy se soluciono
no hace ese ruido que hacia despues del a instalacion de los drivers nuevos, ni satura como antes con estos :)

---

### Post by Apokalyptica79 on 2008-03-22
Hola, al final tu problema se solucionó?
Si es así ponelo en el topic asi se evitan más comentarios al respecto y por si alguien tiene el mismo problema o uno parecido que vea que se solucionó.
Saludos.

---


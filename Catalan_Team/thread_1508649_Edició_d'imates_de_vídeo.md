---
title: "Edició d'imates de vídeo"
date: 2010-06-13
forum: Catalan Team
---

### Post by ladisse on 2010-06-13
Algú em pot donar un cop de mà per saber com ho haig de fer per girar les imatges de vídeo? Gràcies a tots per la vostra ajuda.

---

### Post by epileg on 2010-06-13
amb avidemux ho pot fer fàcilment

Salut.

---

### Post by wgarcia on 2010-06-13
Des de la línia de comandes es pot fer molt fàcilment amb el programa "mencoder". Per exemple per girar un vídeo "ogv" la comanda a donar seria:

mencoder sense_rotar.ogv -oac mp3lame -ovc lavc -vf scale -zoom -vf rotate=1 -o video_rotat.ogv

on sense_rotar.ogv és el teu vídeo sense rotar i suposant  que té audio mp3.

Si busques a Internet amb les paraules clau "mencodar rotate avi" etc., podras trobar diversos exemples de com rotar vídeos en altres formats.

---

### Post by ladisse on 2010-06-16
Prenc nota. Moltes gràcies a tots, altra vegada.

---


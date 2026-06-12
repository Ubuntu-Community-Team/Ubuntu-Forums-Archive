---
title: "Videoconferència en Ubuntu"
date: 2010-10-13
forum: Catalan Team
---

### Post by pelai21 on 2010-10-13
Hola a tots i a totes!

Utilitzo ubuntu des de fa un any i mig. Mica a mica he anat resolent els entrebancs que m'he anat trobant i darrerament només utilitzo entorns lliures, cosa que em satisfà moltíssim. Fins i tot m'he convertit en propagandista, i ja he aconseguit engrescar uns quants coneguts ;-)

Tanmateix encara no he aconseguit realitzar mai una bona videoconferència amb ubuntu. La majoria de problemes se'm presenten quan intento parlar amb un usuari de güindous. Fins ara he provat dues solucions, totes dues insatisfactòries:

[LIST]
[*]En Skype la imatge és dolenta i la conversa es talla sovint.
[*]En Gtalk em falla constantment el so.
[/LIST]
Quins serveis utilitzeu vosaltres? Us trobeu amb els mateixos problemes? Jo utilitzo karmic koala.

---

### Post by Albert Que on 2010-10-13
Has provat l'Ekiga? [http://ekiga.org/](http://ekiga.org/)
tot i que si se't talla el so segurament és problema d'ample de banda.

---

### Post by wgarcia on 2010-10-14
Prova iniciar skype des d'una terminal (Aplicacions -> Accessoris -> Terminal) entrant el següent:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

i prement intro.

Si veus que el vídeo ara et funciona millor es pot suggerir una solució més permanent perquè no hagis d'entrar aquesta parrafada cada cop que vols iniciar skype.

---

### Post by pelai21 on 2010-10-14
Mmm... no sabia que l'Ekiga també tingués una versió per a güindous. Ho provaré, a veure què tal, i ja us diré alguna cosa. Gràcies!

---


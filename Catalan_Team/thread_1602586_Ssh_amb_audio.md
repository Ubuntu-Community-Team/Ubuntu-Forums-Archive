---
title: "Ssh amb audio?"
date: 2010-10-21
forum: Catalan Team
---

### Post by tanreb20 on 2010-10-21
Bones!

L'altre dia vaig descobrir que fent

```
ssh -X IP
``` aconseguies portar les aplicacions grtáfiques del servidor al client.

M'agradaria saber si hi ha alguna manera de portar també l'audio. Per pode veur ela tv per exemple? Grácies!

---

### Post by kukat on 2010-10-21
amb

ssh -X IP mplayer "arxiu.ogg" escoltes l'arxiu mitjançant "mplayer". 

No se quin programari utilitzes per a veure la tele, però pots provar a:

ssh -X IP programari_tv

---


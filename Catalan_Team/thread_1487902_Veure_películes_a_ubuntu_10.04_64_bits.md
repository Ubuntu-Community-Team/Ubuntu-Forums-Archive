---
title: "Veure películes a ubuntu 10.04 64 bits"
date: 2010-05-19
forum: Catalan Team
---

### Post by lluisbages on 2010-05-19
tinc instal·lat l'Ubuntu 10.04 64 bits i no puc veure pel·l&#314;cules amb cap reproductor.
Algú em pot ajudar?

Lluís

---

### Post by lluisanunez on 2010-05-19
Has insta&#320;lat ubuntu-restricted-extras? Això et posarà tots els codecs que necessites a tots els reproductors

---

### Post by pelai21 on 2010-05-22
Afegeix repositoris medibuntu:

> sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

Instal·la codecs restrictius:

> sudo apt-get install libdvdcss2 non-free-codecs

I si dius que tens 64 bits:

> sudo apt-get install w64codecs

---


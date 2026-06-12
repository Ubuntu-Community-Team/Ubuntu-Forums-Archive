---
title: "Controladors Nvidia per la Pangolina Precisa (solució)"
date: 2012-05-13
forum: Catalan Team
---

### Post by lluisanunez on 2012-05-13
Bones,
Si heu actualitzat a la 12.04 i teniu una tarja gràfica Nvidia, segurament us heu trobat amb problemes gràfics (X no arrenca, o bé no us reconeix la configuració de la vostra pantalla, no es guarda la informació de la sessió ni es modifica xorg.conf, etc...)
Una cerca al google us confirmarà que hi ha un problema: el mòdul dins el kernel de la 12.04 és més avançat que els drivers (oberts o propietaris) que us proposarà el sistema.
El driver nou es pot insta&#320;lar amb aquestes comandes:
```

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

```
Insta&#320;leu i reinicieu el sistema. A continuació premeu <SUPER> i cerqueu Nvidia per obrir el programa de configuració. Ara sí que es guardarà la sessió amb la nova configuració de pantalla.

---

### Post by lluisanunez on 2012-05-23
Aquest problema s'ha solucionat avui, amb l'upgrade del kernel

---


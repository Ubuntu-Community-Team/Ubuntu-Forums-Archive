---
title: "Instalar xwindow al ubuntu server"
date: 2009-03-14
forum: Catalan Team
---

### Post by ETP on 2009-03-14
Hola soc nou amb tot aixo del linux i especialment amb unbuntu. Tinc un servidor recuperat, que li he instalat un ubutu server 8.10. Unicament porta la linia de comandes i per un novato es mes dificil. Es possible instala el xwindow, no ho he pogut fer. El problema es que hi tinc un proxy entremig i no el ser configurar amb la lina de comandes.
gracies

---

### Post by papapep on 2009-03-14
Bones, ETP.

Per configurar l'apt per passar pel proxy, fica dins /etc/apt/apt.conf:

```
Acquire::http::Proxy "http://ip-del_proxy:port/";
```

a:

```
man apt.conf
```

trobaràs moltíssima informació de les opcions d'aquest fitxer de configuració.

Per instal·lar l'entorn d'escriptori:

```
sudo aptitude install ubuntu-desktop
```

O kubuntu-desktop (per KDE) o xubuntu-desktop (per XFCE).

---

### Post by ETP on 2009-03-16
Gracies, havia de ser molt facil pero pel novatos ens encallem a qualsevol lloc.

---


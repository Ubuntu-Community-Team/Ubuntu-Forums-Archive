---
title: "Preferències-Sessions"
date: 2007-09-22
forum: Catalan Team
---

### Post by prostata on 2007-09-22
Dins Kubuntu (*), on és Preferències-Session. Vull configurar Beryl i fer que arrenqui quan arrenqui Kubuntu...Gràcies

(*) de tant trastejar amb les Xserver he reinstal-lat Kubuntu i encara  no domino ben bé el seu entorn gràfic respecte a Ubuntu..

---

### Post by pespin on 2007-09-22
Del meu blog he extret això. Fa molt temps que ho vaig escriure i no recordo exactament de que anava el tema:

Si volem que arranqui al inici: Gnome: Sistema -> Preferencies ->Sessions i afegim a “Programes al iniciar” => beryl-manager 

Kde: comanda a la consola

    ln -s /usr/bin/beryl-manager ~/.kde/Autostart/beryl-manager

---

### Post by prostata on 2007-09-22
> **pespin said:**
> Del meu blog he extret això. Fa molt temps que ho vaig escriure i no recordo exactament de que anava el tema:

Si volem que arranqui al inici: Gnome: Sistema -> Preferencies ->Sessions i afegim a “Programes al iniciar” => beryl-manager 

Kde: comanda a la consola

    ln -s /usr/bin/beryl-manager ~/.kde/Autostart/beryl-manager

He fet el que escrius, però ara voldria saber com fer per treure'l, es dir la  opció inversa a la que em dius..aixì el posaré i treuré quan jo vulgui

Gràcies

---

### Post by pespin on 2007-09-22
doncs en principi eliminant el link que has fet ja està:
```

rm ~/.kde/Autostart/beryl-manager
```

---


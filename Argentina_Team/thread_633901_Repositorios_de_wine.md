---
title: "Repositorios de wine"
date: 2007-12-07
forum: Argentina Team
---

### Post by benzema on 2007-12-07
Oigan tengo wine que lo instale hace una semana desde synaptic pero me instalo la version 0.9.46 y no tengo para actualizarla y mirando en webs de juegos para linux vi que salio la 0.9.50 como puedo hacer para que se actualize por ahi vi que estan  los repositorios de wine oficiales con todo al dia pero no encontre para gutsy solo para feisty y versiones anteriores, antes de postear busque mucho pero realmente no encontree espero que me puedan ayudar ,un abrazo fuerte a toda la comunidad saludos.

---

### Post by kowal on 2007-12-07
(Extraído de [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)). En la terminal copiás y pegás:

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
```

Listo ya quedan agregados los repos.

Saludos!

---


---
title: "Arxiu xorgc.onf"
date: 2007-06-25
forum: Catalan Team
---

### Post by prostata on 2007-06-25
Companys, 

tinc un problema amb l'arxiu xorg.conf i és que encara que amb nautilus el veig, no el puc trobar per consola. quan arribo a /etc/ i faig el corresponent cd a /X11 per tocar l'arxiu, [vull tocar la resolució de pantalla per consola], em diu que /X11 no existeix. faig un ls i no és veu. Puc obrirlo amb un editor de text, però com bé sabeu desrpès no m'el diexa "guardar"...¿teniu alguna sol-lució??

Gràcies

---

### Post by papapep on 2007-06-25
Evidentment has d'estar cometent algun error tipogràfic en posar la comanda al terminal (p ex. com el que has comés al títol del post, que has posat xorg**[COLOR="Red"]c[/COLOR]**):

cal que posis:

```
sudo nano /etc/X11/xorg.conf
```

També tens l'opció d'executar el gedit desde consola, com a usuari normal:

```
sudo gedit
```

I podràs editar i desar qualsevol fitxer.

I, òbviament, si l'xorg.conf el trobes en mode gràfic, també hi és via consola.

---

### Post by RainCT on 2007-06-25
> **prostata said:**
> em diu que /X11 no existeix

Efectivament, /X11 no existeix, sinó que existeix /etc/X11. Per entrar-hi fes o bé:

```

cd /etc/X11

```

o bé:

```

cd /etc
cd X11

```

però mai:

```

cd /etc
cd /X11

```

Ja que la barra / al principi indica el directori arrel, així que al fer el "cd /X11" esta buscant la carpeta X11 al directori arrel i no a l'actual.

---

### Post by prostata on 2007-06-25
Gràcies per les vostres opinions i ajudes

---


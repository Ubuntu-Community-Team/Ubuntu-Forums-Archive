---
title: "[SOLVED] recuperació del backup de l'xorg.conf"
date: 2007-06-27
forum: Catalan Team
---

### Post by Curial on 2007-06-27
Confesso, he pecat.

En el meu afany de canviar la resolució de la meva pantalla a 1440x900 es escrit la línia:
sudo dpkg-reconfigure xserver-xorg
He triat VGA a 1440x900.

Bé quan he reiniciat em sortia aquell esgarrifós anunci que no es podia iniciar el meu servidor X.

He provat a engegar des de recovery mode i m'he trobat amb la mateixa situació.

Se que s'ha generat un arxiu backup nomenat /etc/X11/xorg.conf.20070627205931

Com m'ho puc fer per restaurar aquest backup si no aconsegueixo iniciar l'Ubuntu.

Haig de posar el disc d'intal·lació i engegar en live i intentar canviar de nom l'arxiu backup o alguna cosa així?

Sisplau que algú em doni l'absolució.(no ho faré més).
(Sigueu concients que aquestes paraules les escric des de güín-d'ous).
Gràcies

---

### Post by papapep on 2007-06-27
Simplement:

```

sudo cp /etc/X11/xorg.conf.20070627205931 /etc/X11/xorg.conf
```

---

### Post by RainCT on 2007-06-27
Això que ha dit el papapep ho escrius una tty (terminal fora del mode gràfic). Si no t'apareix cap automàticament prem la combinació "Ctrl + Alt + F1" (en lloc d'F1 potser fer servir qualsevol Fx fins al 6), poses nom d'usuari i contrasenya (la contrasenya, encara que no es vegi cap asterisc, l'agafa) i llavors fas això que t'ha dit.

---

### Post by Curial on 2007-06-27
Bufffffff!!

Ja està, gràcies per l'ajuda!

Al vostre consell he seguit amb la comanda "su" posant la meva contrassenya i fent un "shutdown now". Ha rebotat i ja s'ha vist el mode gràfic com sempre.

No se si era la continuació correcta?

Moltíssimes gràcies.

---

### Post by papapep on 2007-06-27
Amb un **startx** n'hi havia prou (recorda que això no és windows ;-D)

Però vaja, mal tampoc has fet.

Per cert, si en vers de "shutdown now", fas "shutdown -r now" és reinicia l'ordinador solet.

---


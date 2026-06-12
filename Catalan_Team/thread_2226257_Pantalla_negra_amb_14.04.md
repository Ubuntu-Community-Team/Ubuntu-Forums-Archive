---
title: "Pantalla negra amb 14.04"
date: 2014-05-26
forum: Catalan Team
---

### Post by lluisanunez on 2014-05-26
A veure si algú em pot ajudar. Vaig fer l'UPGRADE des de 13.10 a 14.04. Tot va com una seda fins al moment de reiniciar l'ordinador, a partir d'aqui... pantalla negra (amb el cursor del ratolí)
OK, entro amb el disc d'insta&#320;lació, recupero els documents que tenia, i inicio una altra insta&#320;lació en fresc. Durant la insta&#320;lació cap problema, i al reiniciar... pantalla negra.
Tinc una tarja Nvidia però ja fa 2 o 3 versions que no em cal cap controlador, si faig al terminal:
l```
luisa@xCube:~$ lspci | grep -i vga
01:00.0 VGA compatible controller: NVIDIA Corporation G72 [GeForce 7300 GS] (rev a1)

```
Ara per poder treballar he insta&#320;lat den ou la 13.10, però voldria la 14.04, a més vas rebent missatges continuament perquè facis l'upgrade. Alguna idea? 
Sembla alguna tonteria, algun detall que se m'escapa i que es podria arreglar amb un terminal des de la pantalla negra... ???

---

### Post by wgarcia on 2014-05-26
Sembla un problema de controlador de la targeta gràfica. Si des de la pantalla negra pots passar-te a una consola amb Ctrl-Alt-F6, per exemple (o iniciar el sistema ja en mode de proves), prova a veure si aquestes ordres a la consola ho arreglen:

```
sudo apt-get purge nvidia*
sudo apt-get install nvidia-current
```

---

### Post by lluisanunez on 2014-05-26
Gràcies. De moment he de treballar i seguire amb 13.10, el cap de setmana provaré de fer un upgrade i això que em dius

---


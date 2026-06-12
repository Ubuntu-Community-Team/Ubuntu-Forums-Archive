---
title: "Efecte cutre al moure finestres i visualitzar videos"
date: 2009-03-06
forum: Catalan Team
---

### Post by rognu on 2009-03-06
Després d'instal·lar els drivers de nvidia i configurar-lo gairebé tot, segueixo visualitzant malament certes coses.



El que passa és que al moure una finestra, aquesta sembla que es mou "per parts", l'efecte capturat és aquest:


[http://img175.imageshack.us/my.php?image=cptz.jpg](http://img175.imageshack.us/my.php?image=cptz.jpg)



En temps real no és tan exagerat però si es nota, i molt. Queda molt cutre i cansa bastant.



També em passa amb qualsevol video.

També es veu un efecte fantasma verdós al moure les finestres 

He pensat que sigui la freqüència de refresc vertical. Per al meu monitor a 1920x1200 és de 60hz.


Ho he posat a 60hz en  Sistema>preferències> NVIDIA X  server  settings como root però gens, segueix passant.

help, please!

---

### Post by papapep on 2009-03-06
[https://wiki.ubuntu.com/CatalanTeam/Recursos/ComPreguntar#Sigues%20prec%C3%ADs%20i%20informatiu%20sobre%20el%20teu%20problema](https://wiki.ubuntu.com/CatalanTeam/Recursos/ComPreguntar#Sigues%20prec%C3%ADs%20i%20informatiu%20sobre%20el%20teu%20problema)
[B][I]
Descriu l'entorn en el que et passa (màquina, S.O., aplicació, elquesigui).[/I][/B]

---

### Post by rognu on 2009-03-06
Sorry 

El pc: 
c2d 6600@3,6ghz 
4gb 1100 Corsair Dominator 
HD raptor 
SLI 8800gts g92 
en Asus Striker Extreme 

El monitor és un Dell 2407wfc (1920x1200@60hz) 

El SO és Ubuntu 8.10. kernel 2.6.27-11-generic 

Els drivers, els 180 de la web de nvidia (els dels repositorios no van bé). 

Crec que no em deixo res...

---

### Post by CarlesOriol on 2009-03-07
Jo també tinc un Dell amb un monitor de 1900x1200 amb una nveja-quadro i es veu bé.

Comprova que tinguis els "sync to vblank" activats al nvidia-settings.

N'hi ha 2:

a: XServer XVideo Settings 
i a: OpenGL Settings

---

### Post by rognu on 2009-03-09
gràcies. ja ho he activat. 
res de res, segueix igual. 

He provat fins i tot a augmentar la qualitat d'imatge i activar el sli... Sense resultats. 

La veritat és que l'efecte és matador...
:-(

---


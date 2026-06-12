---
title: "pantalla negra (11.04  no arrenca)"
date: 2011-05-24
forum: Catalan Team
---

### Post by ellington357 on 2011-05-24
Hola, fa un parell de dies que tinc problemes per arrencar l'Ubuntu 11.04.

Engego la màquina, surten les lletretes d'ubuntu amb els punts a sota, la pantalla es posa lila, després negra, i aquí s'acaba tot.

He provat diverses solucions trobades a la xarxa, com aquesta (en recovery mode):

*Para solucionarlo: escribe: [COLOR=#008000][I]sudo dpkg-reconfigure xserver-xorg*[/COLOR] [/I]

o aquesta:

[I]Cuando aparezca el grub, nos posicionamos  sobre la entrada con la que cargaremos el sistema y volvemos a hacer lo  mismo que en el paso 1: pulsamos en este caso la tecla “e” para editarla  y reemplazamos la parte final, que será “quiet splash --“ o simplemente  “quiet” y en su lugar escribimos **nomodeset x11failsafe**.
Después pulsamos “Ctrl. + X” para que cargue el sistema con estas opciones.
[/I]
Però de moment no me'n surto. Curiosament, totes dues han funcionat una sola vegada, però quan torno a engegar torno a tenir el mateix problema i la solució aplicada anteriorment no funciona.

Tinc por d'haver fet alguna animalada...

Potser hauria de tornar a instal·lar el sistema (no ho sé), però abans hauria de poder entrar per fer còpies de seguretat pels arxius importants que tinc....

Això em passa amb un PC de sobretaula Compacq que també té Windows 7.

Bé, si algú em pot orientar li estaré molt agraït. Sóc molt novell en aquest món: ho dic per si no es notava :)

Gràcies!

---

### Post by wgarcia on 2011-05-25
Has provat d'entrar en mode "recovery"?

---

### Post by ellington357 on 2011-05-25
Sí, ho vaig provar i no me'n sortia. Llavors vaig decidir que instal·laria la versió 10.10, ja que la 11.04 em donava problemes. Ho vaig fer, cosa que ha estat causa de noves desgràcies que explicaré en un altre thread...

---


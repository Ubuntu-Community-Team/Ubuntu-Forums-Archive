---
title: "Problemes amb el driver nvidia 180"
date: 2009-04-25
forum: Catalan Team
---

### Post by torracastanyes on 2009-04-25
Bona nit.

Ahir vaig actualitzar la meva màquina de proves que tenía la 9.04RC i va funcionar com una seda, així que avui he volgut actualitzar la màquina principal que tenía la 8.10, però al reiniciar em diu que no pot configurar l'entorn gràfic.
Crec que en algun lloc deia que el driver nvidia 180.44 està compilat amb el kernel 2.6.24 Ubuntu Server i no és compatible amb l'actual.

Com que algún cop m'ha tret d'un mal pas, reinicio i entro amb el kernel del Intrepid. Tot funciona normalment, així que edito l'xorg.conf i passo al driver nv. A partir d'aquí la pantalla em queda a 400x300 amb tots els kernels. Com que així no vaig enlloc, elimino tots els paquets d'nvidia i des del terminal instalo l'Envy i el driver 180 i em quedo amb la pantalla negra amb tots dos kernels. Finalment, he hagut d'instalar el driver 173.

Ara tinc la màquina vella, amb una gforce 6600, funcionant amb el driver 180 i la nova, amb una 7600 GS només va amb el 173. Com s'entén?

---

### Post by jerec on 2009-04-26
No t'hi escalfis, que ja ho vaig fer jo!!!!

Ahir vaig decidir posar el 9.04 a les dues maquines que hi ha a casa. Amb totes dues vaig renegar molt amb el driver 180 de nvidia. Ho vaig provar tot, no hi va haver-hi mes remei que deixar-lo funcionant amb el de 173

totes dues son amb configuració de dual monitor i ho vaig provar a ma, amb envy. Una es 32 bits i l'altre 64. El que em faltava es compilar el driver original de can nvidia, pero amb el 173 ja funciona 

Buscant per internet, veig que no som els únics que tenim problemes.

Pensa també afegir el usuari al grup "video", sinó nanai del "direct render"

---

### Post by torracastanyes on 2009-04-26
No sé si a tú t'ha passat el mateix, però des que tinc aquestes targes, cada actualització ha estat un mal de cap. Tot i això, que recordi, és el primer cop que em trobo d'entrada amb la pantalla negra.

Què se n'ha fet del dpkg-reconfigure xserver-xorg????

---

### Post by LitusMayol on 2009-04-27
> **torracastanyes said:**
> No sé si a tú t'ha passat el mateix, però des que tinc aquestes targes, cada actualització ha estat un mal de cap.

100% d'acord. Quin merder, i cada cop diferent!

---

### Post by caxipu on 2009-04-27
> **torracastanyes said:**
> Bona nit.

Ahir vaig actualitzar la meva màquina de proves que tenía la 9.04RC i va funcionar com una seda, així que avui he volgut actualitzar la màquina principal que tenía la 8.10, però al reiniciar em diu que no pot configurar l'entorn gràfic.
Crec que en algun lloc deia que el driver nvidia 180.44 està compilat amb el kernel 2.6.24 Ubuntu Server i no és compatible amb l'actual.

Com que algún cop m'ha tret d'un mal pas, reinicio i entro amb el kernel del Intrepid. Tot funciona normalment, així que edito l'xorg.conf i passo al driver nv. A partir d'aquí la pantalla em queda a 400x300 amb tots els kernels. Com que així no vaig enlloc, elimino tots els paquets d'nvidia i des del terminal instalo l'Envy i el driver 180 i em quedo amb la pantalla negra amb tots dos kernels. Finalment, he hagut d'instalar el driver 173.

Ara tinc la màquina vella, amb una gforce 6600, funcionant amb el driver 180 i la nova, amb una 7600 GS només va amb el 173. Com s'entén?

Hola bones el meu cas es el mateix. També en trobo que no puc entrar un cop reinicio l'ordinador després d'haber actualitzat l'ubuntu a 9.04. I en pregunto com hi aneu al kernel del intrepid? Jo encara no he pogut entrar per poder configurar el nvidia 173. Com ho haig de fer?

---

### Post by torracastanyes on 2009-04-27
Per triar él kernel a l'arrencada, només has de pitjar "esc" i triar-lo de la llista, però per això no et cal. Només explicava les meves peripècies.

Per instalar el driver, quant arribis a la pantalla negra, pitja Control+Alt+F1 i et demanarà login i password.
Si no téns instalat l'envy, l'instales:

 ```

``` sudo apt-get install envyng-core  ```

```



i després l'obres:

 ```

```sudo envyng -t ```

```



A la primera llista, selecciones "instalar driver nvidia"
i després pots triar una versió. Pots anar provant fins trobar la que funcioni.

Si necessites més imformació, la pàgina principal és aquí:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by prostata on 2009-04-28
Doncs a jo en un altre màquina en la que tinc una gràfica Nvidia GeForce 6200 i fent una instalació neta de la jaunty, i amb el genvy he instal-lat el 180, però la combinació de tecles CTRL+ALT+Back space no em funciona i haig de ferlo per l'icona sortir de sessió, i això que la instalació feta aquest matí es totalment neta....què puc fer...???

---

### Post by LitusMayol on 2009-04-28
> **prostata said:**
> Doncs a jo en un altre màquina en la que tinc una gràfica Nvidia GeForce 6200 i fent una instalació neta de la jaunty, i amb el genvy he instal-lat el 180, però la combinació de tecles CTRL+ALT+Back space no em funciona i haig de ferlo per l'icona sortir de sessió, i això que la instalació feta aquest matí es totalment neta....què puc fer...???

Diria que això no és un error, sinó que en aquesta versió d'**Ubuntu** està desactivada per defecte. Diria que ara hi ha una altra manera de fer-ho (Alt + Pet Sis + K ), però em sóna que és que enlloc de les X treballa m&#347; a fons (suposo que nucli...). Però hi ha una manera de reactivar l'altra combinaci&#7765;... Però ni idea.

Que t'ho confirmi algú dels que en sap.

---

### Post by prostata on 2009-04-29
> **LitusMayol said:**
> Diria que això no és un error, sinó que en aquesta versió d'**Ubuntu** està desactivada per defecte. Diria que ara hi ha una altra manera de fer-ho (Alt + Pet Sis + K ), però em sóna que és que enlloc de les X treballa m&#347; a fons (suposo que nucli...). Però hi ha una manera de reactivar l'altra combinaci&#7765;... Però ni idea.

Que t'ho confirmi algú dels que en sap.

gràcies litus, vaig trobar la sol-lució ahir i la vaig publicar [http://ubuntuforums.org/showthread.php?t=1141162](http://ubuntuforums.org/showthread.php?t=1141162)

Cóm ara no es pot posalr el SOLVED doncs....

Salutacions

---


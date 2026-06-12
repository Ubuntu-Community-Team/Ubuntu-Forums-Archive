---
title: "No puc entrar al Ubuntu després d'actualitzar a 11.04"
date: 2011-05-02
forum: Catalan Team
---

### Post by lluisalguero on 2011-05-02
Hola amics,

aquest fi de setmana hem va saltar l'actualització a 11.04. Després de tota l'actualització i al reiniciar no hi ha forma de poder entrar.

Us fico unes fotos per si serveix d'ajuda

Aquest és l'aspecte del GRUB després de la actualització (no sé perquè ara la resolució de pantalla és diferent)

[[IMG]http://img156.imageshack.us/img156/8935/img20110502064354.jpg[/IMG]](http://img156.imageshack.us/i/img20110502064354.jpg/)

Si trio la primera opció, que seria el més normal, primer la pantalla em fa pampalluges per a finalment mostrar aquestes linees

[[IMG]http://img864.imageshack.us/img864/1062/img20110502064512z.jpg[/IMG]](http://img864.imageshack.us/i/img20110502064512z.jpg/)

Si trio el mode de recuperació, faig cap a aquest menu, però triant qualsevol de les opcions, no aconsegueixo arrancar l'Ubuntu

[[IMG]http://img848.imageshack.us/img848/759/img20110502064606.jpg[/IMG]](http://img848.imageshack.us/i/img20110502064606.jpg/)

Dir-vos que fins ara, l'Ubuntu m'ha anat perfecte, no entenc el perquè ara d'això :confused:

Moltes gràcies per l'ajuda que em pugueu donar

---

### Post by lluisalguero on 2011-05-02
Perdó per la mida de les imatges, les he pujat a imageshacks i pensava que me les redimensionava totes i només m'ho ha fet amb la primera

---

### Post by wgarcia on 2011-05-02
Sembla que això està passant per a alguns ordinadors amb targeta gràfica NVIDIA d'un cert model.

Saps quina targeta gràfica té el teu ordinador?

Has provat si l'ordinador arrenca amb un USB o CD autònom de la versió 11.04?

---

### Post by lluisalguero on 2011-05-02
> **wgarcia said:**
> Sembla que això està passant per a alguns ordinadors amb targeta gràfica NVIDIA d'un cert model.

Saps quina targeta gràfica té el teu ordinador?

Has provat si l'ordinador arrenca amb un USB o CD autònom de la versió 11.04?

Gracies per la resposta, el meu portàtil fa servir **ATI Mobility Radeon HD 4500 Series**, es un HP Pavillion

El que si he pogut es arrencar-lo amb una opció que em dona una resolució més baixa, però no sé llavors que haig de fer

Moltes gràcies per la teva resposta

---

### Post by Original Flo on 2011-05-03
Buenas, jo també tinc una ati com tu en un portàtil HP pavilion dv7.

Si pots entrar al mode gràfic segur o si pots entrar d'alguna manera, has de fer lo següent.

A internet ves a la següent pagina

[http://www.amd.com/es/Pages/AMDHomePage.aspx](http://www.amd.com/es/Pages/AMDHomePage.aspx)

Tria el driver per la teva tarja gràfica.

Guarda els drivers a una carpeta coneguda, com per exemple "Descarregats".

Obre un terminal.

Ves fins al directori on esta el driver.

```
cd /home/nomusuari/Descarregats
```On he posat "nomusuari" has de posar el nom d'usuari que tinguis al teu ordinador.

Fent aixo ja estaràs al directori on esta el driver.

Després escrius lo següent.

```
sudo sh ./nomcomplertdelarxiudeldriver.run
```On posa "nomcomplertdelarxiudeldriver.run" en lloc d'això posas el nom de l'arxiu complert que t'has descarregar, que ha de ser un nom semblant a "ati-driver-installer.11-4-x86.x86_64.run".

Et demanarà varies coses.

Has d'escollir la opció Xorg. Si t'ho demana al terminal has de posar un "1" (Et sortirà un [1], però aixo no vol dir que ja estigui posat, es nomes per indicar la opció per defecte, has de pitjar l'1 igualment i acceptar). Si to fa al mode gràfic, la selecciones.

Et demanarà si vols la instal·lació automàtica per defecte o que et generi un paquet especific per la teva distribució. L'hi dius la automàtica per defecte.

Triga un minutet o mes en instal·lar.

Quan acabi et sortirà un missatge molt llarg que dirà que has de reiniciar per aplicar els canvis. Reinicia i entra normalment.

Has de tornar a fer lo mateix cada final de mes que es quan surten les actualitzacions del drivers ati si vols tenir els drivers de la teva gràfica actualitzada ja que si no quan s'actualitzin els kernels o altres coses, deixarà de funcionar l'acceleració gràfica.

Espero que et sigui útil.

Salut.

---

### Post by lluisalguero on 2011-05-03
Moltes gràcies Original Flo, tant aviat com pugui faré el que em dius i ja us contaré com ha anat.

---

### Post by lluisalguero on 2011-05-03
Ara ja puc entrar, però ha estat més senzill del que sembla. Si us fixeu a la primera captura, fica que és la versió "pae", que després de googlejar, veig que és la que fan servir als servidors.

He triat la opció "Previous Linux versions" i allà està la versió "normal", he entrat perfectament.

Ara tindria que obrir un altre fil, perquè de moment i pel que veig...la barra aquesta de la esquerra que em surt hi han com uns 25-30 icones, m'ha desaparegut la barra de baix, els menus, etc. No sé si serà per la versió (11.04) o perquè no es va acabar d'instal·lar bé.

Tanco el post i el deixo com a [SOLVED]

---

### Post by Original Flo on 2011-05-03
Buenas, si no instal·les els drivers de la tarja de vídeo, no tindràs acceleració gràfica i no podràs utilitzar unity complert, set carregarà la versio 2D o  la versió Gnome.

A Natty no hi ha barra a la part de baix, a no ser que no entris a l'escritori per defecte (Unity).

Com es aixo de que no es va instal·lar be???

---

### Post by lluisalguero on 2011-05-03
> **Original Flo said:**
> Buenas, si no instal·les els drivers de la tarja de vídeo, no tindràs acceleració gràfica i no podràs utilitzar unity complert, set carregarà la versio 2D o  la versió Gnome.

A Natty no hi ha barra a la part de baix, a no ser que no entris a l'escritori per defecte (Unity).

Com es aixo de que no es va instal·lar be???

Crec que si s'han instalat els drivers perquè es veu prou bé (suposo). El que voldria es tornar al Gnome, aquesta nova interfície no m'agrada gens

Ara estic escrivint des d'un altre pc, ja que al que tinc instal·lat l'Ubuntu he desmarcat una opció al Compiz on ficava alguna cosa del Unity, ara només tinc una pantalla amb el fons, sense icones, sense barres ni res...tot un drama

---

### Post by lluisalguero on 2011-05-03
Ja torno a tindre l'Unity en marxa, però prefereixo el Gnome

---

### Post by pere vidal on 2011-05-03
hola a tots i totes
m'estic rellegint els erros que ha donat al pas a 11 04 i veig que a algú li ha passat el que m'ha passat a mi.

amb 10 10 perfecte.
al passar ja sigui des de 10 10 com instal.lació neta dona problemes amb la gràfica.
tinc una ATI hd 5450  
tinc instal.lada la versió 11 04 de amd ati. 
ho he fet desde els controladors adiccionals i també directament seguint les instruccions de AMD ATI...
tan d'una manera com de l'altra passa que si tinc activada la targeta gràfica no puc entar al escriptori unity ni al clàssic.
nomes al ubuntu sense efectes y al unity2

en canvi si la desistal.lo si que puc entrar als quatre escriptoris pero no funciona la mitat de les coses.  
i ja no se que fer.   esperaré a que passi un mes i tornaré a baixar el cd del 11 04 i espero que ho tinguin controlat.

---

### Post by pere vidal on 2011-05-03
> **Original Flo said:**
> Buenas, jo també tinc una ati com tu en un portàtil HP pavilion dv7.

Si pots entrar al mode gràfic segur o si pots entrar d'alguna manera, has de fer lo següent.

A internet ves a la següent pagina

[http://www.amd.com/es/Pages/AMDHomePage.aspx](http://www.amd.com/es/Pages/AMDHomePage.aspx)

Tria el driver per la teva tarja gràfica.

Guarda els drivers a una carpeta coneguda, com per exemple "Descarregats".

Obre un terminal.

Ves fins al directori on esta el driver.

```
cd /home/nomusuari/Descarregats
```On he posat "nomusuari" has de posar el nom d'usuari que tinguis al teu ordinador.

Fent aixo ja estaràs al directori on esta el driver.

Després escrius lo següent.

```
sudo sh ./nomcomplertdelarxiudeldriver.run
```On posa "nomcomplertdelarxiudeldriver.run" en lloc d'això posas el nom de l'arxiu complert que t'has descarregar, que ha de ser un nom semblant a "ati-driver-installer.11-4-x86.x86_64.run".

Et demanarà varies coses.

Has d'escollir la opció Xorg. Si t'ho demana al terminal has de posar un "1" (Et sortirà un [1], però aixo no vol dir que ja estigui posat, es nomes per indicar la opció per defecte, has de pitjar l'1 igualment i acceptar). Si to fa al mode gràfic, la selecciones.

Et demanarà si vols la instal·lació automàtica per defecte o que et generi un paquet especific per la teva distribució. L'hi dius la automàtica per defecte.

Triga un minutet o mes en instal·lar.

Quan acabi et sortirà un missatge molt llarg que dirà que has de reiniciar per aplicar els canvis. Reinicia i entra normalment.

Has de tornar a fer lo mateix cada final de mes que es quan surten les actualitzacions del drivers ati si vols tenir els drivers de la teva gràfica actualitzada ja que si no quan s'actualitzin els kernels o altres coses, deixarà de funcionar l'acceleració gràfica.

Espero que et sigui útil.

Salut.

a mi m'ha anat molt be.....

---

### Post by Original Flo on 2011-05-03
En-recordat de fer lo mateix amb les noves versions que surtin d'ati catalyst, surten cada final de mes, sobre el dia 25-29 de cada mes, si no quan actualitzis kernels o altres coses et deixarà de funcionar.

---


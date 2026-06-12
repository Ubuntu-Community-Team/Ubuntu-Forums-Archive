---
title: "No hem funciona ubuntu 9.04"
date: 2009-05-08
forum: Catalan Team
---

### Post by carlesbm on 2009-05-08
Hola ha tots

   Us plantejo el meu problema.

   Fa uns dies vaig actualitzar el meu Ubuntu de 8.10 a 9.04, tot anava be fins que vaig veure una opcio dins del menu administra que ens permetia de fer una neteja de sistema ( pel que he trobat per internet es diu "Computer Janitor") vaig executar-lo i vaig seguir normalment.
   Tot seguit, vaig comprobar eslcontroladors propietaris i vaig veure que no tenia els controladors de la meva tarja ATI activat i vaig activar-lo, el vaig instalar i tot anava be.Vaig tancar el ordinador.
   
   Quan l'he intentat de obrir vaig veure que al grup m'havia desaparegut les una de les opcions de linux header, però vaig arrencar igualment, i aqui tenim que no arrancava es va quedar amb la pantalla negra despres del logotip de Ubuntu.
    Vaig tornar a reiniciar i vaig arrencar en mode rescat un cop dins del menu vaig respaturar el paquets amb la opcio que apareix DPKG.... va descarregar imaginoa que tot el que havia borrat i trovaba en falta meny un fixer (linux-module-generic... crec que era així) però jo vaig seguir endavant. Reinicio el sistema i tot sembla anar be fins que despres del logotip apareixen linies que van indicant els moduls que es carreguen; MySQL.... tot esta [OK] menys un que crec que era alguna cosa com (Virtual... i header 2.2.....) no recordo massa be doncs va molt rapid que dona [FALIED]. Segueix arrencant i no apareix l'escriptori sino que pareixen unes linies a la part superior de la pantalla. He pitjat Ctrl+F1 i tampoc apareix la linis de comandes.

   Estic apunt de tornar ha instal-lar el S.O. pero crec que te que haver alguan forma de recuperar el control.

   Si algu hem pot donar algun consell 'hi estaré molt agraït.

Moltes gracies

  P.D.: No tocar el que no estem segurs de com funciona, però la curiositat pot més.

---

### Post by oriolsbd on 2009-05-08
No sé si et servirà d'alguna cosa, però si obres el Synaptic i fas "Fitxer>Història" pots veure quins paquets exactament es van esborrar (em sembla que també veu els que s'han borrat des del Janitor).

Salut!

---

### Post by carlesbm on 2009-05-09
Hola oriolsbd

  Segurament no ho he explicat massa be, no puc veure l'escriptori l'unic que puc fer entrar en mode rescat desde el grup i intentar de aplicar alguna cosa desde l'interpret d'ordres.

  He descarregat la versió Alternate de i he seleccionat la opcio de rescatar un sistema no funcional, però no ho veig clar, si executo aquesta opció sembla que realitza la instalació, i segurament pedi tot el que tinc referent a documents, els programes son recuperables.

  Gracies i segueixo atent a noves propostes.

---

### Post by carlesbm on 2009-05-09
Hola novament

   Ja ho he pogut recuperar.

    Finalment he entrart en mode rescat he accedit al mode root de consola i he executat:

apt-get purge xserver-xorg

despres he fet:

apt-get install xserver-xorg

i he reiniciat l'ordinador, tot ha tornat ha funciona menys la impressora que l'he tingut que configurar de nou, igualment ha passat amb l'escaner, però ara tot torna a funcionar.

Gracies

---

### Post by PatrickVogeli on 2009-05-10
jo el computer janitor aquest no el faria servir.. he llegit que les experiencies no son massa bones!

---


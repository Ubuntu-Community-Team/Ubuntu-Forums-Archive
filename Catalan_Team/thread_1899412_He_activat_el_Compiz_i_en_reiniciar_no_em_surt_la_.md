---
title: "He activat el Compiz i en reiniciar no em surt la barra lateral..."
date: 2011-12-23
forum: Catalan Team
---

### Post by Jayhawker on 2011-12-23
He activat el Compiz i en reiniciar no em surt la barra lateral, i a més em surt un estrany menu en la part de dalt que abans no hi era. 

De quina manera puc desactivar-lo, sisplau? Ja que en no haver la barra lateral esquerra no puc buscar programes ni res de res. 

Mercès

---

### Post by wgarcia on 2011-12-24
Quan dius, "he activat el Compiz"... exactament, què has fet? 

Pel que descrius has canviat l'escriptori, però no queda clar exactament a quin escriptori exactament estàs entrant.

---

### Post by Jayhawker on 2011-12-24
Volia dir que he activitat tot allò per a fer rotar el cub. Aquest efecte, i també allò de les finestres que semblen xicle quan les desplaces; en fi, tot això. En reiniciar, el "workspace" de l'esquerra ha desaparegut, i per tant no puc activar res: ni browser, ni descàrrega de programes, ni terminal, ni Evolution, tot això. L'escriptori té la mateixa imatge de fons, però res més. Només hi ha la barra estreta de dalt que no permet gaire cosa.  

> **wgarcia said:**
> Quan dius, "he activat el Compiz"... exactament, què has fet? 

Pel que descrius has canviat l'escriptori, però no queda clar exactament a quin escriptori exactament estàs entrant.

---

### Post by wgarcia on 2011-12-25
És convenient que expliquis detalladament el que has fet per rebre suport, com has fet a l'últim missatge, perquè si no es fa molt difícil saber què ha causat el problema. 

En aquest cas per solucionar-ho a la pantalla d'entrada, on entres l'usuari i la clau, escull "Ubuntu 2D". Un cop que s'obre l'escriptori torna a obrir l'eina de configuració de Compiz, i marca l'opció "Unity". Un cop fet això surt de la sessió, i en tornar a entrar, escull "Ubuntu" (en comptes d' "Ubuntu 2D" com has fet l'últim cop). 

Tot hauria de tornar a la normalitat ara.

---

### Post by quitus on 2011-12-27
No se si encara s'estila allò de eliminar la carpeta de configuració del programa que ens hem carregat en trastejar.

En aquest cas hi ha diverses carpetes ocultes de configuració del compiz.

salut

---

### Post by CarlesOriol on 2011-12-28
Quina versió de l'ubuntu tens insta&#320;lada?

---

### Post by juandescals on 2012-01-31
M'ha passat el mateix. He hagut de desinstal·lar Compiz però abans vaig fer això:

1. Clik derecho en el escritorio y seleccionas la opción crear un lanzador…
2. Eliges la opción tipo “Aplicacion de terminal” y en el campo Comando escribimos: sudo killall gnome-panel
3. Lo creas y lo ejecutas
4. Creamos otro lanzador y como Comando escribimos: gnome-panel
5. Lo creas y lo ejecutas (Si todo ha ido bien, aparecerá el panel superior)

---


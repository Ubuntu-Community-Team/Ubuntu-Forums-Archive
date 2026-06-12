---
title: "Anular el so de benvinguda"
date: 2009-06-14
forum: Catalan Team
---

### Post by lluisbages on 2009-06-14
Tinc instal·lat l'ubuntu 9 i quan utilitzo l'escriptori GNOME puc, sense cap tipus de  problemes, anular el so de benvinguda i de sortida . Voldria fer el mateix quan utilitzo l'escriptori KDE. 
com puc, doncs anular el so de benvinguda i de sortida  que per defecte emet l'UBUNTU?


Gràcies

---

### Post by SiscoGarcia on 2009-06-14
A mi fa un temps em va passar una cosa semblant amb el soroll de sortida a xubuntu; no recordo qui em va donar la solució de més avall. L'he provat amb gnome i també em funciona, espero que valgui per KDE 

Es tracta d'editar l'arxiu /etc/modprobe.d/blacklist
  
    ```
sudo gedit /etc/modprobe.d/blacklist
```

afegir-hi:

    ```
#Mòdul de pitidets de sistema
blacklist pcspkr
```

i per treure el soroll JA
    
    ```
sudo rmmod pcspkr
```

Sort ;)

---

### Post by CarlesOriol on 2009-06-15
Menu 

Sistema > preferencies > audio > sons 
Entorn gràfic > inicia

(ara estic en un ubuntu en italià i els noms dels menus poden ser lleugerament diferents)

---

### Post by lluisbages on 2009-06-15
Ja ho he solucionat. No és ben bé com m'aconsellàveu però les vostres indicacions m'han donat una pista molt bona.
el camí correcte és:

preferits-->>arranjament del sistema-->>notificacions del sistema-->> pestanya "arranjament del reproductor-->> i finalment, ens caldrà clicar a "sense sortida d'àudio"

i Ja està. el so de benvinguda ha desaparegut.

---


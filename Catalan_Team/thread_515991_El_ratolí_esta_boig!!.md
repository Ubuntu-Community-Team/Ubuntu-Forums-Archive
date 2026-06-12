---
title: "El ratolí esta boig!!"
date: 2007-08-02
forum: Catalan Team
---

### Post by benetj on 2007-08-02
Hola
Volia comentar-vos el problema, un de nou :) que tinc.
ara li toca el torn al ratolí. Quan em passejo per l'escriptori (parlam de gnome) on tenc varies finestres obertes, es tot un espectacle. Pareix com si anés seleccionant, tancant les finestres cada vegada que es va movent. Buf quin pal!!
També em passa quan intento copiar un text a un camp, just posisionant-m'hi al sobre ja queda aferrat i a vegades varies vegades.

Be vos pas la secció del ratolí del fitxer xorg.conf 

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

```

Algú sap com ho puc arreglar??

Salut!

---

### Post by PellRoja on 2007-08-02
doncs mira, a mi això m' ha passat sobint i resulta que era el ratoli que al natejar ha deixat de fer-ho. Mira de netejar-lo be per dins. obrir-lo del tot que potser algun pel o pols esta creant curtcircuit.

;)

---

### Post by benetj on 2007-08-03
Hola PellRoja

El que passa es que el meu ratolí es òptic :-P 
Se que funciona be, ja que l'he provat a altres màquines tant amb gnu/linux com amb güindows.

Salut !

---

### Post by orestesmas on 2007-08-03
No sé massa què dir-te, excepte que jo m'havia trobat amb una cosa semblant i era per tenir seleccionat un protocol erroni (ImPS/2 en el teu cas). Però com que suposo que això no serà (el teu ratolí té rodeta, oi?) aleshores només se m'acut dir-te que ho comprovis amb un altre escriptori (xfce, kde) a veure si el problema és del Gnome o de les Xorg mateixes.

---

### Post by CarlesOriol on 2007-08-03
Probablement sigui degut a l'estat inactiu del kde que produeix errors per emissió de freqüències d'enveja. :-P (he he)

Ara sense conyes, pot ser que el cable faci un mal contacte si en té (a vegades es trenquen per dintre de doblegar-los) , o que estigui rebent interferències (tipus algun transformador massa prop).

També es possible que sigui la superfície de treball que sigui un pel reflectant. Fins i tot alguns barnissos de fusta poden produir aquest tipus d'errors.

Alguns llums (tipus fluorescent) també poden produir errors en ratolins òptics.

------------------------------------------

Una altra reflexió és si estàs treballant amb un portàtil que no tinguis algun problema al touchpad. (OFFTOPIC: Orestes com traduiries touchpad?)

---

### Post by ealbert on 2007-08-07
Hola companys, no fa gaire vaig canviar per avaria a un ratolí òptic i al cap de uns dies, sense adonar men, de cop i volta si estava passejant per la dreta marxava per lliure on ell volia, ja hem plantejava comprar-men un de bola i donar-lo per inservible, però la solució ha estat més senzilla: llençar la catifa del ratolí i fer-lo córrer directament per sobre la taula, s'han acabat els meus problemes...

---

### Post by ealbert on 2007-08-07
Aclaració: la catifa  (o alfombreta) del ratolí era estampada amb propaganda; per contraposició la taula és blanca i d'aquesta manera el lector òptic del ratolí no pren lectures errònies.

---

### Post by lluisanunez on 2007-08-08
El meu ratolí òptic es va tornar boig i es comportava exactament com tu dius, va resultar que s'hi havia posat un trosset de ce&#320;lofà que gairebé ni es veia, just al damunt de l'ull...

---

### Post by CarlesOriol on 2007-08-09
També pot ser que d'un cop l'ull (homenatge a lluisanunuez) s'hagi mogut o estigui mal subjecte dins la carcassa.

---


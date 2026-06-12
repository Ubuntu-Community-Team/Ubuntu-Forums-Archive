---
title: "Pampallugues a la pantalla"
date: 2007-10-29
forum: Catalan Team
---

### Post by lluisalguero on 2007-10-29
3.- També de tant en tant, la pantalla em fa una petita pampalluga, aleatòria, sense que estigui fent res en concret. No és que molesti gaire, però crec que tampoc és massa normal.

---

### Post by jerec on 2007-11-01
Jo revisaria el teu xorg.conf a veure si tens ven posada la configuracio del monitor. mira que tinguis correctament les frequencies verticals i horitzontals que et diu el manual del monitor.
Sino prova directament amb un altre monitor a veure si fa el mateix.

Et deixo un exemple d'una de les meves pantalles.

```

Section "Monitor"
    Identifier     "Monitor[0]"
    VendorName     "BNQ"
    ModelName      "BENQ FP91GX"
    DisplaySize     376    301
    HorizSync       29.0 - 83.0
    VertRefresh     43.0 - 76.0
    Option         "DPMS"
EndSection

```

---

### Post by lluisalguero on 2007-11-01
```
Section "Monitor"
	Identifier	"Monitor genèric"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce Go 7600]"
	Monitor		"Monitor genèric"
	DefaultDepth	24
```

Dir que estic amb un portàtil de 17" amb pantalla panoràmica

---


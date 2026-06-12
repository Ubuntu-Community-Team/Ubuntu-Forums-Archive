---
title: "[SOLVED] Fent pràctiques per donar d'alta un nou usuari"
date: 2007-08-14
forum: Catalan Team
---

### Post by ealbert on 2007-08-14
He entrat en Sistema  > administració >. usuaris i grups i he donat d'alta un nou usuari; una vegada comprovat que tot funcionava correctament, l'he suprimit i fins aquí tot correcte.
El problema a vingut després quan he volgut donar d'alta un nou usuari amb el mateix nom del suprimit,  hem deixa donar-lo d'alta i me'l accepta; fins hi tot en el menú hem deixa revisar tots el usuaris i les seves característiques, inclòs el nou;  però tan bon punt tanco la finestra del menú desapareix aquest usuari.
Suposo que en algun lloc del sistema  l'ordre de suprimir executada la primera vegada segueix estan en vigor per aquest nom; altes amb d'altres noms d'usuaris es poden fer correctament.
Hem podeu donar un cop de mà, 

Agraït,...

---

### Post by papapep on 2007-08-14
Per l'interfície gràfica no en tinc idea de com va, però si fas a un terminal:

```
sudo useradd -m nom_del_nou_usuari
```

(l'opció "-m" li diu que si no existeix el directori home de l'usuari te'l crei)

segur que et funciona de "perilles"

---

### Post by ealbert on 2007-08-16
les teves instruccions funcionen correctament, gràcies

---


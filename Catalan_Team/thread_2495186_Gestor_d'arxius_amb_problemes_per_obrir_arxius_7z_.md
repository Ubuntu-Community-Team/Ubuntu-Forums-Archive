---
title: "Gestor d'arxius amb problemes per obrir arxius 7z amb contrasenya i els noms xifrats"
date: 2024-02-10
forum: Catalan Team
---

### Post by Curial on 2024-02-10
Bon dia a tothom,

No fa gaire he instal·lat l'Ubuntu 23.10 i m'he trobat que quan intento obrir arxius comprimits en .7z que tenien protecció amb contrasenya i a la vegada el nom xifrat no els puc obrir o descomprimir amb el gestor d'arxius 43.0 de Gnome.
Quan els obro, no apareix el nom, cosa normal, però tampoc apareix el camp per introduir la contrasenya, si l'intento descomprimir em crea la carpeta sense res a dins.

He provat de descomprimir-lo des de la línia de comandes i ho he pogut fer sense problemes (7z e -p[COLOR=#ff0000]contrasenya[/COLOR] [COLOR=#0000ff]nomarxiu.7z[/COLOR] ).
També he provat de comprimir un arxiu amb contrasenya però sense xifrar el nom i tampoc he tingut problemes per descomprimir-lo.

No sé si em podrieu orientar,gràcies. ](*,)

Salut!!

---

### Post by wgarcia on 2024-02-11
Tens el paquet p7zip-full instal·lat?

```
sudo apt install p7zip-full
```

---

### Post by Curial on 2024-03-03
Gràcies wgarcia per la resposta.
Els paquets p7zip els tenia tots instal·lats, tot i això els he eliminat i tornat a instal·lar, però no he aconseguit res amb els gestor d'arxius.
Quan vaig tenir aquest problema al començament, vaig provar d'instal·lar altres aplicacions, una d'elles era Xarchiver però si no recordo malament
també em tenia problemes, avui després de desinstal·lar i tornar a instal·lar els paquets p7zip almenys em funciona el Xarchiver.
El que no entenc és per què al gestor d'arxius no ha passat el mateix.

---


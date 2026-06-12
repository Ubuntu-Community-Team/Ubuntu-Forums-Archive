---
title: "Cridar un recurs compartit de linux"
date: 2007-10-23
forum: Catalan Team
---

### Post by xoldy on 2007-10-23
bon dia, volia preguntar-vos com faig per veure des d'un ordinador amb windows un recurs compartit amb linux.

Ja he donat permisos per compartir la carpeta en linux. Ara com crido aquesta carpeta des d'un windows.

Moltes gràcies

---

### Post by papapep on 2007-10-23
Exactament igual que quan busques un recurs compartit d'un ordinador windows, vas al navegador de fitxer i dins xarxa busques, dins el grup de treball, l'ordinador que comparteix el recurs.

---

### Post by xoldy on 2007-10-23
Moltes gràcies Papapep.
Ho he provat, veig el nou grup de treball o domini, però per accedir-hi, em demana nom d'usuari i contransenya.
He provat amb la següent caligrafia. Usuari: XOLDY-PROVES\xoldy
i la meva contrasenya d'usuari de linux.
L'ordinador amb linux es diu XOLDY-PROVES.

No em connecta.
No és vital el tema. Però em faria gràcia poder compartir info en els dues direccions.

Salutacions

---

### Post by papapep on 2007-10-23
Doncs com que suposo que l'assistent de nom "Carpetes compartides" de fet el que fa és configurar el servidor Samba, fes un cop d'ull al que posa al fitxer /etc/samba/smb.conf a veure quins paràmetres té posats. En funció d'això, et demanarà un mètode d'autenticació o un altre i tindràs uns permisos o uns altres al recurs que hagis compartit.

Si estàs una mica bregat en anglès, veuràs que el mateix fitxer de configuració explica fil per randa què significa cada paràmetre i les diferents opcions que tens.

---

### Post by xoldy on 2007-10-23
Moltes gràcies ara m'hi poso i dic que tal.

---

### Post by CarlesOriol on 2007-10-23
Has creat usuaris amb

smbpasswd ?

---


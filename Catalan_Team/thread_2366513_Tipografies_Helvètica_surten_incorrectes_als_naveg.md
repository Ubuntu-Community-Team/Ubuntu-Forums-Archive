---
title: "Tipografies Helvètica surten incorrectes als navegadors"
date: 2017-07-18
forum: Catalan Team
---

### Post by adriarv on 2017-07-18
Hola,

fa un temps vaig possar moltes tipografies Helvètica a un lloc que em semblava que era l'equivalent al Fonts de Windows (la meva primera pregunta és: a ón estan ubicades les fonts de Ubuntu??). La questió es que des de aleshores, a Chrome i a Firefox em surten les lletres amb accents com a simbols raros (i moltes webs utilitzen Helvètica!). La meva segona pregunta és si ho puc arreglar sabent a ón estan les "Fonts dels navegadors" o millor reinstalar-los o què fer? Al libre office em surten correctes.

Moltes gràcies! :D

---

### Post by wgarcia on 2017-07-19
Els tipus de lletra a l'Ubuntu, quan es tracta de tipografies personals d'un usuari, s'han d'instal·lar al directory ".font" de la teva carpeta d'inici (és a dir /home/usuari). Un cop posades aquí s'ha d'executar l'ordre següent des d'una terminal:

```
fc-cache -f -v
```

Si el sistema et diu que no troba "fc-cache", prèviament s'ha d'instal·lar:

```
sudo apt-get install fontconfig
```

Si es vol instal·lar el tipus de lletra per a tot el sistema, es poden instal·lar a "/usr/local/share/fonts" o subdirectoris d'aquest directori. També s'ha d'executar l'ordre indicada a dalt. 

Per veure quins tipus de lletra estan instal·lats i on, una ordre útil és "fc-list", i com pot donar molta informació, potser convé paginar la sortida d'aquesta ordre amb "fc-list | less".

---

### Post by adriarv on 2017-07-19
Gràcies wgarcia. He trobat les fonts incorrectes a "/usr/local/share/fonts" i no em deixa borrar/moure (perquè no sóc el root), però des de el Font Manager les he pogut desactivar.

Per altra banda, a "/home/usuari" no existeix la carpeta ".font" , no sé per quina raó. Tinc Ubunto 16.04.

Una abraçada

---

### Post by wgarcia on 2017-07-19
Pots eliminar els tipus de lletra que no vulguis usant el "sudo" (amb compte). 

Potser en comptes de ".fonts" tens ".local/share/fonts".

---


---
title: "els mp3 no sonen"
date: 2011-06-20
forum: Catalan Team
---

### Post by josep-maria on 2011-06-20
Tinc l'ubuntu 11-04. No puc sentir els arxius de so (els mp3). Abans sí que podia. Quan obro un mp3, em diu: voleu cercar un connector adequat? Li dic que sí, el cerca, però em diu que no n'ha trobat cap.

---

### Post by wgarcia on 2011-06-21
Per tenir aquests còdecs propietaris, s'ha d'instal·lar el paquet ubuntu-restricted-extras:


sudo apt-get ubuntu-restricted-extras

---

### Post by josep-maria on 2011-06-21
Quan faig sudo apt-get ubuntu-restricted-extras, em diu 'operació no vàlida'.

---

### Post by wgarcia on 2011-06-22
Perdona, és:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by josep-maria on 2011-06-22
He fet el apt-get, fa una sèrie d'operacions amb paquets i surt una finestra que diu 'configuració del paquet ttf-mscorefonts-installer' 'end-user license agreement for microsoft software'. Faig clic on diu 'd'acord' però no fa res i ja no puc avançar més, haig de tancar la finestra.

---

### Post by wgarcia on 2011-06-23
Per a aquest diàleg has de fer servir el tabulador fins que el "D'acord" es posi vermell i aquí donar-li a l'intro perquè continuï.

---

### Post by josep-maria on 2011-06-27
Ara ja va bé. Gràcies.

---


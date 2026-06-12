---
title: "Ubuntu i Kubuntu"
date: 2007-02-25
forum: Catalan Team
---

### Post by iradigalesc on 2007-02-25
M'he instal·lar el grup de paquets del Kubuntu (kubuntu-desktop) dins de l'Ubuntu (que ja el tenia) i ara m'apareix l'usplash (pantalla d'inici i d'aturada de l'ordinaror) del Kubuntu. Jo voldria que tornés a aparèixer el de l'Ubuntu que és l'escriptori que més utilitzo.

Que caldria desinstal·lar paquet o configurar?

Gràcies!

---

### Post by cortsenc on 2007-02-25
molt més senzill que això

ves a **Sistema** > **Administració** >** Finestra d'entrada**

---

### Post by patrickfromspain on 2007-02-25
Cortsenc, aixo que dius no servira.. ja que tu et refereixes al GDM..

Per aixo de l'usplash proba a desinstalar els paquets relacionats amb usplash kubuntu (ara estic a debian, no ho poc comprobar) i despres, en una terminal: sudo dpkg-reconfigure linux-image-$(uname -r)

Espero que et serveixi.

---

### Post by cortsenc on 2007-02-25
vaja, ara he llegit millor el primer post :oops: 

Després me mirat aquesta documentació i he entès que preguntaven.
[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

---

### Post by jmaspons on 2007-02-25
Potser n'hi hauria prou amb què instal·lis el paquet ubuntu-desktop.

Salut.

---


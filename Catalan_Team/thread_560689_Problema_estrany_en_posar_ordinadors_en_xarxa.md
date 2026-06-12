---
title: "Problema estrany en posar ordinadors en xarxa"
date: 2007-09-26
forum: Catalan Team
---

### Post by migjorn on 2007-09-26
Hola a tothom!
Tots els ordinadors del meu centre escolar van amb Ubuntu, instal·lat per jo mateix.
Però els vull posar en xarxa i em passa el següent. Em poso a un dels ordinadors, i puc agafar coses de l'escriptori dels altres, però no puc desar les coses meves a l'escriptori dels altres. 
Té sentit?

Gràcies i salut!

---

### Post by pespin on 2007-09-26
Si no vaig errat suposo que és normal, serà una qüestió de permisos d'escriptura. :)

---

### Post by orestesmas on 2007-09-26
Doncs si, la configuració predeterminada d'ubuntu és que un usuari pot llegir els fitxers del directori de qualsevol altre usuari, però només pot escriure al seu propi directori. Si no fos així seria un descontrol total, com passa en windows (usuaris sense experiència escrivint en zones delicades del sistema, etc.). Pensa-t'ho una mica i ho veuràs més clar.

GNU/Linux és un sistema autènticament multiusuari, i en aquests entorns els permisos s'han de tenir en compte, encara que comporti una mica més de feina.

---

### Post by migjorn on 2007-10-01
Disculpeu-me de nou, però no em surto en això de posar 4 ordinadors ubuntu en xarxa.

Quin tipus de xarxa he de posar Samba o Unix?
Jo ho he fet amb Unix, i a través de 'compartir carpetes' a cadascun d'ells li he dit que comparteixi la carpeta anomenada 'compartida'. I, quan des de cada ordinador vas a 'llocs', 'xarxa', pots veure als altres però no veus la carpeta 'compartida'.

Algú em pot fer un cop de mà? Conegueu un bon tutorial sobre el tema?
Altrament, hi ha alguna manera de fer una carpeta on es puguin abocar arxius des de tots els ordinadors?

Moltíssimes gràcies, i disculpeu-me si ho he embolicat una mica...

---

### Post by CarlesOriol on 2007-10-01
Una solució fàcil i ràpida.

Insta&#320;la el ssh als ordinadors

**sudo apt-get install ssh**

Des de qualsevol finestra **nautilus** (gnome) d'un ordinador fas:

(Ctrl+L) Ubicació: **ssh://ip_del_altre** o **ssh://nomusuari@ip_del_altre**

Si ho fas en **kde** en comptes de ssh:// escrius** fish://**

---


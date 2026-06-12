---
title: "Virtual Box"
date: 2012-05-06
forum: Catalan Team
---

### Post by rosa d'abril on 2012-05-06
Hola,
Vaja, m'estic instal·lant la versió 12.04 i en entrar al fòrum veig que ja hi ha força incidències. Espero no penedir-me de no haver-me esperat unes setmanes més.
Però jo volia consultar una altra qüestió. L'altre dia em van ensenyar una Virtual Box corrent en W7 i em vaig fer molt bona impressió. Resulta que l'Ubuntu i el W7 corrien alhora sense interferir-se per res i podent canviar d'un sistema a l'altre amb un sol toc de ratolí. A més, un cop tancada, no en quedava ni rastre: el W7 no s'adonava que havia tingut un *alien* treballant a les seves entranyes. 
Total que estic pensant de baixar-me la Virtual box per a Ubuntu i instal·lar-m'hi el W7. Algú ho ha fet? M'ho recomaneu?
Salut!

---

### Post by wgarcia on 2012-05-07
Si tens prou memòria RAM i disc dur, sol ser la millor opció per tenir dos sistemes operatius (o més) al mateix ordinador. Molt millor que la doble arrencada, perquè com ben dius no s'ha d'anar tancant un sistema i obrint un altre. En particular amb els sistemes Windows, l'altre avantatge és que si t'entra un d'aquells virus devastadors que solen deixar-te sense res sols afecta al sistema virtual i no a tot a l'ordinador. 

Jo tinc més d'una màquina virtual (amb el virtualbox o algun altre programari creador de màquines virtuals pots tenir tantes com vulguis), això permet anar provant coses en diversos sistemes sense remenar el disc dur amb noves particions.

---

### Post by akyra on 2012-05-07
Estic d'acord amb en wgarcia.

Jo havia tingut problemes amb els dispositius USB, però pel demés funciona molt bé, és una bona solució.

Salutacions.

---

### Post by rosa d'abril on 2012-05-07
Ah, perfecte, gràcies pels consells. Doncs, res, me la baixaré i la instal·laré. Si tinc algun problement, ja us donaré la pallissa (he, he, he).
Gràcies

---

### Post by AlbertJB on 2012-05-08
Jo tenia dual-boot fa uns mesos i efectivament era un rotllo haver de tancar i tornar a obrir per canviar de SO. 

Vaig ampliar la memòria RAM a 8 GB (per a sistemes operatius de 64 bits paga molt la pena), i ara tinc com a host Ubuntu i com a guest Windows 7. Assigno 4GB a cada un i la mar de bé. Amb 4 GB la màquina s'alentia molt.

Salutacions

---

### Post by prostata on 2012-05-19
Aprofitant que el fil ja és obert us exposo el meu cas:

En el meu HD tinc una partició per windows xp i altra la que faig servir normalment per a Ubuntu.

El que vull es poder anar d'un al altre sense haver de reiniciar. Per això vaig instal·lar virtualbox, però no em surto amb ell, en crear la màquina virtual on  instal-lar el SO "convidat",  aquí em perdo, jo no tinc "convidats" jo tinc dos SO en el mateix HD i els vull córrer un o altre indistintament. No vull instal-lar res perquè ja els tinc instal·lats...

Com veieu no em surto...he mirat per google però evidentment totes les pàgines parlen sobre el mateix concepte que segur no he entès....¿un cop de mà em vindria molt bé... També he provat Wine, però aquest no obre tots els .exe, es dir clarament, uns sí d'altres no...

Salut

---

### Post by rosa d'abril on 2012-05-19
Jo no és que hi entengui gaire, però em penso que si vols tenir com a sistema amfitrió l'XP (amfitrió vol dir el sistema operatiu de partida, vaja) has d'instal·lar l'Ubuntu en la màquina virtual i per a això necessites la ISO de l'Ubuntu que et descarregues fàcilment d'aquí: 
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)
Un cop tens istal·lada la VB li cliques a Nova i vas seguint l'auxiliar. En algun moment et demanarà on tens magatzemada la ISO i ja està.

---

### Post by wgarcia on 2012-05-19
@prostata: necessites alguna imatge instal·lable (un CD o una imatge d'un CD) per poder instal·lar el sistema operatiu dins de la màquina virtual. És a dir, un cop creada la màquina virtual i configurada (memòria, disc dur, ports USB, etc) has de dir-li d'on arrencar el primer cop, i des d'aquí s'instal·larà. 

Per això necessites doncs una imatge instal·lable del sistema operatiu que vols posar a la màquina virtual. Això amb Linux és trivial perquè sempre et pots baixar aquesta imatge per a qualsevol distribució. Amb Microsoft Windows no és tan trivial, perquè ara tot i que et cobren per la llicència del sistema operatiu no et donen una imatge instal·lable, sino que hi ha una partició al disc on es pot recuperar la instal·lació si li passa alguna cosa. No sé si es pot crear una imatge instal·lable des d'aquestes particions de recuperació, això suposo que ho explicaran en algun fòrum d'usuaris d'aquest sistema operatiu.

---


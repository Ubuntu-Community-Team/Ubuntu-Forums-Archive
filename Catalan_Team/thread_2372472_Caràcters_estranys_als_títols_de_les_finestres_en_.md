---
title: "Caràcters estranys als títols de les finestres en Català"
date: 2017-09-25
forum: Catalan Team
---

### Post by tafol on 2017-09-25
Hola, he comprat un equip amb UBUNTU instal·lat i quan el pose en Català, instal·le el suport d'idioma, etc. Surten caràcters estranys als títols de les finestres, on hauria de sortir un caràcter accentuat. Adjunte captura.
Té solució?
Salutacions

---

### Post by wgarcia on 2017-09-25
Pots enganxar el que et surt quan obres una terminal i entres:

```
locale -a
```

?

---

### Post by tafol on 2017-09-25
Sí. El resultat és:
[FONT=courier new]C
ca_AD.utf8
ca_ES.utf8
ca_ES.utf8@valencia
ca_FR.utf8
ca_IT.utf8
C.UTF-8
en_AG
en_AG.utf8
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_IN.utf8
en_NG
en_NG.utf8
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZM
en_ZM.utf8
en_ZW.utf8
es_AR.utf8
es_BO.utf8
es_CL.utf8
es_CO.utf8
es_CR.utf8
es_CU
es_CU.utf8
es_DO.utf8
es_EC.utf8
es_ES.utf8
es_GT.utf8
es_HN.utf8
es_MX.utf8
es_NI.utf8
es_PA.utf8
es_PE.utf8
es_PR.utf8
es_PY.utf8
es_SV.utf8
es_US.utf8
es_UY.utf8
es_VE.utf8
POSIX[/FONT]

---

### Post by wgarcia on 2017-09-26
Això es veu correcte, saps quin escriptori estàs fent servir (l'escriptori per defecte Unity o algun altre)? Per la captura de pantalla que has enviat sembla l'Unity.

---

### Post by tafol on 2017-09-27
Sí. L'escriptori és UNITY

---

### Post by wgarcia on 2017-09-28
He trobat un informe d'error:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1599516](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1599516)

 on diuen que una aplicació anomenada "bleachbit" pot ser el causant d'això. Per mirar si la tens instal·lada, pots donar la següent ordre des d'una terminal:
```
 apt-cache policy bleachbit
```

---

### Post by tafol on 2017-09-28
Aquest és el resultat:
[FONT=courier new]bleachbit:
  Insta&#320;lat: (cap)
  Candidat:  1.10-1
  Taula de versió:
     1.10-1 500
        500 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
        500 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial/universe i386 Packages
[/FONT]

---

### Post by wgarcia on 2017-09-29
Doncs no sembla el teu problema, perquè aquest paquest no està instal·lat. 

Ara tornaria a Paràmetres de sistema -> Suport d'idoma, a veure si el suport d'idioma està instal·lat completament. Si no ho està, t'ho dirà en clicar a aquesta opció.

---

### Post by tafol on 2017-09-30
Hola.
Moltes gràcies per l'ajuda. Al final he solucionat el problema, tot i que crec que es tracta d'un *bug*. Us conte què vaig fer:
Vaig entrar en un terminal i vaig escriure [FONT=courier new]sudo dpkg-reconfigure locales[/FONT]. Vaig marcar els *locales* per a català i castellà i vaig reiniciar. El problema seguia igual. Després vaig tornar a fer el mateix procés però vaig canviar el *locale* predeterminat del sistema a [FONT=courier new]ca_ES.UTF-8[/FONT] (el tenia en [FONT=courier new]ca_ES.UTF-8@valencia[/FONT]). Amb això i, després de reiniciar, es va solucionar el problema. Pense que deu ser un *bug* del *locale* per a valencià. De moment, a mi em serveix la solució adoptada. Torne a agrair les respostes. Salutacions

---

### Post by wgarcia on 2017-09-30
Perfecte, intentaré reproduir el problema en una màquina virtual, i si es reprodueix, ho reportaré com un error.

---


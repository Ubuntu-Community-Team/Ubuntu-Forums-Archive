---
title: "Libre Office no s'obre a Ubuntu 12.10"
date: 2012-11-04
forum: Catalan Team
---

### Post by Omit7 on 2012-11-04
Molt bones companys,

Avui he intentat obrir un fitxer PDF amb el writer de Libre Office. He pogut treballar amb ell sense problemes. El cas es que ara intento tornar a accedir a d'altres aplicacions de Libre Office i totes fan el mateix. Apareix la pantalla d'inici amb la barra i abans de començar a moure's la barra, es tanca i no arranca. Em passa amb totes igual i no ser que fer.

Alguna suggerencia?

Gràcies,

---

### Post by wgarcia on 2012-11-05
Prova d'obrir una terminal i iniciar LibreOffice entrant el nom directament i prement "intro", a veure si dóna algun missatge d'error:

```
libreoffice
```

---

### Post by Omit7 on 2012-11-05
Efectivament dona un error.

UNO Exception: InvalidRegistryException: file:///usr/lib/libreoffice/program/../share/extensions/pdfimport/components.rdb: duplicate <implementation name="com.sun.star.comp.documents.HybridPDFImport">
terminate called after throwing an instance of 'com::sun::star::uno::DeploymentException'

---

### Post by wgarcia on 2012-11-06
Mirant aquest error ha sortit això:

[http://ask.libreoffice.org/question/4161/libreoffice-fails-to-start-after-update-uno/](http://ask.libreoffice.org/question/4161/libreoffice-fails-to-start-after-update-uno/)

Aquí suggereixen esborrar el directori:

.config/libreoffice/3/user/extensions/

de la teva carpeta d'inici. Jo més que esborrar-la li canviaria el nom a .config/libreoffice/3/usr/extensions.vell i si després que el sistema recrea aquesta carpeta no es veuen més conseqüències l'acabaria esborrant. Potser si tens extensions instal·lades s'hagin de tornar a instal·lar.

---

### Post by Omit7 on 2012-11-06
Solucionat!!! Efectivament era el que m'has dit. Després de fer això tots el menus sortien en anglés pero amb un simple;

sudo apt-get install libreoffice libreoffice-l10n-ca

tot ha tornat al seu lloc.

Moltes gracies,

---


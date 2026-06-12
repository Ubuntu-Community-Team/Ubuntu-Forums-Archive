---
title: "Arxiu ods danyat"
date: 2009-11-06
forum: Catalan Team
---

### Post by pesolnegre on 2009-11-06
Algú sap d'alguna aplicació que em pugui servir per a obrir un arxiu .ods danyat? O bé alguna forma per poder intentar extreure'n les dades que es puguin?

Gràcies

---

### Post by papapep on 2009-11-06
Canvia-li l'extensió d'.ods a .zip i descomprimeix-lo, els od* són fitxers de text (en format XML) comprimits. Allà dins ho tens tot. Una altra cosa és la feina que et porti aprofitar-ho.
A veure si tens sort i la capçalera del fitxer no està cascada i el pots obrir.

---

### Post by pesolnegre on 2009-11-06
Gràcies per la info Papapep

Suposo que això és el certificat de mort de la capçalera:

[/media/disk/home/oriol/Escriptori/Monedes/Arxius/Inventari monedes.zip]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/disk/home/oriol/Escriptori/Monedes/Arxius/Inventari monedes.zip or
          /media/disk/home/oriol/Escriptori/Monedes/Arxius/Inventari monedes.zip.zip, and cannot find /media/disk/home/oriol/Escriptori/Monedes/Arxius/Inventari monedes.zip.ZIP, period.


No hi ha més sistemes, ni que siguin esotèrics?

---

### Post by papapep on 2009-11-06
Podries provar a veure si l'opció que té el paquet zip per a reparar arxius comprimits et funciona.

Primer fes una còpia de seguretat de l'original:

```
cp nomDelFitxer.zip nomDelFitxerBackup.zip
```

i després prova amb:

```
zip -F nomDelFitxer.zip
```

i a veure si ara el pots obrir des del navegador de fitxers.

---


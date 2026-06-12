---
title: "Password pàgina WEB"
date: 2007-10-27
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2007-10-27
Bones.
Algú sap si es pot protegir l'accès a una pàgina WEB amb contrasenya.
O be, protegir amb contrasenya alguns dels documents penjats a la web.
Personalment, edito amb NVU. Però estic obert a qualsevol altre eina.
Moltes gracies.

---

### Post by papapep on 2007-10-27
No sé quin nivell de coneixement tens de servidors web i programació, però això que preguntes no és fàcil de respondre, per la varietat de respostes que se't poden donar.

Si es pot fer, evidentment. 

La pregunta és: fins quin nivell de protecció vols arribar? Amb quin servidor, Apache2?? Serà només un fitxer, o molts? Hi haurà diferents nivells d'accés?, diferents usuaris? o serà tot molt més simple...?

:-)

---

### Post by jerec on 2007-10-27
El mes usual es fer servir un fitxer ".htacces"

El que fa es anar a buscar un fitxer on hi als usuaris i els passwords que tindran acces a entrar a veure la pagina. l'has de posar al direcotri on tens la pagina o pagines que vols protegir amb contrasenya.

Te aquesta estructura:

Fitxer .htaccess
```

AuthType Basic
AuthName Acces
AuthUserFile /srv/www/claus/ClausAccess

<Limit GET>
require valid-user
</Limit>

```

Despres has de fer el fitxer de claus, en el exemple "ClausAccess" i es troba al directori que apunta el .htacces.

Quedaria aixi
```

usuari1:4dED/jwEr3TRFicss
usuari2:3safdfRE/34SFdff

```

Aquest fitxer es genera amb l'ordre "htpasswd" (man htpasswd i veuras com va)

Busca a can Google mes informacio i ja veuras que no es pas complicat. L'altre cosa es configurar el teu servidor web amb encriptacio SSL, HTTPS, que tambe ho pots trobar en el manual del teu servidor web.

---

### Post by Miquel Ubuntero on 2007-10-27
En resposta a Papapep, voldria una coseta sencilleta. Ja tinc una WEB oberta a tot-hom. Ara m'agradaria posar un link a una altre WEB només amb acces amb contrasenya.
He mirat la resposta d'en jerec. tinc 2 dubtes. quina extensió a de tindre el fitxer "ClausAccess"? El contingut d'aquest fitxer, on diu usuari1 i usuari2, el format es potser "usuari1:nomusuari/contrasenya"?
moltes gracies a tots dos.

---

### Post by papapep on 2007-10-27
Si l'altre pàgina web també la controles tu, el fitxer de contrassenyes tindrà el nom que tu vulguis. L'únic requisit és que el nom del fitxer coincideixi amb el que tens dins el .htaccess. A Linux les extensions no tenen cap mena d'importància.

El format del fitxer és: 

```
nomusuari:contrassenya
```

Sempre que el servidor web sigui l'Apache o Apache2. Amb altres servidors no funciona així, clar.

---


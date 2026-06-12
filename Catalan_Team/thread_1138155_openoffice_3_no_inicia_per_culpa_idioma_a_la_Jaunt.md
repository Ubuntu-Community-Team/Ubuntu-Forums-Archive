---
title: "openoffice 3 no inicia per culpa idioma a la Jaunty"
date: 2009-04-26
forum: Catalan Team
---

### Post by trinkus on 2009-04-26
Hola,

He actualitzat a la Jaunty i ara l'Openoffice no s'engega, apareix la pantalla següent:

[ATTACH]111135[/ATTACH]

US deixo el resultat del locale

locale

LANG=ca_ES.UTF-8
LC_CTYPE="ca_ES.UTF-8"
LC_NUMERIC="ca_ES.UTF-8"
LC_TIME="ca_ES.UTF-8"
LC_COLLATE="ca_ES.UTF-8"
LC_MONETARY="ca_ES.UTF-8"
LC_MESSAGES="ca_ES.UTF-8"
LC_PAPER="ca_ES.UTF-8"
LC_NAME="ca_ES.UTF-8"
LC_ADDRESS="ca_ES.UTF-8"
LC_TELEPHONE="ca_ES.UTF-8"
LC_MEASUREMENT="ca_ES.UTF-8"
LC_IDENTIFICATION="ca_ES.UTF-8"
LC_ALL=

Tambe he provat de reinstal·lar els paquets de l'openoffice i de configurar des del suport d'idioma pero res de res. Ara no puc fer anar fitxers d'Openoffice.... i em comença a ser urgent...

merci per si algu pot ajudar

---

### Post by trinkus on 2009-04-26
Ja he provat de reinstalar moltissims paquests relacionats amb openofffice i amb l'idioma pero res de res.... no puc obrir res.

Penjo el que surt si executo des de la consola aveure si algu em pot ajudar perque la cosa es critica.... hi ha manera d'arreglar-ho o fer servir el 2.4 ????

[ATTACH]111154[/ATTACH]

Ajuda siusplau.

Gracies

---

### Post by papapep on 2009-04-26
Prova dues coses.

1) Refer els permisos dels fitxers de configuració de l'OO:

```
chmod -R 755 /home/elteusuari/.openoffice.org2/user
```

si això no funciona, 

2) prova a crear un nou perfil d'usuari de l'OO:

```
mv /home/elteuusuari/.openoffice.org2/user /home/elteuusuari/.openoffice.org2/user.backup
```

obre l'OpenOffice, et tornarà a demanar les dades com si fos just després d'instal·lar, i a veure si funciona.

---

### Post by trinkus on 2009-04-26
Ostres Papapep.... no se que fariem sense tu. Resumeixo:

1a opcio no ha funcionat

2a opcio n'he fet una adaptacio perque com ho has posat no anava. M'explico:
Al meu usuari hi havia una carpeta openoffice.org2 i una .openoffice.org amb una subcarpeta 3. Resulta que aquesta no tenia els permisos adequats de manera que li he aplicat els permisos de la 2a opcio i he traslladat els arxius de la .org2 a la .org .... de moment oli en un llum i tot sembla funcionar.

Moltes gracies

SOLVED!

---


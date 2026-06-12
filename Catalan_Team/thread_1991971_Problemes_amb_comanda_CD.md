---
title: "Problemes amb comanda CD"
date: 2012-05-31
forum: Catalan Team
---

### Post by davit83 on 2012-05-31
Bon dia

Soc nou al fòrum i he fet la migracio completa (bueno, casi) a Ubuntu després d'estar casi un any a mitges.

La qüestió, en la consola la comanda cd no hem permet pujar més enllà del directori /home. No se si te quelcom a veure el fet que vaig instal·lar l'ubuntu en dues particions lógiques: Una per al sistema operatiu (montada a /) i una per als fitxers (montada a /home). 

M0aniria molt bé poguer accedir amb la consola als meus fitxers personals, més que res per si s'ha de treballar amb instal·lacions.tar no se fer-ho des de l'entorn gràfic i si ha d'accedir es a través de la consola.

Us deixo el missatge que hem dona

david@david-desktop:~$ cd /home
david@david-desktop:/home$ cd /david
bash: cd: /david: El fitxer o directori no existeix
david@david-desktop:/home$ 

Com veieu no hi ha cap problema per accedir a home però si a david (la meva carpeta personal)

Si algú hem pogues dir quina es la manera d'accedir des de la consola li agrairia molt.

Gracies per endavant

---

### Post by wgarcia on 2012-05-31
La segona instrucció hauria de ser:

```
cd david
```

o directament

```
cd /home/david
```

tot i que quan obres la terminal o consola ja hauria de començar directament a aquest directori. Pots també donar la instrucció:

```
pwd
```

i et mostrarà en quin directori està.

Quan al teu missatge, un cop estàs a "/home" has d'entrar "david" sense la barra endavant. La barra indica el directori arrel, i per tant si fas "cd /david" com poses en el teu missatge el sistema pensa que "david" és una carpeta que està directament a l'arrel.

---

### Post by davit83 on 2012-06-01
Solucionat hi acabo d'entrar (se'm fa una mica complicada la navegació per consola però ja n'aprendré)

Moltes Gracies

---


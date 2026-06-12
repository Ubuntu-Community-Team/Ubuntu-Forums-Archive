---
title: "desinstal.lar CELETANIA"
date: 2009-03-22
forum: Catalan Team
---

### Post by venusfenix on 2009-03-22
buenas,

tinc un AMD 64x2 amb ubuntu 8.10.

vaig instalar el joc CELETANIA, que en vaig descarregar desde la pagina web amb un paquet .deb

ara el vull desinstallar, pero no trobo el paquet per desinstalar-lo.
he fet dpkg -L programa i no surt al llistat.

per altre banda, al directori hi ha un fitxer anomena't unistall-celetania.sh

pero no se com procedir.

gracies,

---

### Post by oriolsbd on 2009-03-22
Hola.

Des del Synaptic tampoc no el veus?

Per poder executar aquesta shell, has d'anar al directori on és des d'un Terminal i executar:
```
./uninstall-celetania.sh
```

Si et diu que necessites permisos d'administrador, hauràs de fer:
```
sudo ./uninstall-celetania.sh
```

Ull, no sé si aquesta shell desinstal·la el programa. Pel nom sembla que és així (i segurament així és), però no ho podem saber segur. Espera a veure si algú més dóna alguna pista. Si no, prova d'executar-lo com t'he dit.

Salut!

---

### Post by RainCT on 2009-03-22
És «dpkg -l», en mínuscula. Prova això:

```
dpkg -l | grep -i celetania
```

---

### Post by venusfenix on 2009-03-22
buenas, 

opcions provades:

a) dpkg -l | grep -i celetania

no fa res

b) en el synaptic no surt

c) ./uninstall-celetania.sh

ho ha fet. ha funcionat. queden uns fitxers, pero els he esborrat a l'antiga. Ja no surt al menu d'aplicacions i els fitxers grossos estan elimina'ts. perfecte


moltes gracies

---


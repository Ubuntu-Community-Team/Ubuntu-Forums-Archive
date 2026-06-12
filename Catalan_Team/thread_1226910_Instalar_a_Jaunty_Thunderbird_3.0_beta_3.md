---
title: "Instalar a Jaunty Thunderbird 3.0 beta 3"
date: 2009-07-30
forum: Catalan Team
---

### Post by iSoc on 2009-07-30
Hola, bon dia a tothom. Mireu m'agradaria posar thunderbird 3 per substituir evolution, ja que estic acostumat al xp i porta el thunderbird però no hi ha manera de saber com puc instal·lar me baixat l'archiu thunderbird-3.0b3 pero exactament no se el que e de fer ja que soc novell amb el ubuntu i millor preguntar per no carregarme res. Un salut i si em podeu fer un cop de ma gracies..:(

---

### Post by papapep on 2009-07-30
Recordeu, és molt important per evitar molts maldecaps, que això és Ubuntu, i el funcionament, normalment per a millor, no és el del sistema operatiu dominant. Un simple:

```
sudo aptitude install thunderbird-3.0 thunderbird-3.0-gnome-support
```

hauria d'instal·lar-te el necessari.

Salut.

---

### Post by pauelmaco on 2009-07-30
Aquí hi ha una explicació clara (encara que en anglès) del que s'ha de fer:

- [http://ubuntuforums.org/showthread.php?t=1076624](http://ubuntuforums.org/showthread.php?t=1076624)

Sort!

---

### Post by iSoc on 2009-07-30
Gracies gent vaig a provar a veure que enterc. Un salut.

---

### Post by iSoc on 2009-07-30
Hola de nou després de provar instal·lar de les dues maneres la d'en **PAPAPEP** no ma funcionat em diu això.

```
abuelete@abuelete-laptop:~$ sudo aptitude install thunderbird-3.0 thunderbird-3.0-gnome-support
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Escribiendo información de estado extendido... Hecho
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con "thunderbird-3.0"
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con "thunderbird-3.0-gnome-support"
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con "thunderbird-3.0"
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con "thunderbird-3.0-gnome-support"

```La segona opció del **Pauelmaco** funciona correctament pero, ara pregunto com o puc fer per crear un acces directe per poder obrir el thunderbird des de l 'escriptori i no tindre de posar cada vegada thunderbird3 -P a Terminal. ?? Un salut i gracies de nou.

P.D. Llestos ja ho e aconseguit. Gracies per la vostra atenció. **[SOLVED]**.

---

### Post by pauelmaco on 2009-07-30
Fés click dret a l'escriptori, -Nou -llançadora (o una cosa així). Et surtirà una finestreta de propietats. On hi posa "Ordre:" o "Comanda:", posa-hi: "thunderbird3 -P" (O el que posis a la consola per iniciar-lo) i accepta.

---


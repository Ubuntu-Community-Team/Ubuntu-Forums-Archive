---
title: "Carpeta del wine"
date: 2011-10-15
forum: Catalan Team
---

### Post by docevil on 2011-10-15
Bo,soc nou a l'ubuntu y m'agradaria saber si puc posar la carpeta del wine en un disc dur extern, perque el portatil te poc d'espai y voldria instalar programes al disc dur amb el wine desde ubuntu.
Gracies per anticipat.

---

### Post by CarlesOriol on 2011-10-15
Pots fer-ho ràpidament sense canviar cap configuració movent la carpeta .wine al disc extern i creant un enllaç simbolic (amb el nautilus o amb un ln -s)

---

### Post by docevil on 2011-10-15
He intentat fero amb el mv i cuant  le fet, ma donat error de problemes al crear un enllaç simbolic perque, nose si pot ser perque es una carpeta oculta, no puc vorela amb l'interfaz tinc que vorela amb la terminal. Nose si pots dirme una manera, he triat amb sudo i segueix igual.

---

### Post by CarlesOriol on 2011-10-16
escriu que has fet

---

### Post by docevil on 2011-10-16
sudo mv /home/elmeusuari/.wine /media/Elements(Elements es el disc dur), al final he conseguit moureu, pero a l'hora de obrir un programa del wine em deia que no tenia permis, vaig cambiar la carpeta y el propietari del .wine del disc dur, y em seguia diguent lo mateix, he tinc que borrar el wine per complet y tornar a instarlo, aixina que hara estic al mateix punt que a l'inici

---


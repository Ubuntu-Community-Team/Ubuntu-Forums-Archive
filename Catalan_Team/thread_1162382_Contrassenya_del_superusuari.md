---
title: "Contrassenya del superusuari"
date: 2009-05-17
forum: Catalan Team
---

### Post by Daerun on 2009-05-17
Hi ha alguna manera de configurar la contrasenya del superusuari perquè ens la torni a demanar cada vegada que volguem fer alguna operació com a root, en comptes de valer durant x temps cada cop que la introduïm?

---

### Post by orestesmas on 2009-05-17
Bàsicament has d'afegir una línia al fitxer /etc/sudoers que digui així:

```

Defaults timestamp_timeout=0

```

Si ja hi ha una línia que comenci amb "Defaults", aleshores simplement cal afegir el timestamp... darrere, després d'una coma.

**Nota Important:** Els cànons manen que el fitxer /etc/sudoers s'editi amb
```

sudo visudo

```

o bé amb 
```

sudo nano -w /etc/sudoers

```

---


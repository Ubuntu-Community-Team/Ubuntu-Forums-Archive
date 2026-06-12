---
title: "GoogleEarth 5"
date: 2009-02-04
forum: Catalan Team
---

### Post by MiquelBLL on 2009-02-04
Hola, ahir vaig instal.lar la nova versio de Googleearth i al iniciarla al moment que acaba de carregar-se es torna a tancar. Tinc AMD64 i l´Intrepid. A algu li passa el mateix?

---

### Post by tanreb20 on 2009-02-04
a la carpeta d google-eaqrth:
```

sudo ln -s /usr/lib/libcrypto.so libcrypto.so.0.9.8
```

---

### Post by MiquelBLL on 2009-02-04
Gracies, primer tampoc funcionaba, pero despres he trobat que tambe es tenia que eliminar de la carpeta google-earth  el fitxer libcrypto.so.0.9.8. , ara funciona perfectament. Salutacions.

---


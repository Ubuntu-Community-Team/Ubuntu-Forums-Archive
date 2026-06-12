---
title: "Permisos amb sbackup"
date: 2009-01-28
forum: Catalan Team
---

### Post by trinkus on 2009-01-28
Hola,

El programa sbackup em fa les copies de seguretat amb permisos de lectura nomes per al root (exactament no se perque?), es pot configurar per a que no ho faci aixi?
D'altra banda les copies que tinc, els puc canviar la propietat i/o l'acces de lectura rapidament sense haver de fer-ho fitxer per fitxer? Com es fa per fe-ho a tot un directori i subdirectoris fills....

Merci...

---

### Post by oriolsbd on 2009-01-28
No conec el programa sbackup, però si et deixa els fitxers amb usuari "root" deu ser perquè s'executa amb "root" (o sigui, amb "sudo"). Potser ja és correcte, però no ho sé.

Per canviar l'usuari de tots els fitxers d'un directori, has d'anar al directori i fer:
```
sudo chown usuari:grup *
```

Si, a més, vols que la comanda també sigui recursiva pels subdirectoris:
```
sudo chown -R usuari:grup *
```

Per afegir permisos de lectura a tothom als fitxers d'un directori has d'anar al directori i fer:
```
chmod ga+r *
```

Si a més vols que la comanda sigui recursiva en subdirectoris:
```
chmod -R ga+r *
```

Si els fitxers són de "root", la comanda chmod l'hauràs d'executar amb "sudo" davant.

Salut!

---


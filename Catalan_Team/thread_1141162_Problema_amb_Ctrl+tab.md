---
title: "Problema amb Ctrl+tab"
date: 2009-04-28
forum: Catalan Team
---

### Post by prostata on 2009-04-28
Bon dia, tinc un altre ordinador amb la jaunty també. Aquest porta una GeForce 6200 AGP. Dins controlador de hardware te activat el recomenat, es dir Nvidia versió 180, el problema que em dona és el següent:

Quan premo les tecles Ctrl+Alt+Back space l'ordinador no respon, i haig de fer-lo amb sortir>tancar sessió.

Un cop faig tot el procediment del loguin, arrenca normalment però triga gaire bé un minut, o més, en apareixer l'escriptori....

Segur que deu ser un problema o del video, o bé del xorg o del xconfig, però n sé com poder donarl-li sol-lució.

Salutacions

---

### Post by trinkus on 2009-04-28
Jo em sembla haver llegit en algun lloc que la Jaunty ha inhabilitat aquesta combinacio de tecles pero que es pot rehabilitar, el que no se es com... en algun lloc oficial o algun bloc segur que ho posa...

Espero que serveixi...

---

### Post by prostata on 2009-04-28
> **trinkus said:**
> Jo em sembla haver llegit en algun lloc que la Jaunty ha inhabilitat aquesta combinacio de tecles pero que es pot rehabilitar, el que no se es com... en algun lloc oficial o algun bloc segur que ho posa...

Espero que serveixi...


Aquí està la sol-lució:

sudo aptitude install dontzap -y

i desprès

sudo dontzap -d


per més info...

[http://electrobuntu.blogspot.com/](http://electrobuntu.blogspot.com/)

Moltes gràcies pel teu interès

Salutacions

---


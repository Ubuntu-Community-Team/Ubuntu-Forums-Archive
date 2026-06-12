---
title: "error al engegar ubuntu: mountall has errors:/home"
date: 2011-04-07
forum: Catalan Team
---

### Post by pserra on 2011-04-07
hola,
ahir al voler engegar el portàtil, se'm va parar al tenir la bateria a 0, avui al engegar em surt aquest error a la darrera línia, hi ha alguna manera senzilla de arreglar-ho??
Merci

---

### Post by wgarcia on 2011-04-07
Has de córrer un "fsck" perquè verifiqui errors al disc, però ho has de fer sense que la partició /home estigui muntada. El millor és entrar amb un mitjà Live (CD o usb), obrir una terminal i fer "sudo fsck /home" si aquesta és la teva partició.

---

### Post by pserra on 2011-04-10
Merci wgarcia,
solucionat.... des de el live semblava que no era possible...però al provar-lo d'arrancar quan surt l'error, la darrera línia és la de root, li he posat   la comanda que m'has posat abans i després de moltes confirmacions ja torno a tenir el meu 'estimat' ubuntu remix......
Gràcies

---


---
title: "Modificar fstab desde live?"
date: 2010-09-03
forum: Catalan Team
---

### Post by pserra on 2010-09-03
Hola,
 ahir mirant de muntar totes les particions al engegar el ubuntu, n'hi ha una que tinc com a ext4 que se'm resistia, vaig voler fer una modificació (posant la UUID) a fstab a veure si la muntava bé..  i ara quan arrenco el ubuntu no em carrega i em 'peta'...

el cas es que vull modificar-ho desde el live cd-> nautilus i em diu que no puc desar els canvis...
si quan em genera l'error premo esc accedeixo al arxiu amb el nano (com a root) però quan  guardo em diu que no tinc permnisos...
fa estona que estic mirant de solventa-lo i no hi ha manera..
alguna suggerència??
merci.

---

### Post by wgarcia on 2010-09-03
Has provat de muntar primer el disc on tens el fstab i editar-lo des d'aquest punt? Per exemple si el fstab està a /dev/sda5:

mkdir /mnt/tmp

mount /dev/sda5 /mnt/tmp

nano /mnt/tmp/etc/fstab

etc.

---

### Post by pserra on 2010-09-06
> **wgarcia said:**
> Has provat de muntar primer el disc on tens el fstab i editar-lo des d'aquest punt? Per exemple si el fstab està a /dev/sda5:

mkdir /mnt/tmp

mount /dev/sda5 /mnt/tmp

nano /mnt/tmp/etc/fstab

etc.

hola,
Merci, problema arreglat,
aquests dies provaba de fer-ho amb el sudo.... i no guardava...
he vist que amb el sudo su   si que realitzava els canvis....
Merci una altre vegada
Merci.

---


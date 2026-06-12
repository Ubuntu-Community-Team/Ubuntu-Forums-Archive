---
title: "Com puc editar el grub?"
date: 2007-03-29
forum: Catalan Team
---

### Post by sianeu on 2007-03-29
Les actualitzacions del kernel van deixant dues línies cada una al grub, fins que ja es fa massa incòmode per buscar el windows.

He provat de editar-lo: senyalo la entrada, premo **e**, i borro totes les linees premen **d** a cada una. Però quan torno al principal (**esc**), torna a ser-hi. Per tant no es deu de fer així.

Cóm es fa?

Salut

---

### Post by jmaspons on 2007-03-29
Hola

Has d'editar el fitxer /boot/grub/menu.lst per modificar les entrades del grub

Suposo que el què passa és que se't van instal·lant noves versions del nucli. Pots esborrar les velles eliminant els paquets kernel-image* de les versions de linux que ja no utilitzis.

Salut!

---

### Post by sianeu on 2007-03-29
Fet. Moltes gracies.

Si volgués esborrar els fitxers (no se el tamany que tenen), on hauria d'anar?.

PD: a /boot. Em faig creus de lo ruc que puc ser a vegades.... Però son molt petits, no cal.

Salut

---

### Post by CarlesOriol on 2007-03-30
amb el synaptic.

---

### Post by sianeu on 2007-03-30
Esborrar els fitxers de boot amb el synaptic?  Cóm?

---

### Post by CarlesOriol on 2007-03-30
Desinstala els kernel-image* que no siguin la darrera versió.

---

### Post by sianeu on 2007-03-30
M'ho apunto, gracies.

---

### Post by orestesmas on 2007-03-31
Els kernel-image* són antics, de la versió 2.4 del nucli. Ara són els linux-image*

Un lapsus que a mi em passa constantment...

---

### Post by CarlesOriol on 2007-03-31
uops......... perdó!

---


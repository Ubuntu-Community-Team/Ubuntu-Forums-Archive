---
title: "Clauer idcat (de nou)"
date: 2009-11-15
forum: Catalan Team
---

### Post by bratac on 2009-11-15
Bones,

em vaig instal·lar el clauer idcat fa temps i tot funcionava. Després (al cap de bastants mesos) el volia tornar a utilitzar i l'ordinador no me'l reconeix. Si vaig al firefox / certificats/els meus certificats no hi és.

Vaig pensar que el més fàcil seria instal·lar-lo de nou però en fer-ho dóna aquest error quan faig sudo make install :

clos is already running, try doing clos restart
make[3]: *** [install-exec-hook] Error 1
make[3]: Leaving directory `/home/bratac/tmp/ClauerLinux-3.0.0/clos'
make[2]: *** [install-exec-am] Error 2
make[2]: Leaving directory `/home/bratac/tmp/ClauerLinux-3.0.0/clos'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/bratac/tmp/ClauerLinux-3.0.0/clos'
make: *** [install-recursive] Error 1

Em podeu ajudar a arreglar-lo?

Gràcies!

---

### Post by phishie on 2009-11-15
> **bratac said:**
> Bones,

em vaig instal·lar el clauer idcat fa temps i tot funcionava. Després (al cap de bastants mesos) el volia tornar a utilitzar i l'ordinador no me'l reconeix. Si vaig al firefox / certificats/els meus certificats no hi és.

Vaig pensar que el més fàcil seria instal·lar-lo de nou però en fer-ho dóna aquest error quan faig sudo make install :

clos is already running, try doing clos restart
make[3]: *** [install-exec-hook] Error 1
make[3]: Leaving directory `/home/bratac/tmp/ClauerLinux-3.0.0/clos'
make[2]: *** [install-exec-am] Error 2
make[2]: Leaving directory `/home/bratac/tmp/ClauerLinux-3.0.0/clos'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/bratac/tmp/ClauerLinux-3.0.0/clos'
make: *** [install-recursive] Error 1

Em podeu ajudar a arreglar-lo?

Gràcies!

Hola, ha intentat posar fi al procés abans de 'make install'?

---

### Post by bratac on 2009-11-15
Com poso fi al procès? :D Si faig #exit em tanca la terminal...

gràcies!

---

### Post by phishie on 2009-11-16
> **bratac said:**
> Com poso fi al procès? :D Si faig #exit em tanca la terminal...

gràcies!

En realitat no parlen el seu idioma. Estic fent això sobre la base de traductor Google, però vaig a tractar.

La forma més fàcil és anar a: Sistema -> Administració -> monitor del sistema i feu clic a la pestanya 'Processos'. Seleccioneu el procés per posar fi a partir d'allí.

No estic segur que el procés que ha de matar però.

---


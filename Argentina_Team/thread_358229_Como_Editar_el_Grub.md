---
title: "Como Editar el Grub"
date: 2007-02-10
forum: Argentina Team
---

### Post by Darth Trix on 2007-02-10
Después de instalar la última versión del Kernel el grub se descontrolo, ahora tengo** ocho ** opciones de inicio:
-11 Generic
-11 Generic (recovery)
-10-861
-10-861 (recovery)
-10 Generic
-10 Generic (recovey)
memtest+86
Windows XP

¿Como hago para sacar alguna de estas opciones antes de que la lista del grub se empiece a parecer al código penal?

---

### Post by spg76 on 2007-02-10
Yo deinstalado las versiones viejas del kernel desde Synaptic.
Tenes que buscar las que digan linux-image-**2.6.15-27-386**. La parte en negrita es la versión del kernel que queres desinstalar. Esto te borrar esa versión del kernel de tu sistema y te saca la entrada en GRUB.
Siempre es conveniente tener la versión más nueva  y dejar una anterior como respaldo.

---

### Post by Darth Trix on 2007-02-10
Gracias, por ahora estoy bien, pero si tengo una nueva actulizacion la lista se va a hacer muy larga.

---


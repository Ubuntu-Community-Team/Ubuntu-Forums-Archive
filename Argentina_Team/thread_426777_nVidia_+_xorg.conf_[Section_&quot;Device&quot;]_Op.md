---
title: "nVidia + xorg.conf [Section &quot;Device&quot;] Option..."
date: 2007-04-28
forum: Argentina Team
---

### Post by sebas.rhcp on 2007-04-28
Alguien sabe cuales son TODAS las "Option" posibles en xorg 7.2.0 con driver nvidia?

No encuentro una guia que reuna los "tweaks" para xorg.conf hay poca info si alguien conoce gracias...

Aporto las mias...

    Option "RenderAccel" "true" (Aceleracion del escritorio por HW, no tengo manera de comprobarlo)
    Option "HWCursor" "true" (Aceleracion del cursor por HW, tampoco tengo manera de comprobar)
    Option "DPMS" "true" (esta opcion me la activo el driver de nvidia con "sudo nvidia-xconfig" esta relacionado con el refresco del monitor)

:)

---

### Post by el_itur on 2007-04-29
man nvidiaxconfig...
Está en inglés pero ahí está todo.

De cualquier manera me parece que es al ****. Yo tengo una fx5200 con los últimos drivers (9755 creo que es nvidia-glx-new lo bajé de los repositorios) y anda más que bien, con los tunings clásicos:

Sacar el splash horrible. Activar la extesion composite y addrgbwithcomposite.

Yo haría eso nada más. A parte el xorg.conf va a estar despreciado en 5 meses.

---

### Post by sebas.rhcp on 2007-04-29
Ah o sea que ni me caliento de aca a 5 meses?:???: 

No sabia lo del manual jeje

---

### Post by lavaramano on 2007-04-30
> **sebas.rhcp said:**
> Ah o sea que ni me caliento de aca a 5 meses?:???: 

No sabia lo del manual jeje

no es para crear discordia, pero usas *ubuntu... cada 6 meses casi todo se vuelve obsoleto :lolflag:

---

### Post by el_itur on 2007-04-30
yo no probé pero en los foros en inglés hay gente que probó borrando el xorg.conf y tuvo buenos resultados. en teoría tiene que configurarse al vuelo.

Y sí, casi todo se vuelve obsoleto. Pero se actualiza :) .

De cualquier manera yo sigo con mi eclipse de hace un par de años :P

---


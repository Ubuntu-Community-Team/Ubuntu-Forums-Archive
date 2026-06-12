---
title: "Hardy, asus m2n-mx se Timer not conected to IO-APIC"
date: 2008-05-14
forum: Argentina Team
---

### Post by lega on 2008-05-14
Me compre un pc nueva ayer, con un con un Athlon 64 X2 4200+ y 1gb de ram, ni bien inicie el live cd de Hardy ( le instale la versión de 32 bits) me salto este error 
> Timer not conected to IO-APIC
kernel panic - non syncing:_ IO.APIC + timer dowsn't work ! try using noapic kernel parameter reinicié le puse una opcion noapic con F4 y el cd inicio normalmente, al terminar la instalación y reiniciar, me saltó el error nuevamente, entonces entré al setup del bios y deshabilité IOAPIC , reinicié y no hubo ningún problema mas.
La pregunta es si me perjudica en algo deshabilitar esa opción?, no sé ni que es ni para que sirve, encontré esto:
> APIC: Es un acrónimo de **A**dvanced **P**rogrammable **I**nterrupt **C**ontroller. Se divide en 2 partes: el APIC local y el I/O APIC.
El APIC local se usa en sistemas uno o mas procesadores y es usado por el sistema operativo para manipular threads. En sistemas con SMP, su usa para enviar interrupciones a otro procesador.



El I/O APIC se usa solo en sistemas SMP. Se usa para enviar varias interrupciones a varios CPU's simultáneamente, si se desactiva las interrupciones solo le legan al procesador que botea, y este es el encargado de repartir el IRQ.

Pero es como si estuviera escrito en chino para mi :)esta bien que haya deshabilitado eso o hay una opción mejor?

Gracias, saludos

---

### Post by guillermolisi on 2008-05-14
Como lo interpreto te diria que si usas un kernel con funcionalidad SMP el rendimiento de la maquina sin IOAPIC se vera disminuido frente al que podrias lograr pero con IOAPIC.

Si usas un kernel que no es SMP, daria lo mismo ya que con o sin IOAPIC no se aprovecharian sus funciones de distribuir carga entre CPUs (veria todo como una sola CPU).

Lo que no se a ciencia cierta es si ese procesador es SMP o solo doble nucleo (como el dual core de Intel, que simularia un SMP).

---

### Post by valucha on 2008-05-14
[COLOR="DarkOrchid"]Te digo algo desde la práctica:
Me compré una compu el año pasado y vengo usando desde edgy->feisty->gutsy->hardy la opción "noapic" osea, tengo deshabilitado el apic y el i/o apic. 
Va muy rapido (es similar a la tuya un giga de ram, amdx2 4200,etc...) y no tengo ningun desperfecto técnico de hardware ni tampoco tildadas ni nada de eso...

Así que dale pa' delante :)


OJalá te deje más tranquilo, saludos.[/COLOR]

---

### Post by lega on 2008-05-15
Gracias a los dos por la respuesta

Saludos

---


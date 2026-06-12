---
title: "[SOLVED] Problema de teclado (como &amp;quot;colgado&amp;quot;)"
date: 2008-02-04
forum: Argentina Team
---

### Post by euzkoarima on 2008-02-04
Les cuento, acabo de descubrir que de vez en cuando "se me cuelga el teclado" (yo le venía echando la culpa a otras cosas), lo que ocurre es "como si" alguna de las teclas modificadoras quedase presionada, en particular la tecla <ctrl>.
La solución para zafar es apretar un par de veces la tecla <ctrl> si con eso no pasa sigo con <alt> y bueno, al final "descuelga".
Problema del teclado no creo que sea, tiene 2 semana de uso (genius slim star).

Alguna idea, sugerencia?
Sirve postear alguna configuración del sistema para dar mas datos a los que sepan??

Gracias,

---

### Post by Hei Ku on 2008-02-04
si pones "dmesg" en la consola te dice algo?

---

### Post by User21 on 2008-02-05
Probaste el teclado en otra máquina o en otros SOs como para descartar una falla de fabrica ??

---

### Post by faktorqm on 2008-02-05
a mi lo unico q se me ocurrio es que capaz tenes alguna hotkey con el control que te bloquea el teclado o algo parecido. por ejemplo, cada vez que juego algun juego que no bloquea el teclado, apreto control + alt y me cambia de escritorio y me saca del juego :S y despues me cuesta volver.... fijate eso. salu2!

---

### Post by Mister X on 2008-02-05
No descartes la falla de hardware, a mi me pasa lo mismo en mi notebook, muy de vez en cuando una tecla queda como si estuviera presionada (no fisicamente) y se soluciona cuando la apreto de nuevo. Y me pasa en Linux tanto como en guindous

---

### Post by euzkoarima on 2008-02-06
Primero que nada, disculpen mi tardanza en contestar, es que ayer no me conecte a internet en todo el dia. Aprovecho a contestar a todos. Con "dmesg" en la consola me tira tanta info que no se que buscar, pero como el teclado y mouse son ps2, copio aca lo que encontré referido a eso (pero si hace falta posteo todo)

> [    1.492000] input: Macintosh mouse button emulation as /class/input/input0
[    1.492000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.492000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.492000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.492000] mice: PS/2 mouse device common for all mice
...
[   12.428000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
...
[    1.520000] input: AT Translated Set 2 keyboard as /class/input/input1

La otra, probar en otra pc, en un rato lo hago y les cuento.

Gracias

---

### Post by euzkoarima on 2008-02-06
Confirmo que es problema del teclado!!! lo puse en una pc que tiene winxp y la colgó mal (al menos en ubuntu había como remarla, era más tolerante a teclados con mal funcionamiento).

Hasta hace unas semanas mi puesto de trabajo era una mac y no estaba acostumbrado a problemas de hard, menos de algo simple como un teclado, eso mezclado con que todavía no tengo tanta experiencia con el linux me llevo a suponer que le había chingado en alguna configuración.

Gracias a todos los que contestaron.

---


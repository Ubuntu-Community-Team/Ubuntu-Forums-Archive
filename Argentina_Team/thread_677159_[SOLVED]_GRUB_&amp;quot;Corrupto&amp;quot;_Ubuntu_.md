---
title: "[SOLVED] GRUB &amp;quot;Corrupto&amp;quot; Ubuntu no inicia"
date: 2008-01-24
forum: Argentina Team
---

### Post by atari130xe on 2008-01-24
Tengo 3 particiones
hda1 XP (proximo a volar)
hda2 Elive Gem
hda3 Gutsy 
tuve problemas con Elive y lo reinstalé y oh!, cuando inicia Grub y elijo Ubuntu me da error de particion (hda3) no recuerdo el error exacto, (lo postearia si es necesario, es una cadena de caracteres y nros bastante larga) y queda en mi home/desktop el cursor. que debería hacer? claro está,:) como me quedó el "desafio" de hacer funcionar el driver oficinal Nvidia puede que formatee todo y a empezar de cero.

---

### Post by sebaxxxtian on 2008-01-24
a mi me pasa q el grub no me deja elegir el sistema operativo (tengo instalado en otro hd un w98se) y se queda en la primera opcion.

---

### Post by tzulberti on 2008-01-25
atari130xe:
No entiendo algo. Despues de haber instalado el Elive, el grub te aparece ahi elegis ubuntu, y llega hasta una parte de donde no podes seguir? Si es asi eso es porque cuando instalastes el Elive modificastes alguna particion (o formateastes). Para solucionar ese problema, te aconsejo poner un # (numeral) en la particion en la que hayas instalado el Elive.

sebaxxxtian:
Tu teclado o mouse es inalambrico?

---

### Post by sebaxxxtian on 2008-01-25
mi mouse es de los comunes

mi teclado  no es inalambrico pero es usb

---

### Post by tzulberti on 2008-01-25
> **sebaxxxtian said:**
> 
mi teclado  no es inalambrico pero es usb

Leyendo en el foro, encontre que es un problema del Bios. Para solucionarlo tenes que activar la opcion "USB Legacy" dentro del BIOS. Sin embargo, creo que para esto por lo menos vas a necesitar poner un teclado PS2.

NOTA: no estoy totalmente seguro de que eso lo solucione ya que no tengo un teclado usb.

---

### Post by atari130xe on 2008-01-25
> **tzulberti said:**
> atari130xe:
No entiendo algo. Despues de haber instalado el Elive, el grub te aparece ahi elegis ubuntu, y llega hasta una parte de donde no podes seguir? Si es asi eso es porque cuando instalastes el Elive modificastes alguna particion (o formateastes). Para solucionar ese problema, te aconsejo poner un # (numeral) en la particion en la que hayas instalado el Elive.

sebaxxxtian:
Tu teclado o mouse es inalambrico?

Sip, lo que ocurrió es algo así, formateé la partición de Elive pero lo raro es que lo que no arrancaba era la partición de Ubuntu, de todas maneras esta mañana, "borré el HD" eliminando finalmente el XP de mi Compu (ya puedo decir que soy usuario de Linux 100 %, reparticioné nuevamente:

Esta vez como ya estoy "más canchero" :lolflag: creé particiones (Con Gparted Live una excelente herramienta) de esta manera:

"/" para Elive y una "/" para Gutsy
"/home" para Elive y una "/home" (extendida) para Gutsy
una única particion "/swap" para las 2

Lo que me pone contento es haber quitado de mi PC el XP, es raro pero aprendí a manejar y configurar mis cosas en Ubuntu y siento que no necesito más Windows.

Mañana termino de instalar Gutsy y como tengo dial up y las actualizaciones pesan demasiado (unos 220 MB) pienso crear un script o un listado de los paquetes y bajarlos en mi laburo con banda ancha. 

gracias! :)

PD: a ver si esta bendita vez puedo instalarle los driver oficiales de Nvidia jejeje

---

### Post by niko_3100 on 2008-01-26
Viste, yo desde que me baje un par de juegos de Sonic estoy usando bastante XP  :( me da mucha bronca porque lo peor es que solo lo levanto para jugar a los jueguitos ni me interesa internet ni nada, pero me da bronca que no se puedan instalar en ubuntu con wine o que haya juegos nativos de sonic para linux pero bue... yo xp lo tengo exclusivamente para eso.

---

### Post by Mauro22 on 2008-01-26
Sonic?? No trabaja con un emulador bajo DOS?

Probaste con DOSBOX o DOSEMU ??


:guitar:

---


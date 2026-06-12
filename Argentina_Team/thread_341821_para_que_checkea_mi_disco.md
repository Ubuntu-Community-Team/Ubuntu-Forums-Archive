---
title: "para que checkea mi disco?"
date: 2007-01-19
forum: Argentina Team
---

### Post by Nemesis Teufel on 2007-01-19
Hoy inicie mi Ubuntu como cualquier otro dia y derepente me comenzo a checkear el disco hdb6 que corresponde al swap. Me dijo que habia sido montado 30 veces sin checkearlo por eso lo hacia. En 4' termino de hacerlo y mi Ubuntu corrio como siempre.

No me quejo, solo quiero preguntar el motivo de eso. ¿Cómo es que mi swap no se monto 30 veces? ¿Es decir que durante 30 veces(sesiones) mi Ubuntu no utilizo mi swap? ¿Es otro de mis "maravillosos" bugs que se arreglan solos?

---

### Post by BlackHero on 2007-01-19
cacha esta hayer cuando prendo mi laptop entro a xubuntu y me figuraba mi plugins medidor de ram utilizando 700 mb ram cuando por defecto al iniciar carga 68 o 70 y algo empese a putear y a largar killes para ver si algo era que estaba consumiendo mucho termine largandole kill a Xorg crasheo loggeo automaticamente y seguia igual por ultimo reinicie y listo SE ARREGLO SOLO pero no entendia por que me consumia tanta ram :S otro bug tipo nemesis :P

---

### Post by Pajblito on 2007-01-19
> **Nemesis Teufel said:**
> Hoy inicie mi Ubuntu como cualquier otro dia y derepente me comenzo a checkear el disco hdb6 que corresponde al swap. Me dijo que **habia sido montado 30 veces sin checkearlo** por eso lo hacia. En 4' termino de hacerlo y mi Ubuntu corrio como siempre.

No me quejo, solo quiero preguntar el motivo de eso. ¿Cómo es que mi swap no se monto 30 veces? ¿Es decir que durante 30 veces(sesiones) mi Ubuntu no utilizo mi swap? ¿Es otro de mis "maravillosos" bugs que se arreglan solos?

A mi me dijo lo mismo anoche, creo q el truco esta en q **lo monto 30 veces** y lo chekea por mantenimiento.
Tu swat se monto 30 veces, solo q no se chekeo. Te acordas del scandisk? bueno, supongo q algo parecido.

---

### Post by spg76 on 2007-01-19
No es un bug, es una función del sistema que cuando la partición se monta una cierta cantidad de veces (por defecto 30 veces) lo chequea automaticamente en busca de errores.
Creo que se puede modificar desde la cantidad de veces hasta desactivar está función editando algún archivo de configuración, pero la verdad que no sé mucho de eso.

---

### Post by BlackHero on 2007-01-19
para mi es un bug por que sino nos abria pasado a todos :S y ami no me paso

---

### Post by Hex_Mandos on 2007-01-19
A mi me pasa cada 30 booteos. Es normal, pero un poco molesto... ahora el disco se me cagó igual, sin que el chequeo me haya dicho nada.

---

### Post by beuno on 2007-01-19
> **BlackHero said:**
> para mi es un bug por que sino nos abria pasado a todos :S y ami no me paso

Es standard cada 30 veces que montas el sistema de archivos (generalmente, en el booteo).

---

### Post by Tinchio on 2007-01-19
> **BlackHero said:**
> cacha esta hayer cuando prendo mi laptop entro a xubuntu y me figuraba mi plugins medidor de ram utilizando 700 mb ram cuando por defecto al iniciar carga 68 o 70 y algo empese a putear y a largar killes para ver si algo era que estaba consumiendo mucho termine largandole kill a Xorg crasheo loggeo automaticamente y seguia igual por ultimo reinicie y listo SE ARREGLO SOLO pero no entendia por que me consumia tanta ram :S otro bug tipo nemesis :P

perdon que me meta, yo no soy ningun experto pero simplemente queria comentar algo que llego a mi no se como, creo q lo vi en un canal de IRC, comento:
Segun tengo entendido esta es una pregunta tipica de ex usuarios de windows, la memoria en gnu/linux se administra de un forma totalmente distinta, la idea no es que se va "llenando" de a poco, sino que es como que se "llena de una" y como que va "cachenado" los programas en la memoria para poder cargarlos mas rapido; o algo asi, no soy buen profesor :P
En fin esto es lo que tengo entendido en el tema de memoria en gnu/linux si dije cualquier gansada ignorenlo. Saludos

---

### Post by MeduZa on 2007-01-19
> **Tinchio said:**
> perdon que me meta, yo no soy ningun experto pero simplemente queria comentar algo que llego a mi no se como, creo q lo vi en un canal de IRC, comento:
Segun tengo entendido esta es una pregunta tipica de ex usuarios de windows, la memoria en gnu/linux se administra de un forma totalmente distinta, la idea no es que se va "llenando" de a poco, sino que es como que se "llena de una" y como que va "cachenado" los programas en la memoria para poder cargarlos mas rapido; o algo asi, no soy buen profesor :P
En fin esto es lo que tengo entendido en el tema de memoria en gnu/linux si dije cualquier gansada ignorenlo. Saludos

es simple

Linux administra/usa la memoria de una manera muy distinta a la que estamos acostumbrado a verlo en wintendo.
Linux no usa la swap de disco mientras haya memoria ram disponible,
eso lo pueden ver en recursos en el monitor de sistema. (ej: 400 mb ram usandos 0 de swap) haciendo esto el gana una gran velocidad ya que el paginado/swapiado a disco es muy lento (para una pc) y si lo puede hacer en ram mejor. El otro dia estaba leyendo algo de esto y es lo que mas o menos entendi (puedo estar equivocado)
Wintendo no usa la memoria de esta manera y siempre necesita tener la swap para intercambios y esas cosas que el hace q no se saben para que son :roll: 

Saludos

PD: foto del screen de un ejemplo en mi pc
PD2: creo que lo que se esta usando de ram como intercambio (swap) es lo que esta en verde clarito

---

### Post by ubuntu27 on 2007-01-19
Es normal, es como ScanDisk en Windows. 
Solo que esto es automatico y revisa cada 30 que montas el disco (que reinicies la comp)/ :)

Si, como saben en GNU/Linux todo puedes personalizarlo, configurarlo como queires.
No se que archivo tienes que modificar para cambiar cuando cuanto timepo quieres que revise el disco...

Cunado lo encuentre les aviso.

---

### Post by Nemesis Teufel on 2007-01-19
> otro bug tipo nemesis
jajaja, voy a patentarlo!

bueno.. mejor asi si es algo normal, yo cuando veia el check del disco pensaba: uh.. otra vez a mi la puta madre.. 
No hace falta cambiarlo, realmente no me jode.. ahora.. la pregunta del millon.. para que caracoles sirve?

---


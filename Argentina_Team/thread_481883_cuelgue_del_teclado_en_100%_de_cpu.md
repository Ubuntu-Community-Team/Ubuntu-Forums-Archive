---
title: "cuelgue del teclado en 100% de cpu"
date: 2007-06-23
forum: Argentina Team
---

### Post by Kantier on 2007-06-23
la cosa es así:

cuando se queda en 100% el cpu y estoy con una tecla de tipo "meta" (alt, shift, ctrl, win, etc.) apretada, se me **** el uso de teclado en la sesión de X actual (tengo que cerrarla y abrir una nueva).

¿a alguien le pasó algo parecido antes? ¿tienen idea de cómo solucionar el tema?

---

### Post by juanman on 2007-06-23
Yo tengo un problema del mismo estilo: en opera (32bits corriendo en 64) cuando presiono alguna tecla latina (enie, acentos, etc), se me va la cpu al 100 por 5 seg maso y luego me escribe un cuadradito blanco, q cuando lo borro primero aparece un ? y si presiono backspace de nuevo ahi si se borra...
O sea no puedo escribir en latino...
Alguna idea?

---

### Post by guillermolisi on 2007-06-23
Juanma

Por como describis el problema parece que busca el font dentro del set de caracteres que estas usando para representar el simbolo y como no lo encuentra te pone el cuadradito.

Cuando hace la busqueda deben ser esos segundos en que la CPU se va al tope.

Sobre lo que le pasa a Kantier, ni idea.

---

### Post by juanman on 2007-06-23
Aha... Pero como cambio el set de caracteres? Esto solo me pasa al escribir. En las paginas se ven bien los caracteres... Y para escribir estoy usando Arial, la cambie a courier y otras q se q tiene los caracteres latinos pero pasa lo mismo... No encuentro ningun lugar donde se pueda cambiar la codificacion o algo asi... Y en el swiftfox q tambien es de 32 bits, anda bien...

Lo raro es que instale el mismo paquete en ubuntu edgy de 32 bits y anda bien...
No entiendo naa...

---

### Post by guillermolisi on 2007-06-23
Juanman

Edita el /etc/default/locale.
Con el vi (en consola) seria:

```

sudo vi /etc/default/locale 

```

y coloca el "locale character set" (UTF-8, ISO-XXXX, etc) que quieras.

---

### Post by clasificado on 2007-06-24
En mi pecera tengo 

```
$ cat /etc/default/locale
LANG="es_ES.UTF-8"
```

y me anda jóya, ¿que tenes vos juanman?

Por otra parte, ¿es solo con el Opera? por ahi tenga que ver algo la forma en la que hiciste la emulación de arquitectura 32 sobre la de 64

Clasificado

---

### Post by juanman on 2007-06-24
Ya lo probe y no funca. Reinicie y sigue sin funcionar. 
Puedo pegar las eñes pero no las puedo escribir con el teclado... Es raro... Y probe con los demas caracteres del teclado, y andan bien, o sea, esta usando la disposicion de teclas del sistema pero no puedo escribir los caracteres latinos...
Toy viendo si puedo hacer un script de opera... Tanto kilombo pa una *******...:(

---

### Post by Baroh on 2007-06-24
Te pasa lo mismo cuando intentas escribir caracteres como "á", "ó", etc.?

---

### Post by juanman on 2007-06-24
Sisi, con todos los caracteres latinos: acentos, la c con cedilla q usan los portugueses, tambien el o con superindice (para abreviar primero, segundo, etc), enie... Andan $%&&#8364; | [+*

Respondiendo al post anterior q no habia leido: Solo me pasa en Opera. Y swiftfox que esta de la misma forma emulado anda bien... El locale lo tenia igual q vos. Despues le cambie mil cosas y sigue sin andar... Me parece q el problema no viene por ahi... Es algo del opera pero no se q... Busque por google y no encontre a nadie con el mismo problema...

Gracias a todos los q respondieron

---

### Post by faktorqm on 2007-06-27
Hola, en sistema -> preferencias -> teclado, ficha distribuciones, que tenes activado y que no?

yo te cuento, tenia teclado en ingles, lo cambie a espaniol, y me tiro error el xkb y nunca mas pude escribir ningun simbolo. ya te habras dado cuenta que la enie no la puedo escribir, ni nada con la tecla alt. asi que todo mal. fijate si tenes eso activado, capaz lo cambias a espaol o latinoamericano y todo bien. o capaz lo tenes bien y no sirve de nada. salu2!

---


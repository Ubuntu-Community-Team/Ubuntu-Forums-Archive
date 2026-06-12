---
title: "[SOLVED] Problema para instalar Java"
date: 2007-10-20
forum: Argentina Team
---

### Post by Vero1 on 2007-10-20
Hola a todos,

Una vez mas con problemas...

Resulta que quiero instalar Java. Descargué el paquete de la fuente original en formato .rpm. El sistema no reconoce el formato.

En Google encontré una especie de guía para instalar este tipo de archivo pero, aun siguiendo las indicaciones, sigue sin reconocer.

Quisiera saber si a alguien le pasó lo mismo y cómo lo solucionó.

Aclaro que instalé alien pero tampoco funciona.

Desde ya gracias por los comentarios.

saludos:)

---

### Post by Hei Ku on 2007-10-20
tendrias que usar alien, q sirve para convertir archivos .rpm a .deb

Pero lo primero que te preguntaría es para que lo bajaste en rpm, si el java viene en los repositorios?

---

### Post by Vero1 on 2007-10-20
Hola Hei Ku:)

Es cierto está en Synaptic y lo tengo marcado pero como Mozzilla me está enviando cada vez un cartel amarillo hablando de plugins que faltan, pues se me ocurrió descargar Java de Sun directamente.

Ahora me fijo si hay algo mas que tenga que instalar para solventar el problema.

Alien ya lo instalé pero no me aceptó el comando para convertir .rpm en .deb.

Bueno, si sigo con el problema, te aviso.

Gracias una vez mas.

saludos

---

### Post by sajnox on 2007-10-20
Por que no nos posteas el error que te tira la consola con el comando alien

Saludos,

---

### Post by tzulberti on 2007-10-20
No entiendo porque te lo bajastes si esta en los repositorios:
apt-cache search sun java

---

### Post by ariel on 2007-10-21
si estas usando 7.10, instalar java es refacil. Anda a applications>add/remove y busca "ubuntu restricted extras" (asegurate que Show = All available apps).

esto te agreaga Sun Java 6, el plugin de mozilla, y ademas codecs &etc.


> **Vero1 said:**
> Hola a todos,

Una vez mas con problemas...

Resulta que quiero instalar Java. Descargué el paquete de la fuente original en formato .rpm. El sistema no reconoce el formato.

En Google encontré una especie de guía para instalar este tipo de archivo pero, aun siguiendo las indicaciones, sigue sin reconocer.

Quisiera saber si a alguien le pasó lo mismo y cómo lo solucionó.

Aclaro que instalé alien pero tampoco funciona.

Desde ya gracias por los comentarios.

saludos:)

---

### Post by Vero1 on 2007-10-21
Hola Ariel,

No, estoy con Feisty todavía. Gracias por contestar.

tzulberti,

Porque no sabía que estaban:(

sajnox: ésto es lo que me tira:

 sudo alien -i /home/veronica/jre-6u3-linux-i586-rpm.bin
Unknown type of package, /home/veronica/jre-6u3-linux-i586-rpm.bin.

La orden la saqué de una página de Internet que se llama Páginas Dispersas.

saludos

---

### Post by facundocorradini on 2007-10-21
**Te estás complicando innecesariamente.**

Los archivos RPM son de Red Hat Package Manager, algo similar a lo que son los archivos DEB, pero para las distros basadas en Red Hat en vez de Debian.

Lo que te hace falta a vos es el plugin de Java para Firefox. 

**Lo mejor (como_ siempre_) es que lo instales de los repositorios**

Para ello, desde añadir programas o desde synaptic busca Java Plugin y te aparecerá el Sun Java 5 Plugin. doble click, aplicar, y listo! 


saludos y espero que te haya sido util.

---

### Post by Vero1 on 2007-10-22
Te aseguro que no tengo ninguna gana de complicarme, lo que pasa es que todavía no estoy acostumbrada a ver primero en los Repositorios.
Vengo de mas de 10 años en Windows...

Gracias por tus indicaciones y ya me estoy bajando el plugin.

saludos

---

### Post by facundocorradini on 2007-10-22
Ok, me alegra ser de ayuda.

:D


Tratá de acostumbrarte:
 bajar programas de internet es siempre la **últim**a opción. 

En los repositorios tenés software** estable** y **confiable**, cosa que no puedes obtener desde la web (una de las razones por las que son tan comunes los virus en windows)

y podés bajarlo desde aplicaciones -->añadir o quitar, o desde synaptic.

---

### Post by Vero1 on 2007-10-22
Trataré y cada día me acostumbro un poco mas:)

Aparte me olvidé de agradecerte la aclaración sobre .rpm ya que parecía que se estaba hablando de revoluciones por minuto:popcorn:

saludos

---

### Post by tzulberti on 2007-10-23
Los repositorios de ubuntu tienen cerca de 22.000 paquetes... asique es dificil que no encuentres lo que estas buscando...

---

### Post by Vero1 on 2007-10-23
Como le dije a facundo, tengo que acostumbrarme a mirar primero en los Repositorios.
De a poco lo voy logrando:)

saludos

---


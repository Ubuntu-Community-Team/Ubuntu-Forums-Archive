---
title: "Pregunta facil...o no"
date: 2007-07-23
forum: Argentina Team
---

### Post by jpmorelli on 2007-07-23
Simple, si yo tengo Ubuntu instalado, consume mas recursos que tambien cargue kde aparte del Gnome ( siempre hablando de los servicios estandard cargados ) y sin contar el espacio en disco o es lo mismo ?

---

### Post by Salpiche on 2007-07-24
por lo general KDE usa mas recursos que Gnome, en cuanto a espacio no te puedo decir

---

### Post by User21 on 2007-07-24
La logica (o al menos la mia) indica que el solo hecho de tener aplicaciones de KDE instaladas, usando Gnome como escritorio, rekiere librerias adicionales propias de KDE, ke deben ser instaladas, y ejecutadas al inicio, en caso de ke kerramos ejecutar esos programas de KDE. Estas librerias o demonios en el inicio, consumen recursos, si. Obviamente, tambien rekiere mas espacio en disco. 
Uso Konversation y Klipper en Gnome, y hasta noto la diferencia entre programas nativos de Gnome. 

Todo esto, desde mi poca experiencia , basada en el uso de casi 4 meses.

---

### Post by kowal on 2007-07-24
[quote=Salpiche]por lo general KDE usa mas recursos que Gnome, en cuanto a espacio no te puedo decir[/quote]

En que te basás para afirmar eso? o es sólo una impresión?..

Acá hay un benchmark de hace un tiempito que comparan el consumo de memoria entre KDE, Gnome, XFCE, etc. (en inglés):

[http://ktown.kde.org/~seli/memory/desktop_benchmark.html](http://ktown.kde.org/~seli/memory/desktop_benchmark.html)


[quote=jmorelli]Simple, si yo tengo Ubuntu instalado, consume mas recursos que tambien cargue kde aparte del Gnome ( siempre hablando de los servicios estandard cargados ) y sin contar el espacio en disco o es lo mismo ?[/quote]

No entendí bien.. te referís a instalar o a ejecutar los dos a la vez?

---

### Post by jpmorelli on 2007-07-24
Si claro, obviamente si instalo los dos voy a ocupar mas espacio en disco, a lo que me refería es a si arranca con mas cosas cargadas en memoria o hay más demonios corriendo  al inicio, etc.
Puede haber dos teorías : 
1 que cargue lo mismo independientemente de cuantas aplicaciones y/o entornos de escritorio tenga instalado ya que el arranque de Ubuntu/Kubuntu corra los mismos procesos.

2 que cargue por decir un ejemplo, el sistema de sonido de Gnome y el de Kde, el cache de evolution y el de Kmail, el precacheo de nautilus y el de konqueror, etc.

---

### Post by Hei Ku on 2007-07-25
si tenes ubuntu, con algunas aplicaciones kde instaladas, lo que sucede es que las librerias para las aplicaciones kde se van a cargar cuando inicies esa aplicacion. El resultado es que las aplicaciones kde van a tardar mas en arrancar, y van a consumir mas memoria que una nativa de gnome, porq tiene q cargar librerias que las aplicaciones de gnome no necesitan.
Al menos esto es lo que siempre escuche sobre como funcionaba el utilizar aplicaciones no nativas.
El xubuntu da una pista sobre esto cuando te consulta que librerias cargar, si gnome o kde.

---

### Post by Salpiche on 2007-07-29
> **kowal said:**
> En que te basás para afirmar eso? o es sólo una impresión?..
en que uso los dos y siempre encuentro mucha mucha diferencia entre los dos, cuando mi maquina esta usando 20% de recursos en Gnome y cuando cambio a KDE usa 30%. Especialmente si estas usando una maquina vieja con recursos limitados.

> **kowal said:**
> Acá hay un benchmark de hace un tiempito que comparan el consumo de memoria entre KDE, Gnome, XFCE, etc. (en inglés):

[http://ktown.kde.org/~seli/memory/desktop_benchmark.html](http://ktown.kde.org/~seli/memory/desktop_benchmark.html)
Interesante! no es lo que yo he visto en mis maquinas



> **kowal said:**
> No entendí bien.. te referís a instalar o a ejecutar los dos a la vez?

---

### Post by Benji86 on 2007-07-30
Me parece que aca entra la vieja discucion de GNOME mas simple, KDE no.
Te puedo decir por como tengo mi maquina (KDE 3.5.6) que me esta consumiendo menos como la tengo ahora que Ubuntu base.

---


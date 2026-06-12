---
title: "[SOLVED] No puedo jugar en Yahoo Juegos"
date: 2007-12-27
forum: Argentina Team
---

### Post by margori on 2007-12-27
Estimados amigos:

Pues como lo dice el titulo, no puedo jugar a nada en el servicio de juegos de yahoo. La verdad me gusta jugar al poker ahí.

Uso firefox 2.0.0.11 y tengo instalado JavaRE 6.

No es de vida o muerte pero si me pueden dar un dato, mejor.

Gracias.

---

### Post by User21 on 2007-12-27
Yo si puedo jugar a los juegos de Yahoo, con Firefox 2.0.0.11 y los paquetes sun-java6-bin , sun-java-jre , sun-java6-plugin y java-common . Fijate en tu synaptic si te falta alguno de esos, y estate seguro de tener Firefox cerrado al momento de instalarlos. Espero os sirva! 

Suerte!

---

### Post by margori on 2008-01-04
Encontre la solucion. Me faltaba el paquete sun-java6-fonts. Lo supe viendo  [esta pagina]("http://mundogeek.net/archivos/2007/06/11/instalar-el-plugin-java-para-firefox-en-ubuntu/").

Gracias.

---

### Post by margori on 2008-01-06
Pense que el problema estaba solucionado, pero no fue asi.

Lo que me sucedia es que entraba a Yahoo! Juegos, entraba a la sala de poker, estaba un corto tiempo, y luego me aparecia el error de Java plugin no instalado.

Acabo de descubrir el problema real, la maquina virtual java (java_vm) entraba en conflicto con [Cocoa]("http://www.complang.tuwien.ac.at/cacaojvm/"). Lo desintale, resetee el navegador, y anduvo.

Claro esta, deje instalado los paquetes sun-java6-bin , sun-java-jre , sun-java6-plugin, sun-java6-fonts y java-common.

Ahora si... A TIMBEAR! Uhu!

---


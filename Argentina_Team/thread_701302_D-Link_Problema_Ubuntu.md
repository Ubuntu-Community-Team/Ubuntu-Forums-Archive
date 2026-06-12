---
title: "D-Link Problema Ubuntu"
date: 2008-02-19
forum: Argentina Team
---

### Post by Dami23 on 2008-02-19
Hola gente como les va?.
Paso a contarles el problema que me viene ocurriendo últimamente, en mi casa armé una red inhalámbrica que consta de un router linksys y 2 receptores usb inhalámbricos D-Link (DWL-G122). El problema en cuestión tiene que ver con el funcionamiento del adaptador d-link en ubuntu. Tengo el Ubuntu 7.10 y todo funcionaba bien antes, pero últimamente durante los primeros 5 minutos la red me funciona muy bien, pero luego se corta la conexión a la red. Como que me desconecta de la red.
Lo raro de todo esto es que en windows me anda perfecto el mismo receptor por ende no parece ser un problema de hardware.
No he encontrado info sobre esto en la web, por eso, si alguno tiene una idea de lo que puede estar causando este problem sería genial.
Desde ya muchas gracias.

---

### Post by mauriciog on 2008-04-07
Dami23:
Los controladores que estas utilizando para el adaptador D.Link son los de Windows? Si es asi, estarás utilizando un wrapper para utilizarlos sobre Ubuntu y esto es, quizas, la causa de este problema. Recordá que los wrappers son experimentales y pueden fallar. Probá desinstalando todo e instalando nuevamente el ndis-wrapper y los controladores originales del adaptador. Saludos!

---


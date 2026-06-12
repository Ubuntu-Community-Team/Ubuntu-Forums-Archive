---
title: "[SOLVED] Inconveniente con el navegador Epiphany"
date: 2008-01-01
forum: Argentina Team
---

### Post by atari130xe on 2008-01-01
Muy feliz 2008! gente empiezo el 2008 con una consulta: Instalé el navegador web Epiphany que es como Firefox pero más integrado a Gnome y consume mucha menos memoria. La pregunta es: (ya me habia pasado antes en otra instalación del navegador). Una vez instalado, aparece en la pestaña que se abre clickeando "Archivo" la opción "trabajar desconectado", hasta ahí todo normal, pero eh aqui que yo destildo esa opción y cuando abro nuevamente el navegador aparece tildada, como puedo dejar por defecto trabajar conectado? muchas gracias a todos :)

---

### Post by User21 on 2008-01-01
Deberias ver en las opciones de Conexion a Internet de Epiphany, de que manera se conecta a Internet, y elegir la opcion correcta, de modo que Epiphany no asuma QUE NO TIENES CONEXION !!!

Intenta eso, en primera instancia. Si no es eso, vamos a ejecutar Epiphany desde consola y ver que nos dice! 
Saludos!

---

### Post by atari130xe on 2008-01-01
felicidades :) vos te referis a "about:config"? y dentro de esas opciones cual seria la que deberia modificar? gracias!:)

---

### Post by User21 on 2008-01-02
Deberias ver en las preferencias de Epiphany, como maneja la conexion a Internet, ya que pareciese que asume que NO HAY CONEXION, y por ende se activa la opcion "Trabajar desconectado".
De todas formas, about:config (de funcionar en Epiphany, ya que NO SE) puede ser un buen lugar donde buscar. 
En resumen: Deberias ver en las preferencias de Epiphany, acerca de la conexion!!!

---

### Post by atari130xe on 2008-01-02
about:config tiene muchas opciones de las cuales al menos a simple vista no aparece ninguna que hable del tipo de conexion, es muy similar a Firefox, pero sinceramente no se cual tocar.:confused:
PD: en preferencias al menos las que aparecen en "editar opciones" no hay nada sobre tipo de conexiones. De todas maneras es un navegador que yo recomiendo para el que quiere nevagar rápido y con bajo consumo de memoria.

---

### Post by atari130xe on 2008-01-09
Encontré la solucion a mi problema: 
abrí una ventana del navegador, tipeé about:config fuí hasta:
network.dns.disableIPV6 (hice doble click) y lo dejé True y santo remedio ahora me conecto, abro el navegador y entro navegando normalmente.
suerte!:)

---


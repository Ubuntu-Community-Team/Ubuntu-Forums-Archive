---
title: "cambiar pais de residencia"
date: 2016-04-03
forum: Argentina Team
---

### Post by pepinillofordewin on 2016-04-03
No hace mucho reinstale ubuntu (a la anterior le borre alguna carpetita de / , a ver que pasaba) y tras varios usos que le he dado al usb que tengo habilitado para instalar ubuntu, en esta ocasion no me fije demasiado y vaya uste a saber a que le di. El caso es que debo de vivir en holanda o por ahi, porque los dominios (sobretodo los de google) pasan de .com , .es , o .loquesea a .nl , me salta el aviso de cookies que me lo leen por la calle y llamo a un exorcista, y el mail de google me manda de correitos de aviso y captchas por inicios de sesion "de forma extraña" que me va a pedir un aumento la bandeja de entrada. Hay mas tonterias pero ya seria explayarse de mas. El caso es que formatos de region no encuentro. De moneda, de idioma, de teclado... Pero no de pais. Si resulta relevante, la version es 15.10. 

Ayudita plz : D

---

### Post by papibe on 2016-04-03
Hola pepinillo. Bienvenido al foro ):P

El idioma oficial del foro es inglés. La mejor manera de conseguir ayuda es usar el inglés aunque no sea perfecto. 

En caso de que no lo veas como una opción para ti, puedo mover tu pregunta a alguno de los sub foros que tenemos en español. Con suerte, ahí te pueden ayudar mejor. Lo único que tienes que considerar es que esos subforos tienen mucho menos movimiento.

Avísame, si quieres que mueva la conversación.

Saludos.

---

### Post by pepinillofordewin on 2016-04-03
si lo haces te coronas, gracias muchas, que ni sabia que teniamos de eso. Asumia que con eso de que a los hispanoparlantes nos tienen marginadillos en el mundo de la informatica, esto seria lo mas parecido. Por otra parte, si bien es cierto que domino el "chapucerus inglish", considero que la puedo liar lo suficiente con un sudo, cero gui, y una istrucciones bien detalladas en español como para ponerme a buscar handicap. Gracias muchas otra vez, y si me dijeras como acceder a mi pregunta en donde quiera que vaya, mas aun. Saluditos

---

### Post by papibe on 2016-04-03
Conversación movida desde un foro en inglés.

---

### Post by gmunioz on 2016-04-09
Prueba con:
Abre una terminal.
Ejecuta en ella:
> sudo -i
apt-get install --reinstall debconf
dpkg-reconfigure locales

El sistema debería presentar una pantalla en la que puedas seleccionar los locales que quieres instalar
y después una pantalla en la que seleccionarás el locale por defecto.

---


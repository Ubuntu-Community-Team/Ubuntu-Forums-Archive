---
title: "[SOLVED] Problemas con el teclado"
date: 2007-12-03
forum: Argentina Team
---

### Post by Vero1 on 2007-12-03
Hola a todos,

Por un problema que tuve con la resoluci´on de pantalla, me indicaron en el chat que hiciera: sudo dpkg-reconfigure xserver-xorg.

Debo haberme equivocado con la configuraci´on del teclado(creo que es porque le dije ok a español- no eliminar teclas muertas, aunque puede ser otra cosa). La cuesti´on es que ahora al marcar una palabra con acento, hace un espacio, como podr´an  ver y no s´e como arreglarlo porque en Teclado figura eso de las teclas muertas y no se puede cambiar.

Intent´e correr nuevamente el comando que menciono mas arriba pero me contesta que no est´a instalado xorg.

Aclaro que antes ten´ia tambien instalado Kubuntu-KDE y lo desinstal´e porque me desconfigur´o la resoluci´on de pantalla.

Eso ya se arregl´o pero queda el problema del acento.

Alguien me puede decir qu´e tengo que hacer?

Muchas gracias y saludos

---

### Post by GepettoBR on 2007-12-03
Descúlpame mi español, soy brasileño y ello no es dos mejores... El famoso "portuñol" :lol:

No sé como estará escrito en el Ubuntu en español, pero el menú de "Sistema" tiene una opción de GUI para configurar la linguage del teclado. Quizás encontres la opcción para castellano o similar - cuando me sucedió lo mismo con mi teclado en português, cambié el mapa de teclas de Brasil ABNT para Brasil ABNT2 e mis problemas fueron solucionados, espero que su problema seja de lo mismo tipo e que así lo soluciones.

---

### Post by Vero1 on 2007-12-03
Hola Gepetto,
Gracias por contestar.

Mi problema no era el mismo pero acabo de arreglarlo. Me ayudaron en el Chat. 

Había configurado mal el xorg.conf.

saludos:)

---

### Post by lynx.jc on 2007-12-11
bueno bueno... pero como le hiciste para arreglarlo porque yo tengo el mismo problema con los acentos me llamo Jos´e y no puedo escribir con acentos correctamente... como configuro el xorg.conf?????:(

---

### Post by marianom on 2007-12-11
lynx.jc:

tu teclado tiene ç? En ese caso es muy posible que sea Español con teclas muertas (o sea, que al presionar la ´ no escriba nada y solo cuando presiones una vocal salga escrita la á (por ejemplo)

si no tenes ç pero si tenés ñ: es un teclado latinoamericano con teclas muertas

una vez identificaste que tipo de teclado tenes, lo seteas en Sistema-> Preferencias -> Teclado.

Si tenes otras cosas en tu teclado :) avisa y lo vemos.

---

### Post by Vero1 on 2007-12-12
Hola lynx,

No lo arreglé con xorg, lo arreglé directamente con el Teclado.

LO que comenta marianom es lo que me pasó a mi. Al configurar xorg le indiqué lo de las teclas muertas y por eso no funcionaba el acento como corresponde.

Vete a Sistema-Preferencias-Teclado. En Distribuciones ponle Predeterminado. Si llegara a figurar lo de las teclas muertas, bórralo y deja España como Predeterminado.

Dime si te resultó.

saludos

---


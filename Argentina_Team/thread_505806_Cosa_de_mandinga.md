---
title: "Cosa de mandinga"
date: 2007-07-20
forum: Argentina Team
---

### Post by Apipote on 2007-07-20
Es rarisimo lo que me ha pasado varias veces ya.
El hiperobeso openoffice, se cuelga seguido, y cuando esto ocurre me desaparecen los paneles tanto de arriba como de abajo de la pantalla en xfce Xubuntu.
El tema es que tengo que entrar con otra sesion, y no con la default.
La pregunta es: Como borrar la sesion que quedo colgada en xubuntu??
Gracias.

---

### Post by Hei Ku on 2007-07-20
Probaste de reiniciar el X Server desde la pantalla de login?

---

### Post by Apipote on 2007-07-20
No se como se hace, me guias?

---

### Post by Hei Ku on 2007-07-20
En la pantalla de login, donde ingresas el usuario y contraseña, deberias tener un menu para apagar, reiniciar, y tambien reiniciar el X server.
Al menos asi es en mi kubuntu, pero recuerdo q la pantalla del xubuntu era similar. Fijate si te aparece una imagen de un menu, ahi deberia estar.
Una vez que encuentres la opcion, es simplemente apretarlo y reinicia el x server. Eso deberia eliminar las sesiones extra.

---

### Post by Apipote on 2007-07-20
Si es cierto, pero aparece una consola, y ahi que hago?

---

### Post by Hei Ku on 2007-07-20
upps. debería reiniciar solo, y volverte a aparecer la pantalla de login.
Proba apretando Ctrl+Alt+F7, eso deberia traerte la primer sesios de xfce.
Si no, tipeando en la consola: startxfce

---

### Post by Apipote on 2007-07-20
No nada
 Esta todo bien, porque abri otra sesion, pero como borro la anterior que la veo aca, y no sirve?

---

### Post by Hei Ku on 2007-07-20
una sesion grafica o de consola? la sesion de consola queda abierta siempre. solo deberias tomar la precaucion de deslogearte, con exit hasta que aparezca el prompt de login de usuario.
Las sesiones graficas, no se como sera en xfce, proba deslogearte del todo, o reinicia otra vez el xserver :D

---

### Post by lavaramano on 2007-07-21
@Apipote: cuando te desaparezcan los paneles de xfce, apreta alt+f2 > te salta el cosito ese para ejecutar un comando y ahi pone "xfce4-panel" y van a volver a aparecer.

despues para reiniciar X, ctrl + alt + backspace.

o sino, ctrl+alt+f1, te loggeas en consola, sudo killall gdm, y despues sudo gdm. ahora con ctrl+alt+f7 deberia arrancar todo de nuevo.

---

### Post by Hei Ku on 2007-07-21
sudo killall gdm, y despues sudo gdm

eso no es para matar el gnome? es por curiosidad, como uso principalmente KDE no estoy familiarizado con los comandos de xfce.

---

### Post by Apipote on 2007-07-21
Mis respetos Señores.............funciona!!!
Gracias!!
Tengo activado, el "display choser on login" y cuando me logueo, me muestra 2 sesiones, la original, que acabo de arreglar con sus indicaciones, y la que use de auxilio para entrar ya que no tenia paneles. Como borro esta ultima, que tuve que crear de auxilio??

---


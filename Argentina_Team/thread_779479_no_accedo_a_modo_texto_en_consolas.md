---
title: "no accedo a modo texto en consolas"
date: 2008-05-02
forum: Argentina Team
---

### Post by LolaMora on 2008-05-02
Hola a todos. Soy nueva en este foro. He preguntado y buscado por muchas partes, pero no he podido arreglar el error.
El problema surge cuando surge algún cuelgue en el entorno gráfico. Pasa a veces cuando mis hijos están a full con los juegos 3D. Intento pasar a consola con ctrl+alt+F1 a la F6 para usar kill  y nro. de proceso, pero me aparece una pantalla negra. Ni siquiera veo el guión titilante. Lo único que me queda por hacer en estos casos es escribir a ciegas:

        nombre usuario

        password

        sudo reboot

        password

La PC se reinicia y vuelve todo a la normalidad, salvo las consolas que siguen invisibles. 

Tengo Gutsy. Placa gráfica Intel integrada.

Me gustaría no tener que reiniciar cada vez que se me cuelga, ya que una de las cosas buenas de GNU/Linux es precisamente la posibilidad de matar el proceso en cuestión, pero a ciegas no puedo. 

Alguna idea?:confused:

---

### Post by Mauro22 on 2008-05-02
No hacer falta pasarse a una consola para cerrar el juego.

Puedes hacer Control + Alt + Backspace (Retroceso) y asi reiniciar el modo grafico y volver a la pantalla de logueo.


Ahora que no se vea si es un problema. Pero nada nada?????

si pones como antes

usuario
password

y depues, no se, un ls para ver los archivos, tampoco aparencen??

---

### Post by Hei Ku on 2008-05-02
las consolas estan invisibles, independiente del cuelgue? 
O sea, apenas inicia ubuntu tampoco se ve nada si pasas a una consola?

---

### Post by MeduZa on 2008-05-03
> **LolaMora said:**
> Hola a todos. Soy nueva en este foro. He preguntado y buscado por muchas partes, pero no he podido arreglar el error.
El problema surge cuando surge algún cuelgue en el entorno gráfico. Pasa a veces cuando mis hijos están a full con los juegos 3D. Intento pasar a consola con ctrl+alt+F1 a la F6 para usar kill  y nro. de proceso, pero me aparece una pantalla negra. Ni siquiera veo el guión titilante. Lo único que me queda por hacer en estos casos es escribir a ciegas:

        nombre usuario

        password

        sudo reboot

        password

La PC se reinicia y vuelve todo a la normalidad, salvo las consolas que siguen invisibles. 

Tengo Gutsy. Placa gráfica Intel integrada.

Me gustaría no tener que reiniciar cada vez que se me cuelga, ya que una de las cosas buenas de GNU/Linux es precisamente la posibilidad de matar el proceso en cuestión, pero a ciegas no puedo. 

Alguna idea?:confused:

a mi me pasa lo mismo, no tengo consolas desde el F1 al F6

---

### Post by MeduZa on 2008-05-03
> **Hei Ku said:**
> las consolas estan invisibles, independiente del cuelgue? 
O sea, apenas inicia ubuntu tampoco se ve nada si pasas a una consola?

es simple desde F7 en adelante (los modos video) andan, y de F1 a F6 nada, pantallas negras y sin cursor. es como que las consolas de texto estuvieran desactivadas.

---

### Post by fmsismo on 2008-05-03
Yo experimento eso con el driver nvidia.  Si paso al nv (de la comunidad sin aceleración 3d) están accesibles.  Según leí esto es un bug detectado.

Saludos

---

### Post by MeduZa on 2008-05-03
> **fmsismo said:**
> Yo experimento eso con el driver nvidia.  Si paso al nv (de la comunidad sin aceleración 3d) están accesibles.  Según leí esto es un bug detectado.

Saludos

ahora entiendo porque antes me andaban :P

debe ser eso, porque desde que puse el kernel nuevo tampoco tengo usplash aunque estoy trabajando en ello a ver si lo reparo

---

### Post by MeduZa on 2008-05-04
ya "hice andar" el modo texto de las consolas si lo logro mejorar les digo como hice y si no, fracasare en el intento xD

---


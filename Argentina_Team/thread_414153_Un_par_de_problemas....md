---
title: "Un par de problemas..."
date: 2007-04-19
forum: Argentina Team
---

### Post by Maxtwo on 2007-04-19
hola a todos, me presento, soy Maximiliano, la verdad hace rato que tengo instalado ubuntu pero esta ultima semana le he empezado a dar bola enserio.  En fin les cuento que tengo un par de problemas, si alguien utiliza C/SDL me puede explicar, sino cualquiera que pueda llegar a tener una idea mejor. 
El problema es que baje SDL, el codigo fuente, lo compile, le hice el make, make install, etc. Ahora si intento compilar algo que utilice dichas librerías me salta que no las encuentra, nose porque es como que el sistema no se haya enterado que existan. 
En teoria bajarme los instaladores de las librerías debería servir pero eso no es una opción tampoco porque estan en *.rpm, y ya intente utilizar alien para pasarlos a *.deb pero al intentar instalarlos de esa forma, me tira un error y no se instala.
---
Aparte tengo otro problema, a veces, porque si el mouse pone loco , empieza a ir de una punta de la pantalla a otra, si estoy en una ventana se scrollea hasta abajo de todo. Pero si lo dejo quieto un segundo se arregla solo. Aun no le encontre lo que hace que se ponga loco asi que nose si es aleatorio o por alguna razon concreta.

Bueno gracias por cualquier ayuda.

---

### Post by gepatino on 2007-04-20
Para instalar paquetes/software, lo más recomendable es utilizar las herramientas de ubutnu (apt-get, aptitude o synaptic) 
Casi seguro que las librerías que necesitas las vas a encontrar en los repositorios, entonces desde el synaptic la buscas, le doble click y listo.

No sé si es el caso de c/sdl, pero en muchos casos necesitás instalar por un lado la librería, y por otro lado los headers, para poder desarrollar para esa librería. Generalmente los nombres de paquetes son iguales, pero el nombre de los de header terminan en '-dev' 

Lo del mouse loco... te lo debo. Mandá un poco más de info sobre el tipo de mouse, etc, alguien te va a poder dar una mano.

---

### Post by clasificado on 2007-04-21
> **Maxtwo said:**
> Pero si lo dejo quieto un segundo se arregla solo. 

¿Probaste cambiando de mouse? Por ahi ya le llegó la hora.

Clasificado.

---

### Post by Maxtwo on 2007-04-21
Gracias a ambos. 
 > **gepatino said:**
> Para instalar paquetes/software, lo más recomendable es utilizar las herramientas de ubutnu (apt-get, aptitude o synaptic) 
Casi seguro que las librerías que necesitas las vas a encontrar en los repositorios, entonces desde el synaptic la buscas, le doble click y listo.

No sé si es el caso de c/sdl, pero en muchos casos necesitás instalar por un lado la librería, y por otro lado los headers, para poder desarrollar para esa librería. Generalmente los nombres de paquetes son iguales, pero el nombre de los de header terminan en '-dev' 


Te cuento que ya había probado eso, me baje todas las librerias de SDL que encontre en el synaptic e igual el problema persiste. Este es el error que me tira al compilar:
> /tmp/ccGOlaKE.o: In function `apply_surface(int, int, SDL_Surface*, SDL_Surface*)':
lesson02.cpp:(.text+0x31): undefined reference to `SDL_UpperBlit'
/tmp/ccGOlaKE.o: In function `load_image(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)':
lesson02.cpp:(.text+0x53): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::c_str() const'
lesson02.cpp:(.text+0x63): undefined reference to `SDL_RWFromFile'
lesson02.cpp:(.text+0x73): undefined reference to `SDL_LoadBMP_RW'
lesson02.cpp:(.text+0x87): undefined reference to `SDL_DisplayFormat'
lesson02.cpp:(.text+0x95): undefined reference to `SDL_FreeSurface'
/tmp/ccGOlaKE.o: In function `main':
lesson02.cpp:(.text+0xb8): undefined reference to `SDL_Init'
lesson02.cpp:(.text+0xf2): undefined reference to `SDL_SetVideoMode'
lesson02.cpp:(.text+0x120): undefined reference to `SDL_WM_SetCaption'
lesson02.cpp:(.text+0x12b): undefined reference to `std::allocator<char>::allocator()'
lesson02.cpp:(.text+0x145): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::basic_string(char const*, std::allocator<char> const&)'
lesson02.cpp:(.text+0x160): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
lesson02.cpp:(.text+0x173): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
lesson02.cpp:(.text+0x183): undefined reference to `std::allocator<char>::~allocator()'


Y asi con cada linea que contiene algo de SDL.

> **clasificado said:**
> ¿Probaste cambiando de mouse? Por ahi ya le llegó la hora.

Clasificado.

Si es posible, ya esta hasta descolorado, y no se mueve del todo fluido jajaja.

---

### Post by marianom on 2007-04-21
El error es al hacer 
```
./configure 
```
no?
De ser así eso genera un config.log que es más fácil de seguir y entender las razones del error.
Si lo tenes en el directorio de compilacìón, por favor tar.gzealo (a ver quien inventa un verbo como ese) y subilo así lo vemos. Suele tener más de 2000 líneas así que hay que reviasar bien.

---

### Post by Maxtwo on 2007-04-21
No el error es al hacer gcc blablah.c , igual subo el log del error?



EDIT: Acabo de reducir un monton de errores que me tira: no les den en importancia a los de arriba:

> sdlhola.c:12: error: expected ‘)’ before ‘:’ token
sdlhola.c: In function ‘main’:
sdlhola.c:45: warning: assignment45 makes pointer from integer without a cast
sdlhola.c:46: warning: assignment makes pointer from integer without a cast
sdlhola.c:61:2: warning: no newline at end of file


mis headers son:
#include "SDL/SDL.h"
#include <string>

Primero, parece que no reconoce a <string>
miren aca estan las lineas en las que me salta que hay errores : 

Linea 12:SDL_Surface *load_image( std::string filename )
--
45: message=load_image("hello_world.bmp");
46: background=load_image("background.bmp");
---

Seguro es alguna estupidez que pase por alto...si alguno tiene idea, bienvenida su respuesta.

---


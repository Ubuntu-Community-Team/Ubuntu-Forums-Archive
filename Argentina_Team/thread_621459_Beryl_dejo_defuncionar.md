---
title: "Beryl dejo defuncionar"
date: 2007-11-23
forum: Argentina Team
---

### Post by Pabliich on 2007-11-23
**Amigos beryl dejo de funcionar de un dia para el otro... nose que le paso no veo mas los maravillosos efectos el cuba nada de nada.. nose que hacer.. ustedes que me recomiendan?.. desinstalo e instalo de nuevo beryl?** ayuda por favor

---

### Post by Hei Ku on 2007-11-23
podrias probar instalando Compiz-fusion, el sucesor de Beryl y Compiz.

---

### Post by sajnox on 2007-11-23
Coincido con Hei Ku, pasate a compiz fusion.

Que version de Ubuntu usas?? Calculo que si tenes Beryl estas con Feisty no?

En una consola escribi

```
$ beryl --replace
```

Y postea el resultado a ver si hay algo que se desconfiguro

---

### Post by Pabliich on 2007-11-23
crossfire@ZonaHacker:~$ beryl --replace
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Relaunching beryl with __GL_YIELD="NOTHING"
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Reloading options




eso me aparece pero cuando cierro la consola.. se me va el efecto y queda como antes :(

---

### Post by sajnox on 2007-11-23
Si el efecto se va es por que cerras la consola.

Presiona alt+f2 y escribi beryl --manager

Si asi funciona vemos para ponerlo en el inicio del equipo

---

### Post by pablo atheist on 2007-12-07
buenas...
a mi me funcionaba beryl a las mil maravillas hasta que se me ocurrio cambiar unas cosas haciendo click derecho sobre el diamante rojo que aparece en la barra de arriba , no me acuerdo bien que cambie pero si ahora ejecuto el beryl manager se me tranca todo y tengo que reiniciar. Probé reinstalarlo pero no funciono  se ve que la configuracion del beryl se mantiene por mas que lo elimine, en fin hay alguna manera de volver a una configuracion estandar del beryl ... 

saludos

---

### Post by vk-cdg on 2007-12-07
Te mandaste la misma que yo en la PC de acá del trabajo (7.04 con Beryl) de tildar la opción de indirect rendering. 

Como es la PC del trabajo y tiene poca memoria de video (solo 32mb) lo dejé así, pero si alguien sabe como solucionarlo mejor.

---

### Post by vk-cdg on 2008-02-05
Después de mucho tiempo de estar en otro edificio, en una PC de prestado, volví a mi puesto original y volví a tener mi PC, con Fiesty. 

Tras loguearme recordé que tenía este problema. Alguien sabe como deshabilitar la opción de indirect rendering?

---

### Post by Mister X on 2008-02-05
> **vk-cdg said:**
> Después de mucho tiempo de estar en otro edificio, en una PC de prestado, volví a mi puesto original y volví a tener mi PC, con Fiesty. 

Tras loguearme recordé que tenía este problema. Alguien sabe como deshabilitar la opción de indirect rendering?

podes editar el archivo de configuracion a mano, no me acuerdo donde esta el de beryl, pero normalmente comienzan con un punto (oculto) y estan en el home de tu usuario, para ver los archivos ocultos hacé:
```
ls -a
```
en tu home y busca alguno que tenga un nombre significativo

---


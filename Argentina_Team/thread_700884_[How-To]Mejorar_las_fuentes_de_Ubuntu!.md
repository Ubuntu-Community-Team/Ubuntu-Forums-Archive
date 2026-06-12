---
title: "[How-To]Mejorar las fuentes de Ubuntu!"
date: 2008-02-18
forum: Argentina Team
---

### Post by nemodot on 2008-02-18
Les traigo acá un tutorial que encontré en [Mundo Geek]("http://mundogeek.net/") y del cual me gustó mucho el resultado.

Se trata de mejorar las fuentes de Ubuntu con Hinting y auto aliasing.

Una muestra de los resultados en mi PC:
[IMG]http://img85.imageshack.us/img85/7581/fuenteskp9.jpg[/IMG]

Bueno, ahi vamos:

Primero instalamos las fuentes de windows si es que no las tienen. De esta forma al visitar páginas webs podremos verlas con el aspecto que los diseñadores pretendían, en lugar de con sustitutas.

```
sudo aptitude install msttcorefonts
```

La fuente Tahoma no se incluye, pero si queremos instalarla podemos seguir los pasos de [esta]("http://mundogeek.net/archivos/2007/11/13/tahoma-en-ubuntu/") miniguía.

Bueno, pasemos a la parte más interesante:
Activar auto hinting y auto aliasing
Para esto tenemos que modificar (o crear) el archivo oculto .fonts.conf de nuestro directorio de usuario:

```
sudo gedit .fonts.conf

```

Introducimos lo siguiente y guardamos:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "/etc/fonts/fonts.dtd">
<fontconfig>
    <match target="font">
        <edit name="autohint">
            <bool>true</bool>
        </edit>
        <edit name="antialias">
            <bool>true</bool>
        </edit>
    </match>
</fontconfig>
```

Abrimos el diálogo de configuración de las tipografías (Sistema -> Preferencias -> Apariencia -> Tipografías en Ubuntu Gutsy Gibbon) y seleccionamos "Suavizado de subpíxel (LCDs)" (o el que más se ajuste a nuestro gusto).

Les fuentes por defecto de Ubuntu no son precisamente las mas preciositas, personalmente elegi poner Verdana a todo por que mejoradas se ven bárbaras.

Y eso es todo.

[Fuente]("http://mundogeek.net/archivos/2007/10/25/mejorar-las-fuentes-de-ubuntu/#more-1238")

---

### Post by leo_rockway on 2008-02-19
Ya tenía todas las fuentes de mi Kubuntu más customizadas que una Harley :-P

Gracias por compartir esta información.

---

### Post by nemodot on 2008-02-20
La verdad que las fuentes mejoradas le dieron un notable mejor aspecto a mi sistema y por eso quería compartirlo.

---

### Post by niko_3100 on 2008-02-20
Se puede probar y volver atras con las letras originales??vTener las dos opciones?

---

### Post by pol666 on 2008-02-20
jamas note direncia, ni antes ni despues .. lo tendria instalado por defecto supongo

---

### Post by faktorqm on 2008-02-22
Se puede volver a las letras originales? Es importante esa pregunta.
Para mi como no existe ya el archivo por mas que lo pongas es lo mismo. Pero igual lo queria probar a ver que pasaba. Pero si no anda quiero volver ;) Salu2!!

---

### Post by niko_3100 on 2008-02-22
Claro como dice aca el hincha de estudiantes, si no me gusta quiero volver al original por eso viteh!!

---

### Post by spg76 on 2008-02-22
Desde "Sistema > Preferencias > Apariencia > Tipografías", se pueden modificar las fuentes y su renderizado (ver botón "Detalles") sin tocar ningún archivo de texto.
Para volver a la configuración original, simplemente lo vuelven a cambiar desde ahí.

---


---
title: "DSLR freaks: Salio digikam 0.9.0 rc1 y compila bien en Edgy"
date: 2006-12-04
forum: Argentina Team
---

### Post by ariel on 2006-12-04
Para los fanaticos de la fotografia digital, D-SLRs freaks etc...

No se puede creer lo bueno que esta digikam 0.9.0 RC1! Por ahora hay que bajar los fuentes y compilarlo siguiendo las instrucciones, pero vale la pena. Los pibes agregaron todo lo que les faltaba para que muuuuucha gente pueda tirar adobe imageready al tacho:

gamma correction
lectura de raw files (NEF) de Nikon para D80, 16-bits per channel
Color management!!! ahora se puede cargar el .icc del fabricante de la camara, y el .icc del estudio de impresion, y listo. Con un monitor razonablemente calibrado (por ejemplo usando gammaPage + ddcontrol), todo el workflow basico esta resuelto. 

Para sacarse el sombrero.

---

### Post by beuno on 2006-12-04
Seria genial un link y hasta un mini howto para instalarlo.

;)

---

### Post by Nemesis Teufel on 2006-12-04
Upa, me interesa!! espero el how to 	:-\"

---

### Post by jpmorelli on 2006-12-04
> **ariel said:**
> Para los fanaticos de la fotografia digital, D-SLRs freaks etc...

No se puede creer lo bueno que esta digikam 0.9.0 RC1! Por ahora hay que bajar los fuentes y compilarlo siguiendo las instrucciones, pero vale la pena. Los pibes agregaron todo lo que les faltaba para que muuuuucha gente pueda tirar adobe imageready al tacho:

gamma correction
lectura de raw files (NEF) de Nikon para D80, 16-bits per channel
Color management!!! ahora se puede cargar el .icc del fabricante de la camara, y el .icc del estudio de impresion, y listo. Con un monitor razonablemente calibrado (por ejemplo usando gammaPage + ddcontrol), todo el workflow basico esta resuelto. 

Para sacarse el sombrero.

Buenísimo, es chino básico pero suena lindo, jajajaja :rolleyes:

---

### Post by ariel on 2006-12-04
Acá va un mini-howto:

1- Bajar los fuentes de:

   [http://sourceforge.net/project/showfiles.php?group_id=42641](http://sourceforge.net/project/showfiles.php?group_id=42641)

   Bajar: [digikam-0.9.0-rc1]("http://sourceforge.net/project/showfiles.php?group_id=42641&package_id=34800&release_id=465525")   y [digikamimageplugins-0.9.0-]("http://sourceforge.net/project/showfiles.php?group_id=42641&package_id=132740&release_id=465526")rc1

   a una carpeta temporal (ejemplo ~/temp)

   Abrir una terminal y: 

```
cd ~/temp
tar xvzf [digikam-0.9.0-rc1.tar.bz2]("http://sourceforge.net/project/showfiles.php?group_id=42641&package_id=34800&release_id=465525")
cd  [digikam-0.9.0-rc1]("http://sourceforge.net/project/showfiles.php?group_id=42641&package_id=34800&release_id=465525")
./configure 
```

De entrada, configure va a tirar errores que indican cuales son las librerias/bibliotecas faltantes (en una instalacion default de edgy, tipicamente van a faltar todas las librerias de desarrollo).

Por ejemplo, esta la salida de mi ./configure (con todas las librerias ya instaladas).

```
-- digiKam configure results -------------------
-- sqlite3 found.................. YES
-- libgphoto2 found............... YES
-- libkipi found.................. YES
-- libtiff found.................. YES
-- libpng found................... YES
-- lcms found..................... YES
-- Exiv2 library found............ YES
------------------------------------------------

Good - your configure finished. Start make now
```

En caso de haber errores, por ejemplo "missing exiv2 library", lo mas rapido es abrir synaptics, hacer un search de (en este caso) "exiv2", e instalar exiv2 y **libexiv2-0.10 y tambien libexiv2-dev**   (es importante instalar todas los packages "-dev" asociados).

Despues de instaladas todas las librarias requeridas, ./configure va a decir 

```
 Good - your configure finished. Start make now
```

Que indica que ya se puede tirar el make (no hace falta ser root):

```
make
```

El proceso toma diez minutos en una P4 3.2GHz 2G RAM. En una instalacion de edgy oficial no deberia saltar ningun error, ese fue mi caso. Si las ultimas lineas no continenen [Error] basicamente deberia estar todo bien, ahora hay que instalar el nuevo programa:

```
sudo make install
```

Y ahora a laburar:

```
digikam
```

El mismo proceso se aplica a imageplugins, los plugins son opcionales.


Las ventajas del nuevo digikam las van a ver los que gastaron unos morlacos en una camara reflex digital masomenos buena (Nikon D50, D70, D80, o incluso hasta una canon rebel). Practicamente no habia opciones a photoshop y herramientas asociadas. Lamentablemente Gimp tiene una limitacion de disenio (8 bits por canal de color) cuando todas camaras dslr nuevas son de 12 o 16 bits, por lo que muy poca gente usa gimp para editar fotos "mas o menos en serio". Es mas, todas esas camaras graban fotos en formato "raw", eso es sin compresion jpeg, para no generar ningun tipo de distorsion.  Hay plugins para Gimp que "convierten" los raws en jpeg de 8 bits con la consecuente distorsion.

Y aca vinieron los pibes de kde. Digikam carga y procesa raws de 16 bits en forma nativa. Tipicamente la foto va a requerir ajuste de Gamma, brillo y contraste, y finalmente crop (recorte). 

Y durante el proceso de ajuste, es muy importante que los colores que muestra el monitor se aproximen a los que van a salir impresos (suponiendo que el objetivo es imprimir la foto), e**sto es muuuuucho mas complejo de lo que suena** y se llama "Color Management". Un dia me puedo explayar un poco mas, pero basicamente hay que:

[LIST]
[*]Calibrar el monitor: temperatura de color y despues Gamma del monitor.[/LIST][INDENT]Los pros usan un colorimetro, los pobres usamos:
GammaPage: [http://www.pcbypaul.com/software/GAMMApage.html](http://www.pcbypaul.com/software/GAMMApage.html)

[/INDENT][LIST]
[*]Y los controles del monitor o bien esta aplicacion muy piola:[/LIST][INDENT]Monitor DDC control GUI: [http://sourceforge.net/projects/ddccontrol](http://sourceforge.net/projects/ddccontrol)
[/INDENT][INDENT](aca tienen para leer sobre el tema: 

[http://www.normankoren.com/makingfineprints1A.html](http://www.normankoren.com/makingfineprints1A.html)

[http://ufraw.sourceforge.net/Colors.html](http://ufraw.sourceforge.net/Colors.html))

[/INDENT][LIST]
[*]Digikam ahora permite indicarle cual es el "Color space" de la imagen de entrada, y el Color Space de la impresora que va a imprimir. El color space de entrada depende de la camara, cada camara de Nikon tiene el suyo. El de la impresora se puede bajar de los sitios de los estudios de fotografia buenos, ellos mismos los postean. Ademas Digikam requiere conocer el profile del monitor, que ya conocemos gracias al ajuste de GammaPage.[/LIST]
[LIST]
[*]Despues de todo este lio, podemos ajustar los colores, brillo, contraste, etc, de la imagen mirando el monitor, sabiendo que la imagen impresa se va a ver bastante parecida. Lograr algo tan simple  es asi de recontracomplicado (y hasta hace poco requeria Windows o Mac)[/LIST][LIST]
[*]En fotografia digital hacen falta todas estas cosas, lamentablemente; basta mirar la misma foto en dos monitores distintos no calibrados para darse cuenta por qué. O imprimir una foto ampliada en una casa de revelado trucha.[/LIST]
Finalmente, para completarla, hacen falta algunas funciones de uso comun de photoshop para los fotografos que necesitan retocar fotos. Efectos tipo Smudge y cosas asi. Bueno, eso va a venir (con 16 bits por canal y color management) en Krita 2.0. El nuevo Gimp tambien lo va a tener algun dia pero lamentablemente todavia falta muchisimo desarrollo.

Bueno despues de todo este discurso, si leiste hasta aca es porque te interesa la fotografia digital. Espero que esto despierte tu interes en las posibilidades de Linux en procesamiento de fotos (pro o al menos semi-pro), y te muestre el avance impresionante de estos ultimos dos anios en linux (en aquella epoca no habia ninguna opcion)

A

---

### Post by jpmorelli on 2006-12-05
Estos HowTo hay que recopilarlos para la web !!! Tienen que estar !

---

### Post by beuno on 2006-12-05
> **jmorelli said:**
> Estos HowTo hay que recopilarlos para la web !!! Tienen que estar !

Estamos armando la web para que sea facil volcarlos.
Es prioridad.

---


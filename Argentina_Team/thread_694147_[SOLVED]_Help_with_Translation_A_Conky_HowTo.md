---
title: "[SOLVED] Help with Translation: A Conky HowTo"
date: 2008-02-11
forum: Argentina Team
---

### Post by Bruce M. on 2008-02-11
Hola,

I need help translating this for a person from Argentina.
My problem is I'm learning castellano (porteño) and I don't have the ability.

Please take a look at my [HowTo]("http://ubuntuforums.org/showpost.php?p=4157750&postcount=1489").

If you can translate it, please post it here in the Argentina area.

A screenshot of my Conky with weather for Buenos Aires.

Si quieres el "[**5 Day Forecast**]("http://ubuntuforums.org/showthread.php?t=666842")" ( en ingles )

Gracias,
Bruce

EDIT: [dos conkys]("http://ubuntuforums.org/showthread.php?p=4317890#post4317890") - en castellano gracias a tzulberti

---

### Post by tzulberti on 2008-02-11
Hola. Hice esta traduccion, y creo que esta bien. Sin embargo tiene faltas de otrografia porque no soy muy bueno escribiendo.

Hi. I translated it, and I think that it may have some few corrections to be made (mainly in language). Nevertheless, it is easy to follow it and understand the main idea.




Vamos a hacer esto en 7 simples pasos
Para conservar la configuracion original del conky vas a necesitar 3 archivos extra:
1: conkyweather (guardar en: ~/.conkyscripts)
2: weather.sh (guardar en: ~/scripts)
3: weather.xslt (guardar en: ~/scripts)

Los archivos 2 y 3 tienen que estar en la misma carpeta (~/scripts).
Tambien vas a tener 2 scripts de conky, el que tienes ahora, que lo vas a tener que mover y renombrar, y el conkyweather #1 de arriba. Pone esos dos archivos en ~/.conkyscripts

PASO 1: conkywearth (un archivo de script para conky)

Crear un archivo de conkyweather:
gksudo gedit ~/.conkyscripts/conkyweather

Este es mi archivo conkyweather. Copia y pegalo en el archivo vacio que creates anteriormente con gedit. Luego guardalo como conkyweather.
background yes
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
use_spacer yes
use_xft yes
xftfont Candara:size=8
xftalpha 0.5
update_interval 1.0
draw_shades no
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
own_window_colour brown
own_window_transparent yes
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
gap_x 10
gap_y 25
# Subtract file system buffers from used memory?
no_buffers yes

TEXT
${color cyan}WEATHER: ${hr 1}$color
${color white}${execi 60 ~/scripts/weather.sh ARBA0009}$color


PASO 1a (Ver paso 6): Vas a necesitar cambiar ARBA0009 por el codigo postal si estas en los Estados Unidos o por el codigo de la ciudad si estas fuera de EEUU. El codigo para Buenos Aires es 
ARBA0009.

NOTA: En este momento cambiar de nombre el archivo renombra tu archivo existente de conky como conkymain, y ponelo en la misma carpeta que conkyweather. Vamos a ver el porque en el PASO 4.

PASO 2: weather.sh (guardalo en: ~/scripts)

Este es mi archivo conkyweather.sh:

# Usage:
# ${execi 1800 /path/to/weather/weather.sh location}
# Usage Example:
# ${execi 1800 /home/user/weather/weather.sh 03833}

# your Location ID: use [http://xoap.weather.com/search/search?where=](http://xoap.weather.com/search/search?where=)[yourcity] to find it 
# U.S. users can just use their zip code; doubt that works for anyone else though (YMMV)
LOCID=ARBA0009

# s=standard units, m=metric units
UNITS=m

# where this script and the XSLT lives#
RUNDIR=~/scripts

# there's probably other stuff besides CURL that will work for this, but i haven't 
# tried any others. 
# you can get curl at [http://curl.haxx.se/](http://curl.haxx.se/)
CURLCMD=/usr/bin/curl

# get it at [http://xmlsoft.org/XSLT/](http://xmlsoft.org/XSLT/)
XSLTCMD=/usr/bin/xsltproc

# you probably don't need to modify anything below this point....

# CURL url. Use cc=* for current forecast or dayf=10 to get a multi-day forecast
CURLURL="http://xoap.weather.com/weather/local/$LOCID?dayf=10&unit=$UNITS&cc=*"

# The XSLT to use when translating the response from weather.com
# You can modify this xslt to your liking 
XSLT=$RUNDIR/weather.xslt

#filter (if you want to convert stuff to lower-case or upper case or something)
#FILTER="|gawk '{print(tolower(\$0));}'"


#####
eval "$CURLCMD \"$CURLURL\" 2>/dev/null| $XSLTCMD $XSLT - $FILTER"



STEP 2a - See STEP 6: Once again you'll need to edit two lines:
PASO 2a (Ver paso 6): Otra vez vas a necesitar editar dos lineas:
Cambia la linea que empieza con LOCID=ARBA0009 por el codigo postal de tu ciudad (si vivis en EEUU) o por el codigo de tu ciudad (si vivis fuera de EEUU).
En la linea que dice UNITS=m, cambia la "m" por una "s"

Ya esta configurado para la esquina de arriba a la derecha de tu pantalla.
Una vez que esta hecho eso, vas a necesitar convertirlo en un ejecutable:

sudo chmod a+x ~/scripts/weather.sh


PASO 3: weather.xslt (guardar en: ~/scripts)

Este es el codigo responsable por el formato que vas a ver en la imagen de abajo.
<!-- 

 This XSLT is used to translate an XML response from the weather.com
 XML API. 

 You can format this file to your liking. Two things you may feel 
 like doing:

	1) Modify the layout of the fields or static text already defined
	2) Add other fields from the XML response file that aren't referenced in this
	   XSLT. You can grab a full list by just doing a: 
           wget "http://xoap.weather.com/weather/local/$LOCID?cc=*&unit=$UNITS" 
           (change $LOCID and $UNITS to suit your needs)
-->

<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0" > 
	<xsl:output method="text" disable-output-escaping="yes"/>
	<xsl:template match="weather">
			<xsl:apply-templates select="loc"/>
			<xsl:apply-templates select="cc"/>
			<xsl:apply-templates select="dayf/day[@d='1']"/>
	</xsl:template>
	
			<xsl:template match="loc">

<xsl:text>Live from:  </xsl:text><xsl:value-of select="dnam"/>
<xsl:text>
Lat: </xsl:text><xsl:value-of select="lat"/>
<xsl:text>                  Long: </xsl:text><xsl:value-of select="lon"/>
<xsl:text>
SUN:  Rise: </xsl:text><xsl:value-of select="sunr"/>
<xsl:text>     Set: </xsl:text><xsl:value-of select="suns"/>

			</xsl:template>

			<xsl:template match="cc">#

<xsl:text>

Temp: </xsl:text><xsl:value-of select="tmp"/><xsl:value-of select="/weather/head/ut"/>

<xsl:text>              Feels Like: </xsl:text><xsl:value-of select="flik"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text>

Conditions: </xsl:text><xsl:value-of select="t"/>
<xsl:text>
Visibility: </xsl:text><xsl:value-of select="vis"/><xsl:text> KM</xsl:text>
<xsl:text>     Humidity: </xsl:text><xsl:value-of select="hmid"/><xsl:text>%</xsl:text>
<xsl:text>
Wind: </xsl:text>
<xsl:choose>
	<xsl:when test="wind/s = 'calm'"><xsl:text>0</xsl:text></xsl:when>
	<xsl:otherwise><xsl:value-of select="wind/s"/></xsl:otherwise>
</xsl:choose>
<xsl:value-of select="/weather/head/us"/> 
<xsl:choose>
	<xsl:when test="wind/s = 'calm'"><xsl:text>(0 km/h)</xsl:text></xsl:when>
	<xsl:otherwise><xsl:text> (</xsl:text><xsl:value-of select="round(wind/s * 0.6214)"/><xsl:text> mph)</xsl:text></xsl:otherwise>
</xsl:choose>
<xsl:text> (</xsl:text><xsl:value-of select="wind/t"/>
<xsl:text>)</xsl:text>

<xsl:text>
Bar Pressure: </xsl:text><xsl:value-of select="bar/r"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="bar/d"/>

<xsl:text>
UV: </xsl:text><xsl:value-of select="uv/i"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="uv/t"/>
<xsl:text>            Dew Point: </xsl:text><xsl:value-of select="dewp"/>

<xsl:text>

MOON: Icon: </xsl:text><xsl:value-of select="moon/icon"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="moon/t"/>

	</xsl:template>

	<xsl:template match="dayf/day[@d='1']">
<xsl:text>
Tomorrow: </xsl:text><xsl:value-of select="low"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> to </xsl:text><xsl:value-of select="hi"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="part[@p='d']/t"/>
<xsl:text>
  </xsl:text><xsl:value-of select="/weather/swa/a/t"/>
<xsl:text>
</xsl:text>
	</xsl:template>

</xsl:stylesheet>



Asique ahora tenes 4 archivos:
En la carpeta: ~/scripts
--> conkyweather.sh (ejecutable)
--> weather.xslt

y en la carpeta: ~/.conkyscripts
--> conkymain
--> conkyweather

PASO 4: Iniciando los dos conkys:
Empeza creando un archivo oculto llamado: startconky

gksudo gedit ~/.startconky


Copia y pega este codigo en el archivo y guardalo:
#!/bin/bash
sleep 25 
conky -c ~/.conkyscripts/conkymain &
sleep 1 
conky -c ~/.conkyscripts/conkyweather &

The sleep command allows your desktop to setup before conky runs.
El comando sleep permite que se configure tu escritorio antes que conky corra.

PASO 6: Obteniendo mas informacion

Visita esta pagina (copia y pega en tu navegador): (cambiar el nombre de la ciudad o usa el codigo postal una vez conectado, es la forma mas facil):
[http://xoap.weather.com/search/search?where=Buenos](http://xoap.weather.com/search/search?where=Buenos) Aires

Te dara una informacion similar a esta:
<?xml version="1.0" encoding="ISO-8859-1"?>
<!--This document is intended only for use by authorized licensees of The Weather Channel. Unauthorized use is prohibited. Copyright 1995-2005, The Weather Channel Interactive, Inc. All Rights Reserved.-->
<search ver="2.0">
  <loc id="ARDF0127" type="1">Aeroparque Buenos Aires, Argentina</loc>
  <loc id="ARBA0009" type="1">Buenos Aires, Argentina</loc>
</search>

As you see I have two choices for Buenos Aires.
Como puedes ver hay dos opciones para Buenos Aires
Ahora hace esto en la consola:

wget "http://xoap.weather.com/weather/local/$ARDF0127?cc=*&unit=$m"

Changing ARDF0127 for an option you got at the URL above and if necessary:
Cambia ARDF0127 por una de las opciones que obtuvistes del la direccion anterior, y si es necesario, cambia
unit=$s por el standard (F)
unit=$m es para metros(C)

You will receive a file something like this in your home folder: 
Vas a recivir un archivo en tu carpeta home con un nombre similar a este:ARDF0127%3Fcc=*&unit=m
Abrilo, y veras algo similar a esto:
<?xml version="1.0" encoding="ISO-8859-1"?>

<!--This document is intended only for use by authorized licensees of The Weather Channel. Unauthorized use is prohibited. Copyright 1995-2005, The Weather Channel Interactive, Inc. All Rights Reserved.-->

<weather ver="2.0">
  <head>
    <locale>en_US</locale>
    <form>MEDIUM</form>
    <ut>C</ut>
    <ud>km</ud>
    <us>km/h</us>
    <up>mb</up>
    <ur>mm</ur>
  </head>

  <loc id="ARDF0127">

    <dnam>Aeroparque Buenos Aires, Argentina</dnam>
    <tm>5:43 PM</tm>
    <lat>-34.58</lat>
    <lon>-58.43</lon>
    <sunr>5:42 AM</sunr>
    <suns>8:09 PM</suns>
    <zone>-3</zone>

  </loc>

  <cc>

    <lsup>12/29/07 5:00 PM Local Time</lsup>
    <obst>Buenos Aires Air Park, Argentina</obst>
    <tmp>29</tmp>
    <flik>30</flik>
    <t>Partly Cloudy</t>
    <icon>30</icon>
    <bar>
      <r>1003.0</r>
      <d>falling</d>
    </bar>
    <wind>
      <s>8</s>
      <gust>N/A</gust>
      <d>270</d>
      <t>W</t>
    </wind>
    <hmid>51</hmid>
    <vis>10.0</vis>
    <uv>
      <i>3</i>
      <t>Moderate</t>
    </uv>
    <dewp>18</dewp>
    <moon>
      <icon>20</icon>
      <t>Waning Gibbous</t>
    </moon>

  </cc>

</weather>


This file gives you the coding necessary to edit  the way you want.
Este archivo te da la codificacion necesaria para editar weather.xslt en la forma que quieras.

PASO 7: Iniciando y parando ambos conkys:

PASO 7a: Automaticamente al momento de inicio
Yo uso Feisty. Si vos no usas esta version el proceso puede ser diferente:
Abri Sistemas-> Preferencias -> Sessiones -> Nuev
Nombre: Conky
Comando: /home/tu_nombre_de_usuario_aca_/.startconky

NOTA: si ya tienes conky configurado para iniciar automaticamente, editalo para que refleje el cambio hecho arriba con los cambios necesarios.


PASO 7b: Manualmente
En una consola:
Iniciando ambos conkys (Ver PASO 4)
./.startconky

Parando ambos conkys:
killall conky


Yo creo que eso es todo. 
Si tienes mas preguntas, pregunta nomas.,.

Bruce

PD: esta informacion es traida por todas las personas que me ayudaron a configurar mi conky. Sino fuese por ellos, yo no podria haber respondido tu pedido.

EDICION: 21 Ene 2008: Dos errores en weather.sh corregidos - Mis agradecimientos a aonegodman
EDICION: 22 Ene 2008: Editado el "~/.startconky" - Gracias a Salpiche

---

### Post by Bruce M. on 2008-02-12
> **tzulberti said:**
> Hola. Hice esta traduccion, y creo que esta bien. Sin embargo tiene faltas de otrografia porque no soy muy bueno escribiendo.

Hi. I translated it, and I think that it may have some few corrections to be made (mainly in language). Nevertheless, it is easy to follow it and understand the main idea.

Perfecto!  Gracias.
Es mucho mejor que yo puedo hacerlo!

Y tengo algo mas tambien.

Este es para dos conkys, pero ahora estoy usando uno solo como "attached"

El "HowTo" (en ingles) para "los 5 días" esta aca:

[http://ubuntuforums.org/showthread.php?t=666842](http://ubuntuforums.org/showthread.php?t=666842)

---


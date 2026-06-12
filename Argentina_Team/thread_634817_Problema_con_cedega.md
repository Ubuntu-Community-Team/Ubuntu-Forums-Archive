---
title: "Problema con cedega"
date: 2007-12-08
forum: Argentina Team
---

### Post by zerio on 2007-12-08
Hola a todos.
Pues nada, que no consigo poner a funcionar el cedega. No es nada grave, pero si lo soluciono mejor, la verdad.
La cosa es que se supone que lo tengo instalado pero no me aparece en el menú Aplicaciones (y no aparece tampoco en el editor de menus), y cuando lo intento abrir desde el terminal me da el siguiente error:
Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 2616, in ?
    Point2Play_gui_ref = Point2Play_gui( Point2Play.Point2Play( config_file, alternate_configs ) )
  File "/usr/lib/transgaming_cedega/Point2Play.py", line 333, in __init__
    raise badConfigFile( _("Missing options %s") % e.value )
AttributeError: NoOptionError instance has no attribute 'value'

Que yo sepa tengo instalados todos los paquetes necesarios.
Poniendo el error en google me salen dos páginas en inglés y otro que debe ser polaco o algo así (no lo entiendo, claro).
Las de inglés intenté llevarlas a cabo pero no me funcionaba (soy un poco inexperto todavía, aunque voy aprendiendo)
A ver si me podeis ayudar.

---

### Post by jotix on 2007-12-11
Hola, que tal, yo tambien soy bastante nuevo en linux, pero primero te preguntaría si lo que queres hacer funcionar con cedega probaste primero hacerlo funcionar con wine.  Mi experiencia personal (basada unicamente en world of warcraft y call of duty) es que me van perfecto con wine e incluso con ventrilo funcionando al mismo tiempo.
Mi SO: ubuntu 7.10 AMD64

---


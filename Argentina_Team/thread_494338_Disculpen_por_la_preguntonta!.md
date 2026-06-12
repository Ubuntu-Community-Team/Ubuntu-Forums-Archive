---
title: "Disculpen por la preguntonta!"
date: 2007-07-06
forum: Argentina Team
---

### Post by Mauro22 on 2007-07-06
Que tal?

Quiero saber si existe la forma de cambiar el color de las palabras "Aplicaciones, Lugares, Sistema" ya que yo uso la barra transparente y con un wallpaper negro se me complica :D


Lo pregunto aca, porque se que esta lleno de Capos!


Salu2

---

### Post by MeduZa on 2007-07-06
no es preguntonta, la verdad que es algo que necesite, al igual que vos, ni bien empece con ubuntu, y yo lo hice asi (creo que esto ya lo postie):

.gtkrc-2.0 y ponerle esto adentro:
> style "panel"
{
fg[NORMAL]               = "#ffffff"
#  fg[PRELIGHT]            = "#000000"
#  fg[ACTIVE]               = "#ffffff"
#  fg[SELECTED]            = "#000000"
#  fg[INSENSITIVE]            = "#8A857C"

# bg[NORMAL]               = "#5E5FB8"
#  bg[PRELIGHT]            = "#dfdfdf"
#  bg[ACTIVE]               = "#D0D0D0"
#  bg[SELECTED]            =  "#5E5FB8" #"#D8BB75"
#  bg[INSENSITIVE]            = "#EFEFEF"

# base[NORMAL]            = "#8E8FE8"
#  base[PRELIGHT]            = "#EFEFEF"
#  base[ACTIVE]            = "#D0D0D0"
#  base[SELECTED]            = "#DAB566"
#  base[INSENSITIVE]         = "#E8E8E8"

#  text[NORMAL]            = "#161616"
#  text[PRELIGHT]            = "#000000"
#  text[ACTIVE]               = "#000000"
#  text[SELECTED]            = "#ffffff"
#  text[INSENSITIVE]            = "#8A857C"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
class "*tray*" style "panel"

ahi podes cambiar de todo, yo solo cambie la primer linea! q es el color de letra
espero te sirva

---

### Post by Mauro22 on 2007-07-07
Ni bien tenga un minuto lo pruebo.


Se agradece LoCo.


Salu2

---

### Post by andy_91 on 2007-07-08
aun no tengo linux pero pueden poner esto en español q tal manual de linux para bobos me vendria bien

---


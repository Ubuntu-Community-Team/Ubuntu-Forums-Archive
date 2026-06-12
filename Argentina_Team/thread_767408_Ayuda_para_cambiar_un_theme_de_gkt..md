---
title: "Ayuda para cambiar un theme de gkt."
date: 2008-04-25
forum: Argentina Team
---

### Post by valucha on 2008-04-25
[COLOR="DarkOrchid"]¿Cómo podré cambiar esto, por otra imágen? [/COLOR]

[IMG]http://img88.imageshack.us/img88/1403/pantallazovu9.png[/IMG]


[COLOR="DarkOrchid"]Acá dejo el gtk, por si ayuda, desde ya muchisisiisismas gracias :)
[/COLOR]
> gtk-icon-sizes = "panel-menu=24,24" #rozmiar ikon w menu na panelu

style "theme-default"
{
  GtkButton      ::default_border    = { 0, 0, 0, 0 }
  GtkRange       ::trough_border     = 0
  GtkPaned       ::handle_size       = 6
  GtkRange       ::slider_width      = 12
  GtkRange       ::stepper_size      = 15

  GtkScrollbar   ::min_slider_length = 30
  GtkCheckButton ::indicator_size    = 13
  GtkMenuBar     ::internal-padding  = 0
  GtkTreeView    ::expander_size     = 14
  GtkExpander    ::expander_size     = 16
  GtkScale       ::slider-length     = 16
  
  xthickness = 1
  ythickness = 1

  fg[NORMAL]        = "#222222" #czer&#324;
  fg[PRELIGHT]      = "#222222" #czer&#324;
  fg[SELECTED]      = "#ffffff" #biel
  fg[ACTIVE]        = "#575757" #ciemno-szary # kolor czcionki na zak&#322;adkach
  fg[INSENSITIVE]   = "#202020" #szary #b5b3ac # --/--

  bg[NORMAL]        = "#FBF8F1" #jasny pomara&#324;cz # t&#322;o linii warto&#347;ci
  bg[PRELIGHT]      = "#FFFEFC" #jasny pomara&#324;cz #FFFEFC #prelight rozwijanych list
  bg[SELECTED]	    = "#EAD29B" #szary z nut&#261; bordowego #CDB7B5 # EHH
  bg[INSENSITIVE]   = "#E7DACD" #cytrynowy #f1efde
  bg[ACTIVE]        = "#F6EFE0" # jasny pomara&#324;cz #F6EFE0 #E3C4A7 # t&#322;o nieaktywnej zak&#322;adki

  base[NORMAL]      = "#ffffff" #biel
  base[PRELIGHT]    = "#B86D3C" #delikatny fiolet #DEB0CD 
  base[ACTIVE]      = "#F4DD98" #cytrynowy / pomara&#324;cz #E6B68A #F4DD98
  base[SELECTED]    = "#E6B68A" #pomara&#324;cz / fiolet #D5A7AF #E6B68A
  base[INSENSITIVE] = "#F6EFE0" # jasny pomara&#324;cz 

  text[NORMAL]      = "#505050" #ciemno-szary
  text[PRELIGHT]    = "#505050" #ciemno-szary
  text[ACTIVE]      = "#505050" #ciemno-szary
  text[SELECTED]    = "#ffffff" #biel
  text[INSENSITIVE] = "#575757" #szary #b5b5b5

  engine "murrine" 
  {
menuitemstyle = 2 # 0 = flat, 1 = glassy, 2 = striped
	scrollbar_color		= "#505050"
	scrollbarstyle		= 2
	contrast		= 0.8
glazestyle = 0
	 menubarstyle = 3
	 menubaritemstyle = 1
menuitemstyle = 0
	 listviewheaderstyle = 0
	 listviewstyle = 1
	 roundness = 2 # 0,1,2,3,4,5,6,7,8
animation = TRUE
	hilight_ratio = 0.909090
  }
}


style "theme-wide" = "theme-default"
{
  xthickness = 2
  ythickness = 2
  text[NORMAL]      = "#505050" #ciemno-szary
}

style "theme-wider" = "theme-default"
{
  xthickness = 3
  ythickness = 3
  text[NORMAL]      = "#505050" #ciemno-szary
}

style "theme-entry" = "theme-wider"
{
  bg[SELECTED]	    = "#B86D3C" #jasny fiolet #CDB7B5 / ciemniejszy pomara&#324;cz #E6B68A
  text[NORMAL]      = "#505050" #ciemno-szary
  text[PRELIGHT]      = "#505050" #ciemno-szary
  text[INSENSITIVE]      = "#505050" #ciemno-szary
  text[ACTIVE]      = "#505050" #ciemno-szary
}

style "theme-button" = "theme-wider" #przyciski/buttony
{
  #bg[NORMAL]        = "#f2f2f2" #szary
  #bg[INSENSITIVE]   = "#f0f0f0" #szary
  bg[PRELIGHT]      = "#F5E9CE" #ciemny fiolet #E0D0AE #FFEAD4
  bg[ACTIVE]	     = "#F5E9CE" #jasny fiolet / jasny pomara&#324;cz #E6B68A
}

style "theme-notebook" = "theme-wide"
{
  bg[NORMAL]      = "#FFFEFC"  #a la biel
  bg[INSENSITIVE] = "#FFFEFC" #a la biel
  bg[SELECTED]    = "#E6B68A" #jasny pomara&#324;cz #E6B68A / pasek aktywnej zak&#322;adki

  text[NORMAL]      = "#505050" #ciemno-szary
  text[PRELIGHT]      = "#505050" #ciemno-szary
  text[INSENSITIVE]      = "#505050" #ciemno-szary
  text[ACTIVE]      = "#505050" #ciemno-szary

	fg[PRELIGHT]	= "#505050" #ffffff
	fg[NORMAL]		= "#ffffff" #f0f0f0
  fg[INSENSITIVE] = "#FFFEFC" #a la biel
  fg[ACTIVE]      = "#505050" #ciemno-szary

}

style "theme-tasklist" = "theme-default"
{
  xthickness = 4
  ythickness = 2
  text[NORMAL]      = "#ffffff" #ciemno-szary #505050
  bg[NORMAL]      = "#505050"  #a la biel
  text[NORMAL]      = "#505050" #ciemno-szary
  text[PRELIGHT]      = "#505050" #ciemno-szary
  text[INSENSITIVE]      = "#505050" #ciemno-szary
  text[ACTIVE]      = "#505050" #ciemno-szary


}

style "theme-menu" = "theme-default"
{
  xthickness = 3
  ythickness = 3
  text[NORMAL]      = "#505050" #ciemno-szary #505050
  text[PRELIGHT]      = "#ffffff" #505050
  text[SELECTED] = "#4DB224" #ciemno-zielony
  text[ACTIVE] = "#ffffff" #biel
	bg[NORMAL]		= "#FBF8F1" #242424 kolor t&#322;a nieaktyw menu
	fg[PRELIGHT]	= "#ffffff" #ffffff
	fg[NORMAL]		= "#ffffff" #f0f0f0
}

style "theme-menu-item" = "theme-default" # lista menu górnego
{
  ythickness = 3
  #fg[NORMAL] = "#505050" #ciemno-szary
  #fg[PRELIGHT] = "#ffffff"
  #text[NORMAL]      = "#ffffff" #ciemno-szary #505050
  #text[PRELIGHT] = "#505050" #ciemno-szary
	fg[PRELIGHT]      = "#575757"
	fg[NORMAL]        = "#575757" #8A8A8A #A0A0A0 #kolor czcionki w itemach
	fg[INSENSITIVE]      = "#505050" # cie&#324; nieaktywnego itema
	fg[ACTIVE]      = "#FBF8F1"
	bg[SELECTED]		= "#FBF8F1" #FFD799
	bg[PRELIGHT]		= "#FBF8F1" #242424
	bg[INSENSITIVE]		= "#FBF8F1" #242424
	bg[ACTIVE]		= "#FBF8F1" #242424
	text[NORMAL]      = "#575757"
	text[PRELIGHT]    = "#000000" 
	bg[NORMAL]        = "#FBF8F1" #kolor separatoru
}

style "theme-menubar" = "theme-default" # menu górne
{
  bg[NORMAL] = "#FBF8F1" #F6EFE0 #t&#322;o menubara górnego okna #F7F2E8
  fg[NORMAL] = "#505050" #ciemno-szary
  fg[ACTIVE] = "#505050" #ciemno-szary
  text[NORMAL] = "#505050"#ciemno-szary
  text[PRELIGHT] = "#505050" #ciemno-szary
  text[INSENSITIVE]      = "#505050" #ciemno-szary
  text[ACTIVE]      = "#505050" #ciemno-szary 
  base[PRELIGHT] = "#63E62E" #zielony
  base[SELECTED] = "#4DB224" #ciemno-zielony

	fg[PRELIGHT]      = "#505050"  #zmieniony
	#fg[NORMAL]        = "#575757" #8A8A8A
	#text[NORMAL]      = "#ffffff"
	#text[PRELIGHT]    = "#000000" 
	bg[PRELIGHT]        = "#FBF8F1" #color of separators in menu

}

style "theme-menubar-item"
{
	ythickness = 2
	fg[PRELIGHT]      = "#505050" #ZMIENIONY
	fg[NORMAL]        = "#575757" #8A8A8A czcionka górnego menbara
	fg[PRELIGHT] = "#575757" #jasny szary #A0A0A0
	bg[PRELIGHT] = "#FBF8F1" #ciemny szary / ciemniejszy fiolet #AF9490
	#text[NORMAL]      = "#ffffff"
	#text[PRELIGHT]    = "#000000"
	bg[NORMAL]        = "#575757" #kolor separatoru
}

style "theme-tree" = "theme-default" #pasek dolny
{
  xthickness = 2
  ythickness = 2
  bg[NORMAL]        = "#F6EFE0" #bardzo jasny pomara&#324;cz #F6EFE0
  bg[PRELIGHT]        = "#ffffff" #bardzo jasny pomara&#324;cz #F6EFE0
  bg[INSENSITIVE]        = "#ffffff" #bardzo jasny pomara&#324;cz #F6EFE0

  fg[NORMAL]        = "#ffffff" #bardzo jasny pomara&#324;cz #F6EFE0
  fg[PRELIGHT]        = "#ffffff" #bardzo jasny pomara&#324;cz #F6EFE0
  fg[INSENSITIVE]        = "#ffffff" #bardzo jasny pomara&#324;cz #F6EFE0


}

style "theme-frame-title" = "theme-default"
{
  fg[NORMAL] = "#404040" # tekst na dolnym pasku okna
}

style "theme-tooltips" = "theme-default"
{
  xthickness = 2
  ythickness = 2
  bg[NORMAL] = "#FFF1D4" #po&#347;wiata #CDB7B5
  #text[NORMAL]      = "#dfdfdf" #ciemno-szary
  #text[ACTIVE]      = "#dfdfdf" #ciemno-szary
  #text[PRELIGHT]      = "#dfdfdf" #ciemno-szary
  #fg[NORMAL]      = "#dfdfdf" #ciemno-szary
  #text[INSENSITIVE]      = "#dfdfdf" #ciemno-szary

  text[NORMAL]      = "#505050" #ciemno-szary
  text[PRELIGHT]      = "#505050" #ciemno-szary
  text[INSENSITIVE]      = "#505050" #ciemno-szary
  text[ACTIVE]      = "#505050" #ciemno-szary

}

style "theme-progressbar" = "theme-wide"
{
  xthickness = 2
  ythickness = 2

}

style "theme-combo" = "theme-button"
{
}

style "metacity-frame"
{
  # Normal base color
  #bg[NORMAL]  = "#bbbbbb"

  # Unfocused title background color
  #bg[INSENSITIVE]  = { 0.8, 0.8, 0.8 }

  # Unfocused title text color
  #fg[INSENSITIVE]  = { 1.55, 1.55, 1.55 }

  # Focused icon color
  #fg[NORMAL]  = { 0.2, 0.2, 0.2 }

  # Focused title background color
  bg[SELECTED]  = "#444444"
  base[ACTIVE]  = "#E6B68A" #E6B68A

  # Focused title text color
#  bg[NORMAL]  = "#575757"
  fg[SELECTED]  = "#444444"
  fg[INSENSITIVE]  = "#656565"
  fg[NORMAL]  = "#656565"
  text[ACTIVE]  = "#fdfdfd"
}
class "MetaFrames" 	  style "metacity-frame"
class "GtkWindow"      style "metacity-frame"

# widget styles
class "GtkWidget"      style "theme-default"
class "GtkButton"      style "theme-button"
class "GtkScale"       style "theme-button"
class "GtkCombo"       style "theme-button"
class "GtkRange"       style "theme-wide"
class "GtkFrame"       style "theme-wide"
class "GtkMenu"        style "theme-menu"
class "GtkEntry"       style "theme-entry"
class "GtkMenuItem"    style "theme-menu-item"
class "GtkNotebook"    style "theme-notebook"
class "GtkProgressBar" style "theme-progressbar"
class "*MenuBar*"      style "theme-menubar"

widget_class "*MenuItem.*" style "theme-menu-item"
widget_class "*MenuBar.*"  style "theme-menubar-item"

# combobox stuff
widget_class "*.GtkComboBox.GtkButton" style "theme-combo"
widget_class "*.GtkCombo.GtkButton"    style "theme-combo"
# tooltips stuff
widget_class "*.tooltips.*.GtkToggleButton" style "theme-tasklist"
widget "gtk-tooltips" style "theme-tooltips"

# treeview stuff
widget_class "*.GtkTreeView.GtkButton" style "theme-tree"
widget_class "*.GtkCTree.GtkButton" style "theme-tree"
widget_class "*.GtkList.GtkButton" style "theme-tree"
widget_class "*.GtkCList.GtkButton" style "theme-tree"
widget_class "*.GtkFrame.GtkLabel" style "theme-frame-title"

# notebook stuff
widget_class "*.GtkNotebook.*.GtkEventBox" style "theme-notebook"
widget_class "*.GtkNotebook.*.GtkViewport" style "theme-notebook"

# PANEL
style "panel"{
	bg[NORMAL]   = "#EFEBE7" #202020
	fg[NORMAL]   = "#EFEBE7" #fdfdfd #202020
	text[NORMAL] = "#575757" #tekst nieaktywnych w "dodaj do panelu..."
	bg_pixmap[NORMAL]	= "Panel/bg-panel-24b.png"

}

style "panelbuttons"{
    bg[NORMAL] 		= "#EFEBE7" #202020
    bg[ACTIVE]		= "#D7D1CA" #3B5155
    bg[SELECTED]	= "#A8A76F" #8B8715 #D6722D #BF4235 #A29E3F #A7A637
    bg[PRELIGHT]	= "#F1F1F1" #1F3E3B
    
    fg[NORMAL]		= "#202020" #d6d6d6
    fg[ACTIVE]		= "#202020" #DCDCDC
    fg[PRELIGHT]	= "#202020" #D6D6D6
}
class "*Panel*" style "panel"
widget_class "*Panel*GtkToggleButton" style "panelbuttons"
widget_class "*Panel*Button" style "panelbuttons"
widget_class "*Panel*b*" style "panelbuttons"

---

### Post by spg76 on 2008-04-25
Creo que no se puede cambiar por una imagen.
Si no me equivoco, como es un tema para Murrine lo único que podes hacer es cambiarlo a "flat" (plano), "glassy" (brilloso), o "con franjas" (striped).
Busca la línea que dice:
> engine "murrine"
{
menuitemstyle = [COLOR="Red"]**2**[/COLOR] # 0 = flat, 1 = glassy, 2 = striped
Y ahi podés cambiar el número [COLOR="Red"]**2**[/COLOR] por la opción que quieras.
Espero que te sirva.

---

### Post by valucha on 2008-04-26
[COLOR="DarkOrchid"]Hu...
Que lástima...

¿Y conocen algun engine que me permita cambiar eso?


MIl gracias por tu respuesta spg76 igualmente :)[/COLOR]

---

### Post by faktorqm on 2008-04-27
Observacion: La funcion duplica asignacion a una misma variable:

```

engine "murrine" 
{
[COLOR="Red"]menuitemstyle = 2[/COLOR] # 0 = flat, 1 = glassy, 2 = striped
scrollbar_color = "#505050"
scrollbarstyle = 2
contrast = 0.8
glazestyle = 0
menubarstyle = 3
menubaritemstyle = 1
[COLOR="Red"]menuitemstyle = 0[/COLOR]
listviewheaderstyle = 0
listviewstyle = 1
roundness = 2 # 0,1,2,3,4,5,6,7,8
animation = TRUE
hilight_ratio = 0.909090

```

Tendrá algo que ver? capaz no, no sé...

Esto tb puede ser otra ayuda:

bg_pixmap[NORMAL] = "Panel/bg-panel-24b.png"

eso vendria a ser algo parecido a back ground pixmap, si agarras esa foto, la backapeas, pones una que te guste a vos, y probas? para mi lo que hae eso es definir el color de todo el fondo de la calculadora. entonces si cambias eso quiza te lo cambie. si usas negro ojo con el color de la fuentes donde dice calculadora, editar, fuente, ayuda, etc.

Espero que te haya servido. Salu2!

---

### Post by valucha on 2008-04-27
> **faktorqm said:**
> Observacion: La funcion duplica asignacion a una misma variable:

```

engine "murrine" 
{
[COLOR="Red"]menuitemstyle = 2[/COLOR] # 0 = flat, 1 = glassy, 2 = striped
scrollbar_color = "#505050"
scrollbarstyle = 2
contrast = 0.8
glazestyle = 0
menubarstyle = 3
menubaritemstyle = 1
[COLOR="Red"]menuitemstyle = 0[/COLOR]
listviewheaderstyle = 0
listviewstyle = 1
roundness = 2 # 0,1,2,3,4,5,6,7,8
animation = TRUE
hilight_ratio = 0.909090

```

Tendrá algo que ver? capaz no, no sé...

Esto tb puede ser otra ayuda:

bg_pixmap[NORMAL] = "Panel/bg-panel-24b.png"

eso vendria a ser algo parecido a back ground pixmap, si agarras esa foto, la backapeas, pones una que te guste a vos, y probas? para mi lo que hae eso es definir el color de todo el fondo de la calculadora. entonces si cambias eso quiza te lo cambie. si usas negro ojo con el color de la fuentes donde dice calculadora, editar, fuente, ayuda, etc.

Espero que te haya servido. Salu2!
[COLOR="DarkOrchid"]
mmm, lo último corresponde a los paneles, donde está el menú y los tray y etc...

Me parece que con este engine no se puede, voy a probar modificando alguno de esos de Vista, a los que les ponen esas imágenes feas, tal vez poniendo la imágen que yo quiero funcione...

gracias por la observación :)

PD: Si conocés algun programa para hacer themes fácil de usar bienvenido sea.[/COLOR]

---

### Post by spg76 on 2008-04-27
Por lo que investigué se pueden agregar imágenes a los themes de Murrine pero agregando un archivo de configuración aparte con los datos de los archivos de imagen.
Si queres ver un ejemplo, chequea [http://www.debian-art.org/content/show.php/Darker+Ice+Murrina?content=72357](http://www.debian-art.org/content/show.php/Darker+Ice+Murrina?content=72357)
En ese theme en la primera línea de gtkrc pone:
```
include "menubar.rc"
```
para incluir (obvio) los opciones de ese archivo.
En una de esas te resulta útil.

---

### Post by valucha on 2008-04-28
[COLOR="DarkOrchid"]Osea, tendría que crear otro archivo configurando todo debidamente diciendo que quiero tal imágen en tal lugar... y después en el archivo prinicpal poner:
include "menubar.rc" siendo menubar.rc el archivo que yo cree?



gracias por la data :)[/COLOR]

---


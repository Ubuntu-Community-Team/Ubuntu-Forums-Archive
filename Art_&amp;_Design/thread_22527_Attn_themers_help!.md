---
title: "Attn themers: help!"
date: 2005-03-28
forum: Art &amp; Design
---

### Post by HungSquirrel on 2005-03-28
I did a Hoary dist-upgrade this morning, and ever since then the colorscheme I made for Clearlooks hasn't been working correctly.  When I am in a menu and mouse over an item, its color is the one from the Gnome Default theme, [COLOR=#49667f]**#49667f**[/COLOR].  Before the update, the menu mouseover highlights were a green gradient somewhere around [color=#87b08d]**#87b08d**[/color], as can be seen in the Applications menu of this [old screenshot](http://hungsquirrel.org/images/ubuntu-030305.jpg). Also, it now renders flat, rather than the raised gradient of Clearlooks.  This only happens in my theme.  All the other themes, including Clearlooks themes (and including the one I hacked to make mine!), work fine.

To any theme makers/hackers: what do I need to put in my gtkrc to make it work correctly?

My theme is [here](http://hungsquirrel.org/clearlooks-gondola.tar.bz2).

My gtkrc:

```
# Based on Bluecurve
# Modified by Richard Stellingwerff and Emil Jacobs

# Color scheme by Edwin Sheldon (HungSquirrel),
# hacked from Clearlooks-GONX by Billy Cantrell (bvc)


include "icons/iconrc"

style "clearlooks-default"
{
  GtkMenuItem::selected_shadow_type = out
  GtkWidget::interior_focus = 1
  GtkButton::default_border = { 0, 0, 0, 0 }
  GtkButton::default_outside_border = { 0, 0, 0, 0 }
  GtkRange::trough_border = 0

  GtkWidget::focus_padding = 1

  GtkPaned::handle_size = 6

  GtkRange::slider_width = 15
  GtkRange::stepper_size = 15
  GtkScrollbar::min_slider_length = 30
  GtkCheckButton::indicator_size = 12
  GtkMenuBar::internal-padding = 0

  #GtkOptionMenu::indicator_size = { 11, 6 }
  #GtkOptionMenu::indicator_spacing = { 4, 5, 2, 2 }

  GtkTreeView::expander_size = 14
  GtkExpander::expander_size = 16

  xthickness = 1
  ythickness = 1

  bg[NORMAL] = "#e1e3e1"		
  bg[SELECTED] = "#87b08d"
  bg[INSENSITIVE] = "#e1e3e1"	
  bg[ACTIVE] = "#acba9f"
  bg[PRELIGHT] = "#c9cdc9"
  bg[SELECTED] = "#87b08d"

  fg[NORMAL] = "#000000"
  fg[SELECTED] = "#fffdff"
  fg[ACTIVE] = "#000000"
  fg[PRELIGHT] = "#000000"

  base[NORMAL] = "#fdfdfd"
  base[ACTIVE] = "#667766"
  base[SELECTED] = "#87b08d"

  text[SELECTED] = "#000000"
  text[ACTIVE] = "#000000"
  text[SELECTED] = "#ffffff"
  text[INSENSITIVE]       = "#565248"   

  engine "clearlooks" 
  {
    contrast = 1.2 #1.0
    sunkenmenubar = 1
  }
}



style "clearlooks-wide" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 2
}

style "clearlooks-notebook" = "clearlooks-wide"
{
  bg[NORMAL] = "#dae0da" 
}

style "clearlooks-tasklist" = "clearlooks-default"
{
  xthickness = 5
  ythickness = 3
}

style "clearlooks-menu" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 1
}

style "clearlooks-menu-item" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 3
}

style "clearlooks-menu-itembar" = "clearlooks-default"
{
  xthickness = 3
  ythickness = 3
}

style "clearlooks-tree" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 2
}

style "clearlooks-frame-title" = "clearlooks-default"
{
  fg[NORMAL] = "#404040"
}

style "clearlooks-panel" = "clearlooks-default"
{
  xthickness = 3
  ythickness = 3
}

style "clearlooks-tooltips" = "clearlooks-default"
{
  xthickness = 4
  ythickness = 4
  bg[NORMAL] = { 0.90,1.0,0.90 }
}

style "clearlooks-progressbar"		= "clearlooks-default"
{
  xthickness = 0
  ythickness = 0
  fg[PRELIGHT]  = "#000000"
}

style "clearlooks-combo" = "clearlooks-default"
{
  xthickness = 1
  ythickness = 2
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
  #bg[SELECTED]  = { 0.5, 0.8, 0.5 }

  # Focused title text color
  #fg[SELECTED]  = "black"
}

class "GtkWidget" style "clearlooks-default"
class "GtkButton" style "clearlooks-wide"
class "GtkRange" style "clearlooks-wide"
class "GtkFrame" style "clearlooks-wide"
class "GtkStatusbar" style "clearlooks-wide"
class "GtkMenu" style "clearlooks-menu"
class "GtkMenuItem" style "clearlooks-menu-item"
widget_class "*.GtkMenuItem.*" style "clearlooks-menu-item"
widget_class "*.GtkAccelMenuItem.*" style "clearlooks-menu-item"
widget_class "*.GtkRadioMenuItem.*" style "clearlooks-menu-item"
widget_class "*.GtkCheckMenuItem.*" style "clearlooks-menu-item"
widget_class "*.GtkImageMenuItem.*" style "clearlooks-menu-item"
widget_class "*.GtkSeparatorMenuItem.*" style "clearlooks-menu-item"
class "GtkEntry" style "clearlooks-wide"
widget_class "*.tooltips.*.GtkToggleButton" style "clearlooks-tasklist"
widget_class "*.GtkTreeView.GtkButton" style "clearlooks-tree"
widget_class "*.GtkCTree.GtkButton" style "clearlooks-tree"
widget_class "*.GtkList.GtkButton" style "clearlooks-tree"
widget_class "*.GtkCList.GtkButton" style "clearlooks-tree"
widget_class "*.GtkFrame.GtkLabel" style "clearlooks-frame-title"
widget_class "BasePWidget.GtkEventBox.GtkTable.GtkFrame" style "clearlooks-panel"
widget "gtk-tooltips" style "clearlooks-tooltips"
class "GtkNotebook" style "clearlooks-notebook"
class "GtkProgressBar" style "clearlooks-progressbar"
widget_class "*.GtkComboBox.GtkButton" style "clearlooks-combo"
widget_class "*.GtkCombo.GtkButton" style "clearlooks-combo"
class "MetaFrames" style "metacity-frame"
```

[img]http://hungsquirrel.org/images/gondola_error.png[/img]

---

### Post by wfx on 2005-03-28
You like wappons?

---

### Post by HungSquirrel on 2005-03-28
Indeed I do.

---

### Post by HungSquirrel on 2005-03-28
Actually, it does this in GONX, too, and that's the one I hacked now that I think about it.  Any suggestions, bvc?

---

### Post by bvc on 2005-03-28
If you upgraded to hoary you now have version 0.5 of the engine and you are using a 0.4 gtkrc. By default, the 0.5 engine has a flat menuitem so what you are seeing is what they wanted you to see (for some strange reason). Take a look at a 0.5 gtkrc just below the colors. Where you have

sunkenmenubar = 1

0.5 has an option for the sunkenmenubar, menuitem, and other things as well. If you look at one of my gtkrc's from the big_pack you'll see what needs to be done. Until I get home on linux that's about as helpful as I can be.

---

### Post by HungSquirrel on 2005-03-28
Thanks a bunch!  :)

For those who care:
[http://hungsquirrel.org/clearlooks-gondola-0.5.tar.bz2](http://hungsquirrel.org/clearlooks-gondola-0.5.tar.bz2)

---

### Post by Yukonjack on 2005-03-28
[QUOTE=HungSquirrel]Thanks a bunch!  :)
For those who care:
[http://hungsquirrel.org/clearlooks-gondola-0.5.tar.bz2](http://hungsquirrel.org/clearlooks-gondola-0.5.tar.bz2)[/QUOTE]

Thanks a lot nice theme, the only thing I would suggest is changing the arrows to green instead of blue.  ;-)

---

### Post by bvc on 2005-03-28
Glad it's working for ya now!

There was a few problems with the corlor section. You had 2 bg[SELECTED] and 2 text[SELECTED] (I think). I removed them and made a few other changes. If you like them...cool...if not...cool. The important thing is that you got your menuitem back :-& 
[http://home.houston.rr.com/bvc/gtk/Clearlooks-Gondola2.tar.gz](http://home.houston.rr.com/bvc/gtk/Clearlooks-Gondola2.tar.gz)

---

### Post by HungSquirrel on 2005-03-29
[QUOTE=bvc]There was a few problems with the corlor section. You had 2 bg[SELECTED] and 2 text[SELECTED] (I think). I removed them and made a few other changes. If you like them...cool...if not...cool. The important thing is that you got your menuitem back :-& 
[http://home.houston.rr.com/bvc/gtk/Clearlooks-Gondola2.tar.gz](http://home.houston.rr.com/bvc/gtk/Clearlooks-Gondola2.tar.gz)[/QUOTE]
Looks good to me!

> Thanks a lot nice theme, the only thing I would suggest is changing the arrows to green instead of blue.
I am far too lazy to mess with icons, but thanks for the suggestion!   :mrgreen:

---

### Post by bvc on 2005-03-29
oh, I forgot to mention that the only reason the fg prelight is that light green was to show why the arrow (I assumed Yukonjack meant the arrow in the menu) can't be green and still be seen well.

---

### Post by HungSquirrel on 2005-03-29
Hmmm, I thought those were changed by editing icons.  Learn something new every day!

---

### Post by Yukonjack on 2005-03-29
[QUOTE=bvc]oh, I forgot to mention that the only reason the fg prelight is that light green was to show why the arrow (I assumed Yukonjack meant the arrow in the menu) can't be green and still be seen well.[/QUOTE]

Ok thanks for that!  ;-)

---


---
title: "How can I colourise industrial?"
date: 2006-08-20
forum: Art &amp; Design
---

### Post by shame on 2006-08-20
I want to find an industrial theme with the dapper human colour scheme or even edit the theme myself but my attempts so far, using .gtkrc-2.0 have been really crap looking, I just can't really get any of it right.
Does anyone know of a humanised industrial or know what I need to do to force industrial to use the human colours?

---

### Post by bvc on 2006-08-20
have you tried to edit the gtkrc?
/usr/share/themes/Industrial/gtk-2.0/gtkrc
```
style "industrial-default"
{
  GtkWidget::interior_focus = 1
  GtkButton::default_border = { 3, 3, 3, 3 }
  GtkButton::default_outside_border = { 3, 3, 3, 3 }
  GtkRange::trough_border = 0

  GtkWidget::focus_padding = 1

  GtkPaned::handle_size = 7
  
  GtkRange::slider_width = 15
  GtkRange::stepper_size = 15
  GtkScrollbar::min_slider_length = 30
  GtkCheckButton::indicator_size = 13
  GtkRadioButton::indicator_size = 13
  GtkMenuBar::internal-padding = 0

  GtkButton::child_displacement_x = 0
  GtkButton::child_displacement_y = 1

  PanelMenu::stripe-color = "#1E2C43"

  GtkMenuItem::selected_shadow_type = GTK_SHADOW_IN

  #GtkOptionMenu::indicator_size = { 11, 6 }
  #GtkOptionMenu::indicator_spacing = { 4, 5, 2, 2 }

	GtkTreeView::odd_row_color = "#F5F2ED"
	GtkTreeView::even_row_color = "#FAF9F7"

  xthickness = 1
  ythickness = 1
  
	fg[NORMAL]        = "#101010"
	fg[PRELIGHT]      = "#000000"
	fg[ACTIVE]        = "#000000"
	fg[SELECTED]      = "#ffffff"
	fg[INSENSITIVE]   = "#B3AFAB"

	bg[NORMAL]        = "#efebe7"
	bg[PRELIGHT]      = "#f5f3f0"
	bg[ACTIVE]        = "#E1D9D1"
	bg[SELECTED]      = "#D6722D"
	bg[INSENSITIVE]   = "#EBE7E3"

	base[NORMAL]      = "#ffffff"
	base[PRELIGHT]    = "#ffffff"
	base[ACTIVE]      = "#E1D9D1"
	base[SELECTED]    = "#FFD799"
	base[INSENSITIVE] = "#EBE7E3"

	text[NORMAL]      = "#000000"
	text[PRELIGHT]    = "#000000"
	text[ACTIVE]      = "#000000"
	text[SELECTED]    = "#000000"
	text[INSENSITIVE] = "#B3AFAB"

  engine "industrial" {}

}

style "industrial-unrounded" = "industrial-default"
{
  engine "industrial" 
    {
      rounded_buttons = FALSE
    }
}

style "industrial-wide" = "industrial-default"
{
  xthickness = 2
  ythickness = 2
}

style "industrial-tasklist" = "industrial-default"
{
  xthickness = 5
  ythickness = 3
}

style "industrial-arrows" = "industrial-default"
{
  fg[NORMAL] = { 0.2,0.2,0.2 }
}

style "industrial-menu" = "industrial-default"
{
#  engine "redmond95" { }
  xthickness = 3
  ythickness = 3

	#menu entries
	bg[PRELIGHT] = "#FFD799"
	bg[SELECTED] = "#FFD799"
	fg[PRELIGHT] = "#000000"
	text[PRELIGHT] = "#000000"
}

style "industrial-menu-separator" = "industrial-default"
{
#  engine "redmond95" { }
  xthickness = 3
  ythickness = 3

	bg[PRELIGHT] = "#FFD799"
	bg[SELECTED] = "#FFD799"
	fg[PRELIGHT] = "#000000"
	text[PRELIGHT] = "#000000"
}

style "industrial-menubar" = "industrial-default"
{
  xthickness = 3
  ythickness = 3
}

style "industrial-paned" = "industrial-default"
{
  xthickness = 10
  ythickness = 10
}

style "industrial-tree" = "industrial-default"
{
  engine "industrial" 
    {
      rounded_buttons = FALSE
    }
  xthickness = 2
  ythickness = 2
}

#style "industrial-frame-title" = "industrial-default"
#{
#  fg[NORMAL] = "#4d4466"
#}

style "industrial-panel" = "industrial-default"
{
  xthickness = 3
  ythickness = 3
}

style "industrial-tooltips" = "industrial-default"
{
  xthickness = 4
  ythickness = 4
  bg[NORMAL] = { 0.9,0.9,0.9 }
}

style "industrial-druid" = "industrial-default"
{
	bg[SELECTED] = "#FFD799"
}

style "industrial-progressbar" = "industrial-default"
{
	xthickness = 2
	ythickness = 2
	fg[PRELIGHT]  = "#ffffff"
	bg[PRELIGHT] = "#FF6D0C"
}

style "industrial-check" = "industrial-default"
{
	xthickness = 2
	ythickness = 2
	base[NORMAL] = "#FF6D0C"
	base[PRELIGHT] = "#FF8F44"
	text[PRELIGHT] = "#161616"
}

style "metacity-frame"
{
	# Focused title background color
	bg[SELECTED] = "#CC863E"
	base[SELECTED] = "#CC863E"
}

#class "Gtk*Paned" style "industrial-paned"

widget "*.tasklist-button" style "industrial-unrounded"
widget_class "*.GtkTreeView.*" style "industrial-tree"
widget_class "*.GtkList.*" style "industrial-tree"
widget_class "*.GtkCList.*" style "industrial-tree"
widget_class "*.ETree.*" style "industrial-tree"
widget_class "*.ETable.*" style "industrial-tree"

class "GtkNotebook" style "industrial-wide"
class "GtkWidget" style "industrial-default"
class "GtkButton" style "industrial-wide"
class "GtkRange" style "industrial-wide"
class "GtkMenu" style "industrial-wide"
class "GtkFrame" style "industrial-wide"
class "GtkStatusbar" style "industrial-wide"
class "*MenuItem*" style "industrial-menu"
widget_class "*MenuItem*" style "industrial-menu"
widget_class "*.GtkSeparatorMenuItem.*" style "industrial-menu-separator"
class "GtkEntry" style "industrial-wide"
widget_class "*.tooltips.*.GtkToggleButton" style "industrial-tasklist"
#widget_class "*.GtkFrame.GtkLabel" style "industrial-frame-title"
#widget_class "*.GtkFrame.GtkCheckButton.GtkLabel" style "industrial-frame-title"
widget_class "*GnomeDruidPage*" style "industrial-druid"

class "MetaFrames" style "metacity-frame"
class "GtkWindow"      style "metacity-frame"
class "GtkVScrollbar" style "industrial-arrows"
class "GtkHScrollbar" style "industrial-arrows"
widget_class "BasePWidget.GtkEventBox.GtkTable.GtkFrame" style "industrial-panel"
widget "gtk-tooltips" style "industrial-tooltips"

class "GtkProgressBar" style "industrial-progressbar"
class "GtkCheckButton" style "industrial-check"
class "GtkRadioButton" style "industrial-check"

```

I have an old Human here
[http://www.kernow-webhosting.com/~bvc/theme/ubuntu/Human/gtk/Industrial-Human.tar.gz](http://www.kernow-webhosting.com/~bvc/theme/ubuntu/Human/gtk/Industrial-Human.tar.gz)

---

### Post by shame on 2006-08-20
Yeah, I tried changing it but I had trouble working out which line was to do with which part of the theme.
Thanks for the Industrial-Human though, it's just right.  I only needed to change the brown bits to orange which was pretty simple.

---


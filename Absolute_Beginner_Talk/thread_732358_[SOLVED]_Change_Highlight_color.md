---
title: "[SOLVED] Change Highlight color?"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by amazingtaters on 2008-03-22
So, when I try to highlight a string of text, either in Firefox, OO.o, or anything else, the text gets highlighted in white. How can change this?

---

### Post by Lvcoyote on 2008-03-22
Its probably based on your theme??

---

### Post by amazingtaters on 2008-03-22
Yeah it is, but I can't seem to find where in the theme's gtkrc file the setting for it is.

here's the file

```
# Human White
#
# Author: Ben Mather <ben.mather@keble.ox.ac.uk>
#
# Based on the Ubuntu Human Colorscheme ( Richard Stellingwerff <remenic@gmail.com>
# 					  Daniel Borgmann <daniel.borgmann@gmail.com>
# 					  Billy Cantrell <bvcmdk@yahoo.com>)
# 
# Feel free to modify and share!

gtk-icon-sizes = "panel-menu=24,24"

style "clearlooks-default"
{
	GtkButton      ::default_border    = { 0, 0, 0, 0 }
	GtkRange       ::trough_border     = 0
	GtkPaned       ::handle_size       = 6
	GtkRange       ::slider_width      = 15
	GtkRange       ::stepper_size      = 15

	GtkScrollbar   ::min_slider_length = 35
	GtkCheckButton ::indicator_size    = 14
	GtkMenuBar     ::internal-padding  = 0
	GtkTreeView    ::expander_size     = 14
	GtkExpander    ::expander_size     = 16
	GtkScale       ::slider-length     = 31
	# GtkToolbar     ::button-relief     = GTK_RELIEF_NORMAL
	# GtkMenuBar     ::shadow-type       = GTK_SHADOW_OUT
	# GtkScrollbar   ::has-secondary-forward-stepper = 1
	# GtkScrollbar   ::has-secondary-backward-stepper = 1

	GtkButton      ::child-displacement-x = 0
	GtkButton      ::child-displacement-y = 0

	xthickness = 1
	ythickness = 1

	GtkTreeView::odd_row_color = "#ffffff"
	GtkTreeView::even_row_color = "#ffffff"

	fg[NORMAL]        = "#000000"
	fg[PRELIGHT]      = "#000000"
	fg[ACTIVE]        = "#000000"
	fg[SELECTED]      = "#9f9f9f"
	fg[INSENSITIVE]   = "#b4b4b4"

	bg[NORMAL]        = "#ffffff"
	bg[PRELIGHT]      = "#ffffff"
	bg[ACTIVE]        = "#e6e6e6"
	bg[SELECTED]      = "#e6e6e6"
	bg[INSENSITIVE]   = "#ffffff"

	base[NORMAL]      = "#ffffff"
	base[PRELIGHT]    = "#ffffff"
	base[ACTIVE]      = "#ffffff"
	base[SELECTED]    = "#ffffff"
	base[INSENSITIVE] = "#ffffff"

	text[NORMAL]      = "#000000"
	text[PRELIGHT]    = "#000000"
	text[ACTIVE]      = "#000000"
	text[SELECTED]    = "#000000"
	text[INSENSITIVE] = "#b4b4b4"

	engine "ubuntulooks" 
	{
		menubarstyle      = 0       # 0 = flat, 1 = sunken, 2 = flat gradient
		menuitemstyle     = 0       # 0 = flat, 1 = 3d-ish (gradient), 2 = 3d-ish (button)
		listviewitemstyle = 0       # 0 = flat, 1 = 3d-ish (gradient)
		progressbarstyle  = 2       # 0 = candy bar, 1 = fancy candy bar, 2 = flat
		animation         = FALSE
	}
}

# Evolution (and some deprecated widgets) use bg and fg for its listview instead of 
# base and text like they should, so we override it.
style "evolution-hack" = "clearlooks-default"
{	
	bg[ACTIVE]   = "#ffffff"
	bg[SELECTED] = "#ffffff"
	fg[ACTIVE]   = "#000000"
	fg[SELECTED] = "#000000"
}

# Bright orange highlights only for selected widgets
style "clearlooks-orange" = "clearlooks-default"
{
	bg[SELECTED] = "#ffffff"
}


style "clearlooks-wide" = "clearlooks-default"
{
	xthickness = 2
	ythickness = 2
}
style "clearlooks-wide-orange" = "clearlooks-wide"
{
	bg[SELECTED] = "#ffffff"
}

style "clearlooks-wider" = "clearlooks-default"
{
	xthickness = 3
	ythickness = 3
}
style "clearlooks-wider-orange" = "clearlooks-wider"
{
	bg[SELECTED] = "#ffffff"
}

style "clearlooks-button" = "clearlooks-wider-orange"
{
	bg[PRELIGHT] = "#ffffff"
	bg[ACTIVE]   = "#ffffff"
}

style "clearlooks-notebook" = "clearlooks-wide-orange"
{
	bg[NORMAL]      	= "#ffffff"
	bg[ACTIVE]      	= "#ffffff"
	bg[INSENSITIVE] 	= "#ffffff"
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
	bg[NORMAL] = "#ffffff"
}

style "clearlooks-menubar-item" = "clearlooks-button"
{
	fg[PRELIGHT] = "#000000"
}

style "clearlooks-menu-item" = "clearlooks-default"
{
	xthickness = 2
	ythickness = 3
	bg[SELECTED] = "#e6e6e6"
	fg[PRELIGHT] = "#000000"
	text[PRELIGHT] = "#000000"
}

style "clearlooks-tree" = "clearlooks-wide"
{
}

style "clearlooks-frame-title" = "clearlooks-default"
{
	fg[NORMAL] = "#000000"
}

style "clearlooks-tooltips" = "clearlooks-default"
{
	xthickness = 4
	ythickness = 4
	bg[NORMAL] = { 1.0,1.0,0.75 }
}

style "clearlooks-progressbar" = "clearlooks-wide-orange"
{
	xthickness = 2
	ythickness = 2
	fg[PRELIGHT]  = "#ffffff"
}

style "clearlooks-combo" = "clearlooks-button"
{
}

style "clearlooks-check" = "clearlooks-button"
{
}

style "clearlooks-range" = "clearlooks-wide-orange"
{
}

style "metacity-frame" = "clearlooks-default"
{
	bg[SELECTED] = "#111111"
}

style "extra-view-widgets" = "clearlooks-default"
{
	bg[NORMAL] = "#ffffff"
}


# widget styles
class "GtkWidget"      style "clearlooks-default"
class "GtkButton"      style "clearlooks-button"
class "GtkCombo"       style "clearlooks-button"
class "GtkRange"       style "clearlooks-range"
class "GtkFrame"       style "clearlooks-wide"
class "GtkMenu"        style "clearlooks-menu"
class "GtkEntry"       style "clearlooks-wider-orange"
class "GtkMenuItem"    style "clearlooks-menu-item"
class "GtkNotebook"    style "clearlooks-notebook"
class "GtkProgressBar" style "clearlooks-progressbar"
class "MetaFrames"     style "metacity-frame"
class "GtkWindow"      style "metacity-frame"

class "GtkCheckButton" style "clearlooks-check"
class "GtkRadioButton" style "clearlooks-check"

widget_class "*MenuItem.*" style "clearlooks-menu-item"
widget_class "*MenuItem.*ProgressBar*" style "clearlooks-default"

# combobox stuff
widget_class "*.GtkComboBox.GtkButton" style "clearlooks-combo"
widget_class "*.GtkCombo.GtkButton"    style "clearlooks-combo"
# tooltips stuff
widget_class "*.tooltips.*.GtkToggleButton" style "clearlooks-tasklist"
widget "gtk-tooltips" style "clearlooks-tooltips"

# treeview stuff
widget_class "*.GtkTreeView.GtkButton" style "clearlooks-tree"
widget_class "*.GtkCTree.GtkButton" style "clearlooks-tree"
widget_class "*.GtkList.GtkButton" style "clearlooks-tree"
widget_class "*.GtkCList.GtkButton" style "clearlooks-tree"
widget_class "*.GtkFrame.GtkLabel" style "clearlooks-frame-title"

# notebook stuff
widget_class "*.GtkNotebook.*.GtkEventBox" style "clearlooks-notebook"
widget_class "*.GtkNotebook.*.GtkViewport" style "clearlooks-notebook"

# these should really use base and text colors instead
widget_class "*GtkCTree*" style "evolution-hack"
widget_class "*GtkList*" style "evolution-hack"
widget_class "*GtkCList*" style "evolution-hack"
widget_class "*.ETree.*" style "evolution-hack"

widget "*.nautilus-extra-view-widget" style:highest "extra-view-widgets"
```

---

### Post by amazingtaters on 2008-03-22
Well, with gnome color chooser, I got the highlight background color to change.

---

